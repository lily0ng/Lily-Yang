
---

##  ACCESS WORKFLOW DIAGRAM

```mermaid
flowchart TD
    A[User Login] --> B{MFA Required?}
    B -->|Yes| C[Verify MFA Token]
    B -->|No| D[Validate Credentials]
    C --> D
    D --> E[Fetch User Roles & Permissions]
    E --> F{Super Admin?}
    F -->|Yes| G[Grant Full System Access]
    F -->|No| H[Fetch Region/Warehouse Access]
    H --> I[Apply Access Filters]
    I --> J[Generate Session Token]
    J --> K[Load Dashboard with<br>Filtered Locations]
    K --> L{User Action Request}
    
    L --> M[Check Permission]
    M --> N{Permission Granted?}
    N -->|Yes| O[Execute Action]
    N -->|No| P[Log Denied Attempt<br>Show Error Message]
    
    O --> Q[Update Audit Log]
    Q --> R[Trigger Notifications]
    R --> S[Return Success Response]
    
    P --> T[Session Continues<br>with Limited Access]
```

---

## REGION & WAREHOUSE STRUCTURE DIAGRAM

```mermaid
graph TB
    subgraph "Country Level"
        C1[Country: USA]
        C2[Country: Germany]
        C3[Country: Japan]
    end
    
    subgraph "Region Level"
        R1[Region: North-East]
        R2[Region: Bavaria]
        R3[Region: Kanto]
    end
    
    subgraph "Warehouse Level"
        W1[Warehouse A<br>Capacity: 10,000 units]
        W2[Warehouse B<br>Capacity: 8,000 units]
        W3[Warehouse C<br>Capacity: 15,000 units]
        W4[Warehouse D<br>Capacity: 5,000 units]
    end
    
    subgraph "Rack Level"
        RK1[Rack #001<br>Type: Pallet]
        RK2[Rack #002<br>Type: Shelf]
        RK3[Rack #003<br>Type: Cold Storage]
        RK4[Rack #004<br>Type: Hazardous]
    end
    
    subgraph "Node Level"
        N1[Node A1<br>Status: Available]
        N2[Node A2<br>Status: Occupied]
        N3[Node B1<br>Status: Reserved]
        N4[Node C1<br>Status: Maintenance]
    end
    
    subgraph "Item Level"
        I1[Item #SN-001<br>Laptop]
        I2[Item #SN-002<br>Monitor]
        I3[Item #SN-003<br>Server]
        I4[Item #SN-004<br>Router]
    end
    
    %% Connections
    C1 --> R1
    C2 --> R2
    C3 --> R3
    
    R1 --> W1
    R1 --> W2
    R2 --> W3
    R3 --> W4
    
    W1 --> RK1
    W1 --> RK2
    W2 --> RK3
    W3 --> RK4
    
    RK1 --> N1
    RK1 --> N2
    RK2 --> N3
    RK3 --> N4
    
    N1 --> I1
    N2 --> I2
    N3 --> I3
    N4 --> I4
    
    %% User Access Paths
    style R1 fill:#e1f5fe
    style W1 fill:#e1f5fe
    style RK1 fill:#e1f5fe
    style N1 fill:#e1f5fe
    style I1 fill:#e1f5fe
```

---

## ITEM RELOCATION WORKFLOW DIAGRAM

```mermaid
flowchart TD
    A[Start Relocation Request] --> B{Relocation Type?}
    
    B --> C[Same Node Move]
    B --> D[Same Rack Move]
    B --> E[Same Warehouse Move]
    B --> F[Same Region Move]
    B --> G[Cross-Region Move]
    B --> H[Entire Rack Migrate]
    B --> I[Entire Warehouse Migrate]
    B --> J[Bulk Items Move]
    
    C --> K[Validate Node Availability]
    D --> K
    E --> K
    F --> K
    G --> K
    H --> K
    I --> K
    J --> K
    
    K --> L{Node Available?}
    L -->|No| M[Suggest Alternatives]
    L -->|Yes| N[Check User Permissions]
    
    M --> O[Update Request with Alternatives]
    O --> P[Notify Requester]
    
    N --> Q{Permission Level?}
    
    Q -->|Warehouse User| R[Require L1 Approval]
    Q -->|Warehouse Manager| S[Auto-approve Same WH]
    Q -->|Regional Admin| T[Auto-approve Region Moves]
    Q -->|Super Admin| U[Auto-approve All]
    
    R --> V[Send to Warehouse Approver]
    S --> W[Create Move Ticket]
    T --> W
    U --> W
    
    V --> X{Approved?}
    X -->|Yes| W
    X -->|No| Y[Notify Requester of Denial]
    
    W --> Z[Generate Physical Move Instructions]
    Z --> AA[Assign to Move Team]
    AA --> AB[Physical Move Execution]
    AB --> AC[Scan Verification]
    
    AC --> AD{All Items Verified?}
    AD -->|No| AE[Flag Discrepancies]
    AD -->|Yes| AF[Update System Inventory]
    
    AE --> AG[Investigation Required]
    AG --> AF
    
    AF --> AH[Close Relocation Request]
    AH --> AI[Send Completion Notifications]
    AI --> AJ[Log Audit Trail]
```

---

## ITEM CREATION WORKFLOW DIAGRAM

```mermaid
flowchart TD
    A[Start Item Creation] --> B[Pre-fill Warehouse<br>Based on User Access]
    
    B --> C{Item Category?}
    C --> D[Electronics]
    C --> E[Fragile]
    C --> F[Hazardous]
    C --> G[Perishable]
    C --> H[General]
    
    D --> I[Apply Special Handling Rules]
    E --> I
    F --> J[Apply Hazardous Rules]
    G --> K[Apply Cold Chain Rules]
    H --> L[Apply Standard Rules]
    
    I --> M[Check Serial Number]
    J --> M
    K --> M
    L --> M
    
    M --> N{Duplicate Serial?}
    N -->|Yes| O[Show Warning & Details]
    N -->|No| P[Auto-generate Asset Code]
    
    O --> Q{Proceed Anyway?}
    Q -->|No| R[Cancel Creation]
    Q -->|Yes| P
    
    P --> S[Validate Node Availability]
    S --> T[Lock Selected Node]
    
    T --> U[Apply Assignment Restrictions<br>Based on User Permission]
    
    U --> V{Valid Assignment?}
    V -->|No| W[Show Permission Error]
    V -->|Yes| X[Save Item to Database]
    
    W --> Y[Suggest Authorized Locations]
    Y --> Z[Update Selection]
    Z --> X
    
    X --> AA[Generate QR/Barcode Label]
    AA --> AB[Print Documentation]
    AB --> AC[Send Creation Notifications]
    AC --> AD[Log in Audit Trail]
```

---
## FULL DATABASE ERD

```mermaid
erDiagram
    users ||--o{ user_roles : has
    users ||--o{ user_region_access : "can access"
    users ||--o{ user_warehouse_access : "can access"
    users ||--o{ user_rack_access : "can access"
    users ||--o{ login_sessions : "creates"
    users ||--o{ mfa_tokens : "uses"
    users ||--o{ audit_logs : "generates"
    
    roles ||--o{ role_permissions : "contains"
    roles ||--o{ user_roles : "assigned to"
    
    regions ||--o{ warehouses : contains
    regions ||--o{ user_region_access : "accessible by"
    
    warehouses ||--o{ racks : contains
    warehouses ||--o{ user_warehouse_access : "accessible by"
    
    racks ||--o{ nodes : contains
    racks ||--o{ user_rack_access : "accessible by"
    
    nodes ||--o{ items : stores
    nodes ||--o{ item_status_history : "tracks status"
    
    items ||--o{ item_movement_logs : "tracks movement"
    items ||--o{ item_assignment_history : "tracks assignment"
    items ||--o{ relocation_items : "included in"
    
    item_categories ||--o{ items : categorizes
    
    relocation_requests ||--o{ relocation_items : includes
    relocation_requests ||--o{ relocation_approvals : requires
    relocation_requests ||--o{ relocation_status : tracks
    
    users ||--o{ relocation_approvals : approves
    
    users {
        bigint id PK
        varchar email UK
        varchar password_hash
        varchar full_name
        boolean is_active
        boolean mfa_enabled
        timestamp last_login
        timestamp created_at
        timestamp updated_at
        timestamp deleted_at
    }
    
    roles {
        bigint id PK
        varchar name UK
        varchar description
        integer access_level
        boolean is_system_role
        timestamp created_at
    }
    
    role_permissions {
        bigint id PK
        bigint role_id FK
        varchar permission_code
        varchar resource_type
        jsonb allowed_actions
        timestamp created_at
    }
    
    user_roles {
        bigint id PK
        bigint user_id FK
        bigint role_id FK
        timestamp assigned_at
        bigint assigned_by FK
        timestamp expires_at
    }
    
    user_region_access {
        bigint id PK
        bigint user_id FK
        bigint region_id FK
        boolean can_manage
        boolean can_view
        boolean can_edit
        timestamp granted_at
        timestamp expires_at
    }
    
    user_warehouse_access {
        bigint id PK
        bigint user_id FK
        bigint warehouse_id FK
        boolean can_manage
        boolean can_view
        boolean can_edit
        timestamp granted_at
        timestamp expires_at
    }
    
    user_rack_access {
        bigint id PK
        bigint user_id FK
        bigint rack_id FK
        boolean can_manage
        boolean can_view
        boolean can_edit
        timestamp granted_at
        timestamp expires_at
    }
    
    regions {
        bigint id PK
        varchar code UK
        varchar name
        bigint country_id FK
        varchar timezone
        jsonb metadata
        boolean is_active
        timestamp created_at
        timestamp updated_at
    }
    
    warehouses {
        bigint id PK
        varchar code UK
        varchar name
        bigint region_id FK
        varchar address
        decimal latitude
        decimal longitude
        integer capacity
        integer current_occupancy
        varchar status
        jsonb operating_hours
        timestamp created_at
        timestamp updated_at
    }
    
    racks {
        bigint id PK
        varchar code UK
        bigint warehouse_id FK
        varchar type
        integer total_nodes
        integer available_nodes
        varchar status
        jsonb dimensions
        timestamp created_at
        timestamp updated_at
    }
    
    nodes {
        bigint id PK
        varchar code UK
        bigint rack_id FK
        varchar status
        varchar node_type
        jsonb properties
        timestamp last_occupied
        timestamp created_at
        timestamp updated_at
    }
    
    items {
        bigint id PK
        varchar asset_code UK
        varchar serial_number UK
        bigint category_id FK
        bigint current_node_id FK
        varchar name
        text description
        jsonb specifications
        varchar status
        decimal value
        timestamp acquisition_date
        timestamp warranty_expiry
        bigint assigned_to FK
        timestamp created_at
        timestamp updated_at
        timestamp deleted_at
    }
    
    item_categories {
        bigint id PK
        varchar name UK
        varchar code
        jsonb handling_instructions
        jsonb storage_requirements
        boolean requires_approval
        timestamp created_at
    }
    
    item_movement_logs {
        bigint id PK
        bigint item_id FK
        bigint from_node_id FK
        bigint to_node_id FK
        bigint moved_by FK
        timestamp moved_at
        varchar reason
        varchar move_type
        jsonb metadata
    }
    
    item_status_history {
        bigint id PK
        bigint item_id FK
        varchar old_status
        varchar new_status
        bigint changed_by FK
        timestamp changed_at
        varchar reason
    }
    
    item_assignment_history {
        bigint id PK
        bigint item_id FK
        bigint old_assignee FK
        bigint new_assignee FK
        bigint assigned_by FK
        timestamp assigned_at
        varchar reason
    }
    
    relocation_requests {
        bigint id PK
        uuid request_code UK
        varchar relocation_type
        bigint source_region_id FK
        bigint dest_region_id FK
        bigint source_warehouse_id FK
        bigint dest_warehouse_id FK
        bigint source_rack_id FK
        bigint dest_rack_id FK
        bigint requested_by FK
        timestamp requested_at
        varchar status
        timestamp scheduled_for
        timestamp completed_at
        text notes
        jsonb metadata
    }
    
    relocation_items {
        bigint id PK
        bigint request_id FK
        bigint item_id FK
        bigint from_node_id FK
        bigint to_node_id FK
        varchar item_status
        boolean is_verified
        timestamp verified_at
        bigint verified_by FK
    }
    
    relocation_approvals {
        bigint id PK
        bigint request_id FK
        bigint approver_id FK
        integer approval_level
        varchar decision
        timestamp decided_at
        text comments
    }
    
    relocation_status {
        bigint id PK
        bigint request_id FK
        varchar status
        timestamp changed_at
        bigint changed_by FK
        text notes
    }
    
    audit_logs {
        bigint id PK
        varchar event_type
        varchar resource_type
        bigint resource_id
        bigint user_id FK
        jsonb old_values
        jsonb new_values
        jsonb metadata
        timestamp created_at
        varchar ip_address
        varchar user_agent
    }
    
    notifications {
        bigint id PK
        varchar type
        bigint user_id FK
        varchar title
        text message
        jsonb data
        boolean is_read
        timestamp read_at
        timestamp created_at
        timestamp expires_at
    }
    
    system_settings {
        bigint id PK
        varchar key UK
        jsonb value
        varchar data_type
        varchar description
        timestamp updated_at
        bigint updated_by FK
    }
    
    mfa_tokens {
        bigint id PK
        bigint user_id FK
        varchar token_hash
        varchar method
        timestamp expires_at
        boolean is_used
        timestamp used_at
        timestamp created_at
    }
    
    login_sessions {
        bigint id PK
        bigint user_id FK
        varchar session_token
        timestamp started_at
        timestamp last_activity
        timestamp expires_at
        varchar ip_address
        varchar user_agent
        boolean is_active
    }
```

---

## CRUD OPERATIONS DIAGRAMS

### **User Management CRUD Workflow**
```mermaid
flowchart TD
    A[Create User Request] --> B[Validate Input Data]
    B --> C[Check Creator Permissions]
    C --> D{Permitted to Create User?}
    
    D -->|No| E[Return Permission Error]
    D -->|Yes| F[Generate Temporary Password]
    
    F --> G[Assign Default Role]
    G --> H{Limit Region/Warehouse Access?}
    
    H -->|Yes| I[Apply Creator's Access Limits]
    H -->|No| J[Apply System Default Limits]
    
    I --> K[Save User to Database]
    J --> K
    
    K --> L[Send Welcome Email<br>with Temp Credentials]
    L --> M[Log Creation in Audit Trail]
    M --> N[Return Success Response]
    
    E --> O[End Process]
```

### **Inventory CRUD Workflow**
```mermaid
flowchart TD
    subgraph "CREATE Item"
        A1[Receive Item Data] --> A2[Validate Required Fields]
        A2 --> A3[Check Serial Duplication]
        A3 --> A4[Assign Location<br>Based on Rules]
        A4 --> A5[Generate Asset Code]
        A5 --> A6[Save to Database]
        A6 --> A7[Create Initial Audit Log]
    end
    
    subgraph "UPDATE Item"
        B1[Receive Update Request] --> B2[Check Update Permissions]
        B2 --> B3[Validate New Values]
        B3 --> B4[Check Location Change Rules]
        B4 --> B5[Update Record]
        B5 --> B6[Log Changes in History Tables]
    end
    
    subgraph "MOVE Item"
        C1[Initiate Move] --> C2[Check Move Permissions]
        C2 --> C3[Validate Target Location]
        C3 --> C4[Lock Source & Target Nodes]
        C4 --> C5[Update Current Node]
        C5 --> C6[Log Movement]
        C6 --> C7[Update Warehouse Occupancy]
    end
    
    subgraph "DELETE Item"
        D1[Request Deletion] --> D2[Check Delete Permissions]
        D2 --> D3{Soft or Hard Delete?}
        D3 -->|Soft| D4[Set deleted_at timestamp]
        D3 -->|Hard| D5[Check Dependencies]
        D4 --> D6[Free Up Node]
        D5 --> D7[Remove All References]
        D6 --> D8[Log Deletion]
        D7 --> D8
    end
```

### **Rack & Node Management CRUD**
```mermaid
flowchart TD
    subgraph "Rack Management"
        A[Create Rack] --> B[Assign to Warehouse]
        B --> C[Define Rack Type & Properties]
        C --> D[Generate Node Slots]
        D --> E[Update Warehouse Capacity]
        
        F[Update Rack] --> G[Check Active Items]
        G --> H{Has Active Items?}
        H -->|Yes| I[Block Structural Changes]
        H -->|No| J[Allow Modifications]
        
        K[Deactivate Rack] --> L[Move All Items Out]
        L --> M[Mark as Inactive]
        M --> N[Update Availability]
    end
    
    subgraph "Node Management"
        O[Create Node] --> P[Assign to Rack]
        P --> Q[Set Node Properties]
        Q --> R[Set Initial Status]
        
        S[Update Node] --> T[Check if Occupied]
        T --> U{Occupied?}
        U -->|Yes| V[Allow Status Changes Only]
        U -->|No| W[Allow All Changes]
        
        X[Deactivate Node] --> Y[Move Item Out if Present]
        Y --> Z[Mark as Maintenance/Inactive]
    end
```

### **Warehouse Management CRUD**
```mermaid
flowchart TD
    A[Create Warehouse] --> B[Assign to Region]
    B --> C[Define Capacity & Properties]
    C --> D[Set Initial Status: Active]
    D --> E[Create Default Rack Layout]
    E --> F[Update Region Statistics]
    
    G[Update Warehouse] --> H{Status Change?}
    H -->|Yes| I[Check for Active Items]
    I --> J{Can Change Status?}
    J -->|No| K[Block Status Change]
    J -->|Yes| L[Apply Status Change]
    H -->|No| M[Apply Direct Updates]
    
    N[Lock Warehouse] --> O[Prevent New Assignments]
    O --> P[Allow Outgoing Moves Only]
    P --> Q[Notify All Users]
    
    R[Archive Warehouse] --> S[Move All Items Out]
    S --> T[Mark as Archived]
    T --> U[Remove from Active Lists]
    U --> V[Preserve History]
```

---

## APPROVAL WORKFLOW

```mermaid
flowchart TD
    A[Relocation Request Created] --> B[Auto Permission Check]
    B --> C{Requires Approval?}
    
    C -->|No| D[Auto-approve & Proceed]
    C -->|Yes| E[Route to Level 1: Warehouse Approver]
    
    D --> F[Generate Move Instructions]
    
    E --> G{Level 1 Approved?}
    G -->|No| H[Notify Requester of Denial]
    G -->|Yes| I[Check if Cross-Warehouse]
    
    I -->|No| F
    I -->|Yes| J[Route to Level 2: Regional Admin]
    
    J --> K{Level 2 Approved?}
    K -->|No| H
    K -->|Yes| L[Check if Cross-Region]
    
    L -->|No| F
    L -->|Yes| M[Route to Level 3: Super Admin]
    
    M --> N{Level 3 Approved?}
    N -->|No| H
    N -->|Yes| F
    
    F --> O[Assign to Move Team]
    O --> P[Physical Move Execution]
    P --> Q[Scan Verification]
    Q --> R{All Items Verified?}
    
    R -->|No| S[Flag Discrepancies]
    S --> T[Investigation Required]
    T --> U[Update System Partially]
    
    R -->|Yes| V[Complete System Update]
    
    U --> W[Send Partial Completion Notice]
    V --> X[Send Full Completion Notice]
    
    W --> Y[Close with Exceptions]
    X --> Z[Close Successfully]
    
    Y --> AA[Update Audit Trail]
    Z --> AA
```

---

## ADDITIONAL DIAGRAMS

### **Permission Inheritance Hierarchy**
```mermaid
graph TB
    SA[Super Admin] -->|Full Inheritance| RA[Regional Admin]
    RA -->|Region Inheritance| WM[Warehouse Manager]
    WM -->|Warehouse Inheritance| IM[Item Manager]
    WM -->|Warehouse Inheritance| MA[Move Approver]
    WM -->|Warehouse Inheritance| WU[Warehouse User]
    
    IM -->|Item Control| VU[Viewer Users]
    MA -->|Move Control| VU
    
    RA -->|Audit Access| AU[Auditor]
    
    style SA fill:#ffebee
    style RA fill:#f3e5f5
    style WM fill:#e3f2fd
    style IM fill:#e8f5e8
    style MA fill:#fff3e0
    style WU fill:#f5f5f5
    style AU fill:#fce4ec
    style VU fill:#fafafa
```

### **Notification Flow System**
```mermaid
flowchart LR
    subgraph "Event Sources"
        A[CRUD Operations]
        B[Approval Requests]
        C[System Alerts]
        D[Scheduled Tasks]
    end
    
    subgraph "Notification Engine"
        E[Event Detector]
        F[Rule Matcher]
        G[Recipient Resolver]
        H[Channel Router]
    end
    
    subgraph "Delivery Channels"
        I[Email]
        J[In-App]
        K[SMS]
        L[Webhook]
    end
    
    subgraph "User Preferences"
        M[Channel Settings]
        N[Frequency Settings]
        O[Do Not Disturb]
    end
    
    A --> E
    B --> E
    C --> E
    D --> E
    
    E --> F
    F --> G
    G --> H
    
    M --> H
    N --> H
    O --> H
    
    H --> I
    H --> J
    H --> K
    H --> L
```

### **Audit Trail Data Flow**
```mermaid
flowchart TD
    A[User Action] --> B[Interceptor Captures Event]
    B --> C[Extract Before State]
    C --> D[Execute Action]
    D --> E[Extract After State]
    E --> F[Compare Changes]
    F --> G[Generate Audit Record]
    G --> H[Store in Audit Table]
    H --> I[Trigger Notifications if Critical]
    I --> J[Update Real-time Dashboard]
    
    K[Audit Query] --> L[Search Engine]
    L --> M[Apply Filters & Permissions]
    M --> N[Retrieve Audit Records]
    N --> O[Generate Report]
    O --> P[Export/Display]
```

---

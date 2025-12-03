

## **User & Access Management Workflow**

```mermaid
flowchart TD
    A[User Login] --> B{Check User Role & Permissions}
    
    B --> C[Super Admin]
    B --> D[Regional Admin]
    B --> E[Warehouse User]
    B --> F[Viewer]
    
    C --> C1[Access All Regions<br>All Warehouses]
    D --> D1[Access Assigned Regions<br>All Warehouses in Region]
    E --> E1[Access Specific Warehouses<br>in Assigned Region]
    F --> F1[Read Only Access<br>Based on Assignment]
    
    C1 --> G[Load Accessible Locations]
    D1 --> G
    E1 --> G
    F1 --> G
    
    G --> H[Show Only Assigned<br>Regions/Warehouses]
    H --> I[User Can Perform Actions<br>Based on Permissions]
```

## **Region & Warehouse Access Structure**

```mermaid
flowchart LR
    subgraph R1 [Region - Yangon]
        subgraph W1 [Warehouse - TDC]
            W1A[Rack A]
            W1B[Rack B]
        end
        subgraph W2 [Warehouse - TGG]
            W2A[Rack A]
            W2B[Rack B]
        end
        subgraph W3 [Warehouse - TWC]
            W3A[Rack A]
        end
    end
    
    subgraph R2 [Region - Mandalay]
        subgraph W4 [Warehouse - MDY1]
            W4A[Rack A]
        end
    end
    
    subgraph R3 [Region - Naypyidaw]
        subgraph W5 [Warehouse - NPT1]
            W5A[Rack A]
        end
    end
    
    %% User Access Examples
    U1[User A: YGN Region Only] --> R1
    U2[User B: TDC Warehouse Only] --> W1
    U3[User C: TGG & TWC Only] --> W2
    U3 --> W3
```

## **Item Relocation Workflow**

```mermaid
flowchart TD
    Start[Start Item Relocation] --> A{Select Relocation Type}
    
    A --> B[Move Item to Different Node<br>Same Rack]
    A --> C[Move Item to Different Rack<br>Same Warehouse]
    A --> D[Move Item to Different Warehouse<br>Same Region]
    A --> E[Move Item to Different Region]
    A --> F[Move Entire Node<br>All Items]
    
    B --> G[Select Destination Node]
    C --> H[Select Destination Rack & Node]
    D --> I[Select Destination Warehouse, Rack & Node]
    E --> J[Select Destination Region, Warehouse, Rack & Node]
    F --> K[Select Destination Location<br>for Entire Node]
    
    G --> L[Check User Permissions<br>for Source & Destination]
    H --> L
    I --> L
    J --> L
    K --> L
    
    L --> M{Permission Granted?}
    M -->|Yes| N[Create Relocation Request]
    M -->|No| O[Show Access Denied Error]
    
    N --> P[Submit for Approval]
    P --> Q[Approval Workflow]
    Q --> R[Physical Move Completed]
    R --> S[Update Item Location<br>in System]
    S --> T[Audit Log Updated]
```

## **Item Creation & Location Assignment**

```mermaid
flowchart TD
    Start[Add New Item] --> A[User Logs In]
    A --> B[Load User's Accessible Locations]
    
    B --> C{User's Access Level}
    
    C --> D[Super Admin]
    C --> E[Regional Admin]
    C --> F[Warehouse User]
    
    D --> D1[Show All Regions<br>All Warehouses]
    E --> E1[Show Assigned Regions<br>All Warehouses in Regions]
    F --> F1[Show Only Assigned<br>Warehouses]
    
    D1 --> G[Select Region]
    E1 --> G
    F1 --> H[Select Warehouse<br>Auto-selected if only one]
    
    G --> I[Select Warehouse]
    I --> J[Select Rack]
    J --> K[Select Node]
    
    H --> J
    
    K --> L[Fill Item Attributes]
    L --> M[Save Item with<br>Location Assignment]
    M --> N[Item Accessible Only to Users<br>with Location Permissions]
```

## **User Permission Matrix**

```mermaid
flowchart LR
    subgraph U [User Types & Permissions]
        U1[Super Admin]
        U2[Regional Admin]
        U3[Warehouse User]
        U4[Viewer]
    end
    
    subgraph P [Permissions]
        P1[Create Users]
        P2[Assign Regions/Warehouses]
        P3[Manage All Items]
        P4[Manage Regional Items]
        P5[Manage Warehouse Items]
        P6[View Only]
        P7[Approve Requests]
    end
    
    U1 --> P1
    U1 --> P2
    U1 --> P3
    U1 --> P7
    
    U2 --> P4
    U2 --> P7
    
    U3 --> P5
    
    U4 --> P6
```

## **Database Structure for Access Control**

```mermaid
erDiagram
    users ||--o{ user_region_access : has_access_to
    users ||--o{ user_warehouse_access : has_access_to
    users ||--o{ user_roles : has
    
    user_roles {
        int id PK
        string role_name
        string permissions
    }
    
    user_region_access {
        int id PK
        int user_id FK
        int region_id FK
    }
    
    user_warehouse_access {
        int id PK
        int user_id FK
        int warehouse_id FK
    }
    
    regions ||--o{ warehouses : contains
    regions {
        int id PK
        string region_code
        string region_name
    }
    
    warehouses ||--o{ racks : contains
    warehouses {
        int id PK
        string warehouse_code
        string warehouse_name
        int region_id FK
    }
    
    racks ||--o{ nodes : contains
    racks {
        int id PK
        string rack_code
        int warehouse_id FK
    }
    
    nodes ||--o{ items : contains
    nodes {
        int id PK
        string node_name
        int rack_id FK
    }
    
    items {
        int id PK
        string serial_number
        string asset_tag
        int current_node_id FK
        string item_category
        string status
    }
```



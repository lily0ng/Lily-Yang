
##  Group setup 

```javascript
const sidebarcustomTheme = {
    root: {
        inner: "bg-white",
    },
    item: {
        base: "group flex items-center rounded-lg p-2 hover:bg-[#F9F5FF] hover:text-red-500",
        icon: {
            base: "text-red-700 group-hover:text-green-500",
        }
    }
}
```

## Group Setup 

```javascript
const sidebarcustomTheme = {
    root: {
        inner: "bg-white",
    },
    item: {
        base: "group flex items-center rounded-lg p-2 text-gray-900 hover:bg-[#F9F5FF]",
        content: {
            base: "text-gray-900 group-hover:text-red-500 transition-colors duration-200"
        },
        icon: {
            base: "text-gray-700 group-hover:text-red-500 transition-colors duration-200",
        }
    }
}
```

## Floating Label

```jsx
<div>
    <FloatingLabel 
        variant="outlined" 
        label="Label" 
        className="text-red-500 focus-within:text-red-700 border-red-300 focus-within:border-red-500"
    />
</div>
```
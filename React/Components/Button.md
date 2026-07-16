---
aliases: [react-button, btn-component, action-button]
tags: [react, button, components, ui]
cssclass: reference
---
# React Button Component

## Button Variants

```jsx
function Button({ children, variant = 'primary', onClick, disabled }) {
    return (
        <button 
            className={`btn btn-${variant}`}
            onClick={onClick}
            disabled={disabled}
        >
            {children}
        </button>
    );
}

// Usage
<Button variant="primary">Save</Button>
<Button variant="danger">Delete</Button>
<Button variant="outline">Cancel</Button>
```

## Related

- [[React\Components\Badge|Badge]]

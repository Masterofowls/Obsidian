---
aliases: [react-list, list-component, data-list]
tags: [react, list, components, data]
cssclass: reference
---
# React List Component

## Basic List

```jsx
function List({ items }) {
    return (
        <ul className="list">
            {items.map(item => (
                <li key={item.id}>{item.name}</li>
            ))}
        </ul>
    );
}
```

## Related

- [[React\Components\Table|Table]]

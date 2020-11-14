## The New Way
You can create a binding to an attribute as follows:

```html
<input bind-attr(value)="view.content"></div>
```

If you'd like attribute changes to be applied to your view, i.e. two-way binding, you have to specify the name of an event:

```html
<input bind-attr(value)="view.content=input"></div>
```
Your view will then be updated on each `input` event.


## The Old Way (deprecated)

| Binding Name 	| Expression Type   | Value Type                   |
|---------------|-------------------|------------------------------|
| bind-attr 	| object expression | { name: string, value: any } |

## Usage
```HTML
<div bind-attr="{ name: disabled, value: view.isDisabled }"></div>
```


```html
<button bind-event(click)="view.onCreateItem"></button>
```

The `event` binding allows you to bind a function on your view to be called when ever the specified event is dispatched.
Event handlers are always called with two arguments, the native `Event` object and the current `Scope` of the binding. The scope is particularly useful inside a `Repeat` binding as it will always point to the current instance of the template.

```js
function eventHandler(event, scope) {
    ...
} 
```
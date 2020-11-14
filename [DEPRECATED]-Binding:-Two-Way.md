| Binding Name     | Expression Type                | Value Type                   |
|------------------|--------------------------------|------------------------------|
| bind-model       |single expression               | any value                    |
| bind-model-event |colon separated expression list | string, any value, any value |

## Usage 
```HTML
<div bind-model="view.text" 
     bind-model-event="changeEvent:elementProperty:eventProperty">
</div>
```

The primary attribute of the binding is `bind-model`. If the property is present, a binding will be created. 
However, the helper attribute `bind-model-event` is also required. It specifies to which DOM event the binding will listen, into which DOM element property to put the bound value and from which event property to read user input.
This makes the two-way binding the currently most complex binding in this framework.

```HTML
<div bind-model="view.text" 
     bind-model-event="change:textContent:target.textContent">
</div>
```

## Quirks
Due to the initial openness and dynamic of the binding, an inconvenient quick has sneaked into this binding. 
If a child element, of the element which is equipped with this binding, emits the same event, 
the binding will also receive that update. This means that the binding at some point could receive a wrong value.
To avoid this issue it is recommended to bind against the `currentTarget` instead of `target`. The event still will be received, but always the intended value will be assigned. 

**Note:** Polymer paper elements do not provide the `currentTarget` property on their events. 
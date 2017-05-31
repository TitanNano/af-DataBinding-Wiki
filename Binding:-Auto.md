| Binding Name | Expression Type | Value Type   |
|--------------|-----------------|--------------|
| bind-auto    | expression      | scope object |

The value of the provided expression is used to create a new scope. This scope then gets used instantiate the template content. 
Finally the new scope will be written back into the expression.

## Usage
```HTML
<template bind-auto="view.createComponentView"></template>
```
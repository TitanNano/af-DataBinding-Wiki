This Trait is intended to simplify the connection between templates and their controlling code. It defines a clear structure which a view controller should follow.

## Properties

|Name    |Trait                       |Description                                     |
|--------|----------------------------|------------------------------------------------|
|template|string / HTMLTemplateElement|the template this controller is responsible for.|
|scope   |Scope                       |the current template scope                      |

## Methods
### useInAutoBinding() => `{ view: ViewController }`

this method creates a new object which then can be used with an auto binding.
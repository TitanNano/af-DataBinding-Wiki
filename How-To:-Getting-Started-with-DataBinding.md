The most simplest way to use the Data Binding framework is via a `ViewController`.

```JavaScript
// App Header 

import ViewController from '@af-modules/databinding/prototypes/ViewController';

const AppHeader = {
    template: 'app-header',

    __proto__: ViewController,
};

export default AppHeader;
```
This will setup a basic view. Every property of the controller will be available in the template.

Now we need a corresponding template.

```HTML
<!-- app-header.html -->
<template>
    <header>
        <div>{{view.title}}</div>
        <div>{{view.status}}</div>
    </header>
</template>
```
This simple template renders two properties into a header. In order to render something we need actual data, so we need to fill the properties in the controller.

```JavaScript
// App Header 

import ViewController from '@af-modules/databinding/prototypes/ViewController';

const AppHeader = {
    template: 'app-header',

    title: 'App Title',
    status: 'online',

    __proto__: ViewController,
};

export default AppHeader;
```

Now the view has to be created before we can see anything on our page.

First we need to include the template:
```HTML
<html>
    <head></head>
    <body>
        <template id="app-header" src="./AppHeader.html" replace>
    </body>
</html>
```

Then the view has to be initialized:
```JavaScript
import Application from 'application-frame/core/Application';
import AppHeader from './AppHeader';

const App = {
    name: 'My Test App',
    version: '1.0.0',

    init() {
        this.constructor();

        AppHeader.constructor();
    },

    __proto__: AppHeader,
};

export default App;
```

This integrates the view into our Application Frame app and will render the template into our DOM.

**Continue with [How To: Update your view](https://github.com/TitanNanoDE/af-DataBinding/wiki/How-To:-Update-your-view)**
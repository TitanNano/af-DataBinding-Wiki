Until now our view is static. 
Once it is rendered, nothing changes and there is no way of interaction.

How can we update our view?
On every `ViewController`, there is a property called `scope`. The scope object contains everything that is available to the view. In short, the scope is the representation of our view. 
Your scope should look something like this:

```JavaScript

const myView = {
//....

    scope: {
        update(),
        __destroy__(),
        __watch__(),
        view: view, // this is our view controller myView. JavaScript calls this a circular reference.
    },
    __proto__: ViewController, 
};
```

Everything inside scope we can call in our template. That's why we are able to access `view.title`.

But now back to updating the view. With calling `myView.scope.update()` we will tell the data binding engine that something on our scope has changed and we request a re-render.

doing something like this, demonstrates the functionality:

```JavaScript

const myView = {
//....

    title: 'demo app',

    constructor() {
        super.constructor();

        setTimeout(() => {
            myView.title = 'test';
            myView.scope.update();
        }, 3000);
    },

//....
};
```

## Automatic Updates
Until now this seems a bit of a hassle. Call the update function every time we change something? while it is quite Possible to do so, you might want the framework to automatically update. Event handlers automatically update the view once they are done, but more on that later.

To track changes on your data, it is useful to use `Application Frame`s `DataStorage`.

```JavaScript
import DataStorage from 'application-frame/core/DataStorage';

const view = {

    data: Object.create(DataStorage).constructor();

    constructor() {
        super.constructor();
        this.data.when(this.scope.update);
    },

    updateOurStuff() {
        this.data.fill({ stuff: 13 });
    },

    __proto__: ViewController,
};
```

How does this work? `DataStorage.when()` accepts a callback function which is called every time we put data into the storage. Here we simply pluck our update function in there. When we now call the `updateOurStuff()` function, we fill new data into the storage and this will trigger our view to update. 

As long as we register with all data storages our view requires, it will be updated whenever some data changes.
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
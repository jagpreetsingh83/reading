## Basics

*   A key powerful feature of LoopBack is that when you define a model it automatically comes with a predefined REST API with a full set of create, read, update, and delete operations.
*   The Model definition JSON file includes an idInjection property that indicates whether LoopBack automatically adds a unique id property to a model. For a model connected to a database, the id property corresponds to the primary key.
*   Base Models > Connected Models > Built-in models
*   To specify a project-relative path (for example, to a directory containing static assets), start the string with the prefix $!
*   You can create loopback models directly from the relational database using the Model discovery.
*   Application logic..
    1.  Remote Methods (Custom REST endpoints), Remote Hooks (triggered by remote methods) and Operation Hooks (triggered by create, read, update, delete etc.)
    2.  Boot scripts that runs when the application starts
    3.  Custom middleware

## Components

*   LoopBack components are predefined packages that extend a basic LoopBack application. Fundamentally, a component is related code bundled together as a unit to enable LoopBack applications for easy reuse. 
*   The bare minimum to meet the LoopBack component “contract” is to export a `function(app, options)` as the main module export.
    1.  API Explorer (Swagger UI)
    2.  OAuth 2.0
    3.  Push Notifications 
    4.  Storage component
    5.  Synchronization
    6.  Third-party login using Passport


## Middleware

*   Middleware registered via the Express API app.use, app.route, app.get (and other HTTP verbs) runs at the beginning of "route" phase.
*   By convention, place middleware functions in the server/middleware directory.
*   `#` in the middleware ID is just an easy way to determine the method name e.g. **loopback#static = loopback.static()**
*   Middlewares can have name, method they are applied to e.g. get/post etc. Paths these should get trigger. For more info read [configuration.](http://loopback.io/doc/en/lb3/Defining-middleware.html#middleware-configuration-properties "Middleware Configuration Properties")
*   If you don’t provide the route, then the middleware will trigger on all routes
*   **Using phases helps to avoid ordering issues that can occur with standard Express middleware.**
*   If you add middleware on the `route` or `route:after` phase, it will not execute after the route is matched. Instead, it will be ignored because the route was already matched.
*   You can put listeners on response in the middleware:
    ```javascript
    module.exports = function() {
        return function tracker(req, res, next) {
            console.log('Request tracking middleware triggered on %s', req.url);
            var start = process.hrtime();
            res.once('finish', function() {
            var diff = process.hrtime(start);
            var ms = diff[0] * 1e3 + diff[1] * 1e-6;
            console.log('The request processing time is %d ms.', ms);
            });
            next();
        };
    };
    ```
    1.  Add the code above to server/middleware/tracker.js.
    2.  Edit (or create) the file server/middleware.json and register the new middleware in the “initial” phase:
    ```
    {
        "initial": {
            "./middleware/tracker": {}
        }
    }
    ```
>   For routes serving JSON, best practice is to create a new model and implement the routes as remote methods. For routes serving non-JSON responses, best practice is to define them the standard “Express way” in server.js or a boot script.


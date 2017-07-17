# Goal Based Investing

### Learning

*   Used `loopback-component-jsonapi` to standardize the API response structure.

### Improvements

*   config.json file can be read using `app.get('setting-name')`
*   Disable /explorer for production (security reasons)
    ```javascript
    {
        "loopback-component-explorer": null
    }
    ```
*   Enable stack traces in development
    http://loopback.io/doc/en/lb3/Environment-specific-configuration.html#include-stack-traces-in-http-responses
*   ${MONGO_USER} to use config/environment variables even in the JSON files.




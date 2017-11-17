Zip is a simple yet powerful PHP Micro Framework.

```
Legend:
    - folder
    * file
    > syntax/code

zip (Convention)
    - config
        * app.php
            > return [];
            > version = ''
            > default_landing_route = ''
            > default_404_route = ''
        * routes.php
            > Route::get('users-management', 'User_Management\UserController@method')->middleware([User_Management\Middleware\RedirectIf::class, ]);
            > Route::post('add-users-management', 'User_Management\UserController@method')->middleware([User_Management\Middleware\RedirectIf::class, ]);
            > Route::group(['prefix' => '', 'middleware' => [], 'namespace' => 'User_Management'], function() {});
    - modules
        - users-management
            - middleware
                > RedirectIf.php
                    > class RedirectIf extends Middleware {}
                    > public function catch($request, Loader $loader) { return $loader->next($request); }
            - controller
                * UserController.php
                    > use Module/User_Management/Services/UserService;
            - services
                * UserService.php
                    > namespace Module/User_Management/Services;
        - accounts
            - middleware
            - controller
        - event-registration
    - www
        - assets
            - js
            - css
            - img
        * index.php
        * .htaccess
    - storage
        - framework
            - views
    - vendor
        - zip
            - framework
                - flare
                    - Container
                    - Foundation
                        * Loader.php
                    - Session
                        * Session.php
                        * SessionManager.php
```

TO DO:
1. Routes
2. Views
3. Request and Response
4. Life Cycle
5. Validation
6. Session
7. Assets Loading (Private and Public)
8. Middlware
9. Controller
# PHP Code Comment Documentation

### Goal: "To write effective and comprehensive documentation."

### Sample of Comment Structure Block:

### For Class:
```php
    /**
     * Short Description...
     *
     * Long Description...
     *
     * @package     Nucleus
     * @subpackage  Session
     * @copyright   Nuworks Interactive Inc.
     * @license     MIT License
     * @version     x.x.x
     * @link        https://nuworks.ph
     * @author      Sample Author<author@email.com>
     * @author      Sample Author 2<author2@email.com>
     */
    class Sample 
    {   
        /**
         * Short Description...
         *
         * Long Description...
         *
         * @deprecated x.x.x | n/a
         * @see ... | n/a
         *
         * @param  {[type]}  {[argument]}  [description]
         * ...
         *
         * @return {[type]}
         * @throws ... n/a
         */
        public function __construct()
        {

        }

        /**
         * Short Description...
         *
         * Long Description...
         *
         * @deprecated x.x.x | n/a
         * @see ... | n/a
         *
         * @param  {[type]}  {[argument]}  [description]
         * ...
         *
         * @return {[type]}
         * @throws ...
         */
        public function sampleFunction($argument, ...)
        {
            /**
             * Short In-line Description...
             *
             * Long In-line Description...
             *
             * @deprecated x.x.x | n/a
             *
             * @see ... | n/a
             */
            if ($argument == true) {
                return [...];
            }
        }

        ...
    }
```

### For Function:
```php
/**
 * Short Description...
 *
 * Long Description...
 *
 * @package     Nucleus
 * @subpackage  Session
 * @copyright   Nuworks Interactive Inc.
 * @license     MIT License
 * @version     x.x.x
 * @link        https://nuworks.ph
 * @author      Sample Author<author@email.com>
 * @author      Sample Author 2<author2@email.com>
 *
 * @access public
 * @deprecated x.x.x | n/a
 * @see ... | n/a
 *
 * @param  {[type]}  {[argument]}  [description]
 * ...
 *
 * @return {[type]}
 * @throws ...
 */
function sample_helper($argument, ...) 
{
    
}
```

------

```

Common Used Tags:

@package
    - Specify the main group of all the modules, classes or functions.
    Ex. @package  Nucleus

@subpackage
    - Specify the module where the classes or functions belongs to.
    Ex. @subpackage  Session

@copyright
    - Specify the copyright information.
    Ex. @copyright  Nuworks Interactive Inc.

@license
    - Specify the license used.
    Ex. @license  MIT License

@version
    - Show the current version of the classes or functions with the format of (major.minor.patches).
    Ex. @version  x.x.x

@link
    - Specify the link of the provided documentation for the classes or functions.
    Ex. @link  https://nucleus.nuworks.ph/docs/v1/...

@author
    - The creator name of the classes and functions.
    Ex. @author  Sample Author <email@emailsample.com>

@access
    - Define the access type of the functions
    Ex. @access public | private | protected

@deprecated
    - Specify the version when the classes or functions deprecated.
    Ex. @deprecated  x.x.x

@see
    - Specify the example how to use or purpose of the classes or functions.
    Ex. @link  https://nucleus.nuworks.ph/docs/v1/example/...

@param
    - The arguments define in the method.
    Ex. @param  {[type]}  $argument  Description...

@return
    - Specify the return type of the function.
    Ex. @return {[type]}
        - array
        - boolean
        - int
        - mixed
        - string
        - void
        - etc...

@throws
    - If the method or function provide a throwable exception return then specify the path of the exception class here.
    Ex. @throws Exception\SampleSubException
```

### References:
* https://en.wikibooks.org/wiki/PHP_Programming/Coding_Standards
* https://make.wordpress.org/core/handbook/best-practices/inline-documentation-standards/php/
* https://en.wikipedia.org/wiki/PHPDoc
* http://manual.phpdoc.org/HTMLSmartyConverter/PHP/phpDocumentor/tutorial_tags.pkg.html
* http://docs.phpdoc.org/guides/docblocks.html
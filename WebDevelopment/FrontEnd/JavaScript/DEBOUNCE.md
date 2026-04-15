# Debounce

```js
/**
 * The code snippet for Debounce Strategy.
 *
 * @param {Function} callback     The callback function that will be debouce.
 * @param {Number}   waitingTime  The (N) milliseconds that the callback function  
 *                                will be call after no call action made.
 *
 * @return {Function}
 */
function debounce(callback, waitingTime = 0) {

    if (typeof callback !== 'function') {
        throw Error('The first argument is not a type function.');
    }

    if (typeof waitingTime !== 'number') {
        throw Error('The second argument is not a type number');
    }

    var timeout = null;

    return function() {

        var context = this;
        var args = arguments;

        clearTimeout(timeout);

        timeout = setTimeout(function() {
            timeout = null;
            callback.apply(context, args);
        }, waitingTime);
    };
};
```

### 浅拷贝
> Object.assign()
在MDN上介绍Object.assign()：”Object.assign() 方法用于将所有可枚举的属性的值从一个或多个源对象复制到目标对象。它将返回目标对象

```
    var a = {
        myname: 'yana'
    };
var b = a;
b.myname = '小雅';
console.log(b.myname);    // 小雅
console.log(a.myname);    // 小雅
```


```
    var target = {a: 1, b: 1};
var copy1 = {a: 2, b: 2, c: {ca: 21, cb: 22, cc: 23}};
var copy2 = {c: {ca: 31, cb: 32, cd: 34}};
var result = Object.assign(target, copy1, copy2);
console.log(target);    // {a: 2, b: 2, c: {ca: 31, cb: 32, cc: 33}}
console.log(target === result);    // true

```


> jquery extend

```
jQuery.extend = jQuery.fn.extend = function() {
    var options, name, src, copy, copyIsArray, clone,
        target = arguments[ 0 ] || {},
        i = 1,
        length = arguments.length,
        deep = false;
 
    // Handle a deep copy situation
    if ( typeof target === "boolean" ) {
        deep = target;
 
        // Skip the boolean and the target
        target = arguments[ i ] || {};
        i++;
    }
 
    // Handle case when target is a string or something (possible in deep copy)
    if ( typeof target !== "object" && !jQuery.isFunction( target ) ) {
        target = {};
    }
 
    // Extend jQuery itself if only one argument is passed
    if ( i === length ) {
        target = this;
        i--;
    }
 
    for ( ; i < length; i++ ) {
 
        // Only deal with non-null/undefined values
        if ( ( options = arguments[ i ] ) != null ) {
 
            // Extend the base object
            for ( name in options ) {
                src = target[ name ];
                copy = options[ name ];
 
                // Prevent never-ending loop
                if ( target === copy ) {
                    continue;
                }
 
                // Recurse if we're merging plain objects or arrays
                if ( deep && copy && ( jQuery.isPlainObject( copy ) || ( copyIsArray = Array.isArray( copy ) ) ) ) {
 
                    if ( copyIsArray ) {
                        copyIsArray = false;
                        clone = src && Array.isArray( src ) ? src : [];
 
                    } else {
                        clone = src && jQuery.isPlainObject( src ) ? src : {};
                    }
 
                    // Never move original objects, clone them
                    target[ name ] = jQuery.extend( deep, clone, copy );
 
                // Don't bring in undefined values
                } else if ( copy !== undefined ) {
                    target[ name ] = copy;
                }
            }
        }
    }
    // Return the modified object
    return target;
};
```


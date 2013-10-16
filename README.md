# PhpDocReader

[![Build Status](https://travis-ci.org/mnapoli/PhpDocReader.png?branch=master)](https://travis-ci.org/mnapoli/PhpDocReader) [![Coverage Status](https://coveralls.io/repos/mnapoli/PhpDocReader/badge.png)](https://coveralls.io/r/mnapoli/PhpDocReader)

This project is used by:

- [PHP-DI](http://php-di.org/)
- [phockito-unit-php-di](https://github.com/balihoo/phockito-unit-php-di)

Fork the README to add your project here.

## Features

PhpDocReader parses `@var` and `@param` values in PHP docblocks:

```php

use My\Cache\Backend;

class Cache
{
    /**
     * @var Backend
     */
    protected $backend;

    /**
     * @param Backend $backend
     */
    public function __construct($backend)
    {
    }
}
```

It supports namespaced class names with the same resolution rules as PHP:

- fully qualified name (starting with `\`)
- imported class name (eg. `use My\Cache\Backend;`)
- relative class name (from the current namespace, like `SubNamespace\MyClass`)
- aliased class name  (eg. `use My\Cache\Backend as FooBar;`)

## Usage

```php
$reader = new PhpDocReader();

// Read a property type (@var phpdoc)
$property = new ReflectionProperty($className, $propertyName);
$propertyType = $reader->getPropertyType($property);

// Read a parameter type (@param phpdoc)
$parameter = new ReflectionParameter(array($className, $methodName), $parameterName);
$parameterType = $reader->getParameterType($parameter);
```

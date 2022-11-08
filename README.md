# design patterns used in laravel:
- The Builder (Manager) pattern
- The Factory pattern
- The Repository pattern
- The Strategy pattern 
- The Provider pattern
- The Facade pattern
  
## The builder pattern :
the builder design patter is a well known pattern used when we want to create an object with defferent configurations depending on our need, the class provide us with methods so we can configure our object.

### Example:
```php
    class CarBuilder {

        private $car;

        public function __construct() 
        {
            $this->car = new Car();
        }

        public function engin($engin) 
        {
            $this->car->engin = $engin;
            return $this;
        }
        public function speed($speed)
        {
            $this->car->speed = $speed;
            return $this;
        }
    }
```

in the car builder class we created an object of car in the constructor, and we can configure our car using the methods on builder class. and we are returning the `$this` so we can chain methods, as the example bellow.

```php
    $myCar = (new CarBuilder())->engin("EcoBoost I4 3.7 L")->speed(240);
```

the same thing is used in in query builder in laravel 
```php 
    $products = DB::table('product')->where('name', 'car')->get();
```

## The Factory pattern :

the factory design pattern is used to isolate the creation of the object and return a refirance to the newly created object.

### Example :

```php

    class CarFactory {
        public function create()
        {
            return new Car([
                "model" => " SS 454",
                "brand" => "chevrolet"
            ]);
        }
    }
```

## The Repository pattern
# Simple rules to make Mutuo developers happy

Goals
* Make it easier and faster for application developers to be productive.
* Write code that is simple to read and which will always be understandable.

Avoid
* Conflicting design and documentation
* Function duplication

# Curly braces

* Same line (cuddled)
``` php
function foo() {
    //do something
}
```
``` php
if (true) {
    //do something
}
else {
    //do something else
}
```
``` php
while (a > b) {
    //do something
}
```
``` php
Route::get('/', function() {
    //do something
});
```
``` php
return [
    'value' => 1
];
```

## Naming convention

* Declare variable and function names in **lowerCamelCase**
* Declare class names in **UpperCamelCase**

``` php
class FooClass {
    private $usersService;

    public function __construct() {

    }
    public function foo() {

    }
}
```

## Scope prefixes

* Use prefixes to describe scope:
    * formal parameters: **p** (short for *parameter*)
    * local scope variables: **l** (short for *local*)

``` php
function sumUpTo($pValue) {
    $lSum = ($pValue) * ($pValue + 1) * 0.5;
    return $lSum;
}
```

# Avoid nested code
``` php
function getPayAmount() {
    $lResult;
    if ($isDead) {
        $lResult = $this->deadAmount();
    } 
    else {
        if ($isSeparated) {
            $lResult = $this->separatedAmount();
        }
        else {
            if ($isRetired) {
                $lResult = $this->retiredAmount();
            }
            else {
                $lResult = $this->normalPayAmount();
            }
        };
    }
    return $lResult;
};  
```

* Adding guard clauses can remove the need to nest code.

``` php
function getPayAmount() {
    if ($isDead) { 
        return $this->deadAmount();
    }
    if ($isSeparated) { 
        return $this->separatedAmount();
    }
    if ($isRetired) {
        return $this->retiredAmount();
    }
    return $this->normalPayAmount();
};  
```

# Naming
* Avoid confusing and misleading names
``` php
$userId = [1, 2, 3, 4, 5];
```
``` php
$x = $a + $usrRl;
```
* Use intention revealing names
* Names should be able to tell why something exists, what it does, and how it is used.
```php
private $elapsedTimeInDays;
private $daysSinceCreation;
private $daysSinceModification;
private $fileAgeInDays;
```

Generally, any method longer than ten lines should make you start asking questions.

# Comments

* If you feel the need to comment on something inside a method, you should take this code and put it in a new method.

* The best comment is a good name for a method or class.

* If you feel that a code fragment cannot be understood without comments, try to change the code structure in a way that makes comments unnecessary.

Controllers should be thin because controller code can’t be reused

# Project structure

* **Solution**
    * **Core** (Business or Domain Layer Project)
    * **Data** (Data Access Layer Project)
    * **UI** (UI/API Layer Project)
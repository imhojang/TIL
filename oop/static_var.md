### 🏄‍♂️ Static variable - why, what & how



Let's say that we want to create a class. How about an animal class? Okay, now let's think about what animals have all in common. They all have a cells. mass, etc. 

```swift
class Animal {
  var cells = true
  var mass = true
  
}
```

Cool. Now I can create instances of an animal class, and give them all distinct properties.

```swift
let squid = Animal()
let bear = Animal()
squid.mass // true
squid.cells // true
bear.mass // true
bear.cells // true
```

Squid and bear both now have cells and mass as its properties. But each animal has cells and mass property as its own property. If all animals share these properties, is it necessary to have the property bind to each animal? What if we could make a property to the class instead of the object? That way we can define a property of an animal class.  



We can acheive this by putting the keyword `static` in front of variable declaration.   

```swift
class Animal {
  static var cells = true
  static var mass = true
}
```

Now the properties `cells`and `mass` have moved to animal class from animal objects.

```swift
Animal.cells // true
Animal.mass // true
```

**The ` static` keyword makes a property of a class attaches to the class itself instead of the instance of the object. **



Another example of how a `static` keyword could be used is when you want to apply a singleton design pattern and create a unique object.



```swift
class SomeSingletonOjbect {
  static let sharedInstance = Singleton()
  
  private init () {}
  
  func someMethod () {}
}
```



```swift
SomeSingletonObject.sharedInstance.someMethod()
```

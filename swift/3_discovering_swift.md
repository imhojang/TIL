## Discovering Swift 🦅



Today I ran into a website where I can self-analyze my swift skillset with some interesting set of quizzes. Here I have listed some Swift grammer insights, and questions that I got it wrong / want to review later. 



Link to Swift Quiz: https://www.hackingwithswift.com/test



---



```swift

enum CompassDirection: CaseIterable {

​    *case* north, south, east, west

}



print("There are \(CompassDirection.allCases.count) directions.")

// *Prints "There are 4 directions."*

let caseList = CompassDirection.allCases

​                               .map({ "\($0)" })

​                               .joined(separator: ", ")

// *caseList == "north, south, east, west"*

```





#### CaseIterable



\[Protocol]



A type that provides a collection of all of its value



Types that conform to the `CaseIterable` protocol are typically enumerations without associated values. When using a `CaseIterable` type, you can access a collection of all of the type’s cases by using the type’s `allCases` property.





---



####  Answer Review 🙆🏻‍♀️🙅🏿‍♂️



Score : 11/20 😱



What output will be produced by the code below?



\#1 Initialization of Classes



```swift

class Starship {

​    var type: String

​    var age: Int

}



let serenity = Starship(type: "Firefly", age: 24)

print(serenity.type)

```



Question: What output will be produced by the code below?



My Answer: `"Firefly"`



Correct Answer: `This code will not compile`



Explanation: Struct have memberwise initialization as standard, but this is not available to classes. The code will fail to compile because the ****Starship**** class has no initializers.





\#2 Joining of the arrays



```swift

let first = ["Sulaco", "Nostromo"]

let second = ["X-Wing", "TIE Fighter"]

let third = first + second

```



Question: What output will be produced by the code below?



My Answer & Correct Answer : `["Sulaco", "Nostromo", "X-Wing", "TIE Fighter"]`



Explanation: Swift arrays can be joined together using the ****+**** operator, which adds the right-hand array to the end of the left-hand.





\#3



```swift

let oneMillion = 1_000_000

let oneThousand = oneMillion / 0_1_0_0_0

print(oneThousand)

```



Question: What output will be produced by the code below?



My Answer & Correct Answer: `1000`



Explanation: Swift allows you to ****use any number of leading zeros before a number****, and ****any number of underscores inside a number****, in order ****to make reading easier****. The example given, 0_1_0_0_0, is unlikely, but a perfectly valid way to write 1000.





\#4 Default data type of a number with decimals



```swift

let i = 10.2

```



Question: Given the code above, what data type does `i` have?



My Answer: `Float`



Correct Answer: `Double`



Explanation: When given a floating-point number, Swift's type inference will use the ****Double**** data type.





\#5 Inheritance of classes: `Final` keyword



```swift

*final* class Dog {

​    func *bark*() {

​        print("Woof!")

​    }

}



class Corgi : Dog {

​    *override* func *bark*() {

​        print("Yip!")

​    }

}



let muttface = Corgi()

muttface.bark()

```



Question: What output will be produced by the code below?



My Answer: `"Woof!"`



Correct Answer: `The code will not compile`



Explanation: The `Dog` class is marked as `final`. This means that the class cannot be inherited from. Therefore, the class `Corgi` cannot inherit class `Dog`. 





\#7



```swift

var i = 2

*do* {

  print(i)

  i *= 2

} *while* (i < 128)

```



Question: What output will be produced by the code below?



My Answer: `2 4, 8, 16, 32, 64`



Correct Answer: `This code will not compile.`



Explanation: The `do` keyword is invalid here; should use `repeat` instead.





\#8 UInt



```swift

let num = UInt.min

```



Question: When this code is executed, what value will `num` have?



My Answer & Correct Answer : `0`



Explanation: `UInt` stands for `unsigned integer`, and indicates integer with zero and positive values, excluding negative values. Therefore, the minimum value of unsigned integer is zero.



\#9



```swift

*for* i *in* 3...1 {

  print(i)

}

```



Question: What output will be produced by the code below?



My Answer: `This code will not compile.`



Correct Answer: `This code will compile but crash.`



Explanation: This code will compile successfully, but crash at runtime. Swift does not allow you to generate ranges where the initial value is greater than the end value.



\#10



Which Swift compiler directive will force the compiler to issue an error?



- \#error

- @error

- !error

- _ERROR

- none



My Answer: `@error`



Correct Answer: `#error`



Explanation: The `#error` compiler directive forces Switch to issue an error. It's useful when you're sending code to someone and they need to fill in an important value, such as an API key.



\#11



```swift

let names = ["Amy", "Clara"]



*for* i *in* 0 ... names.length {

  print("Hello, \(names[i])!")

}

```



Question: What output will be produced by the code below?



My answer: `This code will compile but crash.`



Correct answer: `This code will not compile.`



Explanation: Swift arrays do not have a `length` property, this code should use `count`.



With that replacement, the code will compile, but will then crash becasue it uses the closed range operator (...), which will cause an ****out-of-bounds error**** when reading into the array.





\#12



```swift

enum Weather {

  *case* sunny

  *case* cloudy

  *case* windy(speed: Int)

}



let today: Weather = .windy(speed: 10)



*switch* today {

*case* .sunny, .cloudy: 

  print("It's not that windy")

*case* .windy(let speed) *where* speed >= 10:

  print("It's very windy")

*default*:

  print("It's a bit windy")

}

```



Question: What output will be produced by the code below?



My Answer & Correct Answer: `It's very windy`



Explanation: The `windy` case value has an associated value to store the wind speed as an integer. In the code, this is set to 10, which means the "It's very windy" case will be triggered in the `switch` block



\#13



```swift

let names = ["Chris", "Joe", "Doug", "Jordan"]



*if* let name = names[1] {

​    print("Brought to you by \(name)")

}

```



Question: What output will be produced by the code below?



My Answer: `"Brought to you by Joe"`



Correct Answer: `This code will not compile`



Explanation: ****Subscripting an array of strings will return a** `**String**` **rather than** `**String?**`**, which means that it is a compile error to attempt to unwrap it using `if let`.



\#14



```swift

let names = ["Serenity", "Sulaco", "Enterprise", "Galactica"]



*if* let last = names.last {

  print(last)

}

```



Question: What output will be produced by the code below?



My Answer: `Optional("Galactica")`



Correct Answer: `"Galactica"`



Explanation: Using `names.last` will return an optional string, but the `if let` unwraps that safely to produce "Galactica".



\#15

Question: How many bits are used to store an `Int`?

My Answer: `16 bit`

Correct Answer: `Depends on the device`

Explanation: Swift's integers are 32-bit on 32-bit devices such as iPhone 5 and earlier, and 64-bit on 64-bit devices such as iPhone 5s and later.



\#16

```swift
var motto = "Bow ties are cool."
motto.replacingOccurrences(of: "Bow", with: "Neck")
print(motto)
```

Question: What output will be produced by the code above?

My Answer: `"Nect ties are cool"`

Correct Answer: `"Bow ties are cool"`

Explanation: The `replacingOccurrences()` method returns a new string with its change effected, rather than modifying it in place. In this code, that return value is being discarded, so the original motto variable remains unchanged.



\#17

```swift
let names \ ["Amy", "Rory"]

for name in names {
  name = name.uppercased()
  print("HELLO, \()!")
}
```

What output will be produced by the code below?

My Answer & Correct Answer: `This code will not compile`

Explanation: This code will not compile because it modifies name inside the loop. If you want to do this, you must use the `var` keyword like this:  

```swift
for var name in names
```

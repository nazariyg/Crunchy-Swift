# Swift 2

## Output

```swift

print("Hello there!")
print("He", "llo", separator: "", terminator: " there!")  // "Hello there!"

print("one"); print("two")

```

## Data Types

* `AnyObject` can represent an instance of any class type
* `Any` can represent an instance of any type at all, including function types

```swift

let strValue = "Hello, there!"
let intValue = 1234
let boolValue = true
let floatValue:Float = 1.0
let floatValueCG:CGFloat = 1.0
let doubleValue = 1.0
let charValue:Character = "a"
let valueDiv = 1.0/4.0
let valueIntDiv:CGFloat = 200/255
var voidValue:Void
var x = 0.0, y = 0.0, z = 0.0
var red, green, blue : Double?
var `var` = 1234

let intValue8:Int8 = 0
let intValue16:Int16 = 0
let intValue32:Int32 = 0
let intValue64:Int64 = 0
let intValueU:UInt = 0
let intValueU8:UInt8 = 0
let intValueU16:UInt16 = 0
let intValueU32:UInt32 = 0
let intValueU64:UInt64 = 0

let fpValue = 1e-06
let hValue = 0xFF
let bValue = 0b101
let iValue = 001_234

Int8.min
Int16.min
Int32.min
Int.min

Int8.max
Int16.max
Int32.max
Int.max

typealias MyType = UInt16

```

## Operators

```swift

5.0 % 2.0                   // 1.0, unlike in C
a..<b                       // half-open range operator, non-inclusive
a...b                       // closed range operator, inclusive
if x = y                    // not allowed
a &+ b                      // allow value overflow
let val = optValue ?? 1234  // nil coalescing

```

## Constants & Variables

```swift

let constant = 6
var variable = 7
variable = 8

// string interpolation
let apples = 3
let oranges = 5
let fruitSummary = "I have \(apples + oranges) pieces of fruit."  // evaluation
print("Heya \(abs(Float(intValue)*2.8))")
let (x, y) = (1, 2)

// tuple
let aTuple = ("one", "two", "three")
print(aTuple.0)
print(aTuple.1)
print(aTuple.2)
let p1 = (1, 2)
let (x1, y1) = p1  // decompose
print(x1, y1)
let (x2, _) = p1
let x3 = p1.0, y3 = p1.1
let p2 = (x: 1, y: 2)
let x4 = p2.x, y4 = p2.y

```

## String

* string characters represent extended grapheme clusters; an EGC can be composed of multiple Unicode code points

```swift

let strValue = "Hello, there!"
print(strValue.characters.count)  // expensive (due to UTF-8)
let charValue:Character = "a"
for character in "Dog!".characters
{
    print(character)
}
let catCharacters:[Character] = ["C", "a", "t", "!"]
let catString = String(catCharacters)
let string1 = "hello"
let string2 = " there"
var welcome = string1 + string2
// \u{n}, where n is a 1–8 digit hexadecimal number
let eAcute:Character = "\u{E9}"                 // é
let combinedEAcute:Character = "\u{65}\u{301}"  // e followed by ́ = é EGC
let greeting = "Guten Tag!"
greeting[greeting.startIndex]              // G
greeting[greeting.endIndex.predecessor()]  // !
greeting[greeting.startIndex.successor()]  // u
let index = greeting.startIndex.advancedBy(7)
greeting[index]  // a
for index in greeting.characters.indices  // range
{
    print(greeting[index])
}
var welcome = "hello"
welcome.insert("!", atIndex: welcome.endIndex)
welcome.insertContentsOf(" there".characters, at: welcome.endIndex.predecessor())
let range = welcome.endIndex.advancedBy(-6)..<welcome.endIndex
welcome.removeRange(range)
// strings are compared by canonical equivalence (and not by binary equivalence)
str.utf8
str.utf16
str.unicodeScalars  // (UInt32)

```

## Collection Types

```swift

// array
var anArray = [
    "one",
    "two",
    "three",
]
print(anArray[1])
print(anArray.count)
anArray += ["four"]
anArray.append("five")
anArray += ["six", "seven"]
anArray[0] = "uno"
anArray.insert("zero", atIndex: 0)
anArray.removeLast()
anArray.removeAtIndex(0)
if !anArray.isEmpty
{
    for str in anArray
    {
        print(str)
    }
}
var floatArray = [Float]()
floatArray.append(0.5)
floatArray.append(1.5)
var threeDoubles = [Double](count: 3, repeatedValue: 0.0)  // 3 initial values
var anArray2 = [
    "one",
    "two",
    "three",
    "four",
    "five",
    "six",
    "seven"
]
anArray2[0...1] = ["1", "2"]
for (index, value) in anArray2.enumerate()
{
    //
}

```

```swift

// dictionary
var aDict = [
    "one": 1,
    "two": 2,
    "three": 3,
]
for str in anArray
{
    print(str)
}
for (key, value) in aDict
{
    print("\(key): \(value)")
}
for key in aDict.keys
{
    //
}
for key in aDict.keys.sort()
{
    //
}
for value in aDict.values
{
    //
}
let keys = [String](aDict.keys)
aDict["three"] = 33
aDict.removeValueForKey("two")  // or aDict["two"] = nil
print(aDict.count)
var anotherDict = [String: Int]()

```

```swift

// set
var letters = Set<Character>()
letters.insert("a")
var favoriteGenres:Set = ["Rock", "Classical", "Hip hop"]
for genre in favoriteGenres
{
    //
}
for genre in favoriteGenres.sort()
{
    //
}
a.union(b)
a.intersect(b)
a.subtract(b)
a.exclusiveOr(b)
a == b
a.isSubsetOf(b)
a.isSupersetOf(b)
a.isStrictSubsetOf(b)    // false if equal
a.isStrictSupersetOf(b)  // false if equal
a.isDisjointWith(b)

```

## Optionals

```swift

var optValue:Int? = 10
print(optValue!)
optValue = nil
if optValue != nil
{
    print("value: \(optValue!)")
}
if let val = optValue  // optional binding (if, while)
{
    print("value: \(val)")
}
else
{
    print("Nope")
}
if var val = optValue
{
    val = 11
    print("value: \(val)")
}
let val = optValue ?? 1234
if let data = widget.data where data.isValid,
   let source = sourceIP(), dest = destIP()
{
    // do something
}
if let a = a, b = b, c = c where c != 0
{
    // do something
}
var iuOptValue:Int! = 10  // implicitly unwrapped

// optional chaining
if let roomCount = john.residence?.numberOfRooms
{
    print("John's residence has \(roomCount) room(s).")
}
else
{
    print("Unable to retrieve the number of rooms.")
}
if john.residence?.printNumberOfRooms() != nil  // Void?
{
    print("It was possible to print the number of rooms.")
}
else
{
    print("It was not possible to print the number of rooms.")
}
john.residence?.address = someAddress
john.residence?[0].name

```

## Control Flow

```swift

// if
if strValue.lowercaseString == "HELLO, there!".lowercaseString
{
    print("Hi, there!")
}
else if strValue.isEmpty
{
    print("Nuffin.")
}
else
{
    print("Just hi")
}

// guard
func greet (person:[String: String])
{
    guard let name = person["name"] else
    {
        return
    }
    print("Hello \(name)!")
    guard let location = person["location"] else
    {
        print("I hope the weather is nice near you.")
        return
    }
    print("I hope the weather is nice in \(location).")
}

// for
for i in 0..<10
{
    print(i)
}
for i in 0...9
{
    print(i)
}
for _ in 0..<3
{
    //
}
for value in array[1..<array.count]
{
    //
}
myloop0: for i in 0...9
{
    myloop1: for j in 0...9
    {
        if i == 5
        {
            break myloop0
        }
        print(i)
    }
}
for (key, value) in aDict
{
    print("\(key): \(value)")
}

// while/repeat-while
var n = 2
while n < 100
{
    n = n*2
}
print(n)
var m = 2
repeat
{
    m = m*2
} while m < 100
print(m)

// switch
// no implicit fallthrough, must be exhaustive
switch varValue
{
case 0:
    print("0")
case 1:
    print("1")
case 2...5:  // interval matching
    print("2 through 5")
    if false
    {
        break
    }
case 6, 7:
    print("6 or 7")
case let x where x > 7:
    print("\(x) is greater than 7")
default:
    break
}
let point = (1, 1)
switch point
{
case (let x, 0):
    print("point on x with displacement of \(x)")
case (0, _):  // _ matches anything
    print("point on y")
case (1..<5, 1..<5):
    print("point within bounds")
case let (x, y) where x == y:
    print("point is on line")
case let (x, y):
    print("point out of bounds at \(x), \(y)")
}

// availability
if #available(iOS 9, OSX 10.10.3, *)
{
    // Use iOS 9 APIs on iOS, and use OS X v10.10 APIs on OS X
}
else
{
    // Fall back to earlier iOS and OS X APIs
}

```

## Functional

```swift

// function and default parameter values
func aFunctionWithExternalParamName0
    (localParamName0:Int, externalParamName1 localParamName1:String = "") -> String
{
    return ""
}
aFunctionWithExternalParamName0(5678, externalParamName1:"Aloha")

// named elements in returned tuple
func aFunction2 (param1:String, _ param2:String, _ param3:String) ->
    (a:String, b:String, c:String)
{
    return (param1, param2, param3)
}
print(aFunction2("lala", "lala", "lala").a)
func returnTuple () -> (first:Int, second:String)
{
    return (5, "five")
}
let ret = returnTuple()
print(ret.1)
print(ret.first)
let (f, l) = returnTuple()  // decompose
print("\(f), \(l)")

// variable number of parameters
func sumOf (numbers:Int ...) -> Int
{
    var sum = 0
    for number in numbers
    {
        sum += number
    }
    return sum
}
print(sumOf(42, 597, 12))

// in-out parameters
func swapTwoInts (inout a:Int, inout _ b:Int)
{
    let temporaryA = a
    a = b
    b = temporaryA
}
var someInt = 3
var anotherInt = 107
swapTwoInts(&someInt, &anotherInt)

// nested function
func returnFifteen () -> Int
{
    var y = 10
    // or a closure
    func add ()
    {
        y += 5
    }
    add()
    return y
}
print(returnFifteen())

// function as a return value
func makeIncrementer () -> ((Int) -> Int)
{
    // or a closure
    func addOne (number:Int) -> Int
    {
        return 1 + number
    }
    return addOne
}
var increment = makeIncrementer()
print(increment(7))

// closure as a parameter
func getAClosure (closure:(() -> Int)
{
    for _ in 1..<3
    {
        closure()
    }
}
let aClosure = { () -> Int in
    print("Heya")
    return 0
}
getAClosure(aClosure)
getAClosure { () -> Int in
    print("Heya")
    return 0
}

func aFunc () -> Int
{
    var v = 5
    let closure = {
        v += 1
    }
    closure()
    return v
}
print(aFunc())  // 6

func aFunc ()
{
    var i = 0
    let j = { () -> Int in
        i += 1
        return i
    }
    print(j(), terminator:"")  // 1
    i += 1                     // 2
    print(j(), terminator:"")  // 3
}
aFunc()

var numbers = [20, 19, 7, 12]
let mappedNumbers = numbers.map { number in 3*number }  // implicit `return`
print(mappedNumbers)
let sortedNumbers = numbers.sort { $0 > $1 }
print(sortedNumbers)
numbers.sort(>)

// `@noescape` marks a closure parameter as exclusive to the param's function/closure
// optimization; also lets refer to `self` implicitly within the closure
func someFunctionWithNonescapingClosure (@noescape closure:(() -> Void))
{
    closure()
}

// autoclosures are used by e.g. `assert` and enable deferred execution
// `@autoclosure` attribute implies the `@noescape` attribute
func serveCustomer (@autoclosure customerProvider:(() -> String))
{
    if condition
    {
        print("Now serving \(customerProvider())!")
    }
}
serveCustomer("Joe".uppercaseString)  // call to `uppercaseString` is delayed

```

## Enumerations

* first-class type (support initializers, methods, ...)
* support computed properties only
* passed by copy
* mutating methods can substitute the value with another one by assigning to `self`

```swift

enum CompassPoint
{
    case North
    case South
    case East
    case West
}
var direction = CompassPoint.North
direction = .South

enum Rank
{
    case Ace
    case Two, Three, Four, Five, Six, Seven, Eight, Nine, Ten
    case Jack, Queen, King

    // can have methods
    func simpleDescription () -> String
    {
        switch self
        {
        case .Ace:
            return "ace"
        case .Jack:
            return "jack"
        case .Queen:
            return "queen"
        case .King:
            return "king"
        default:
            return String(self.rawValue)
        }
    }
}
let ace = Rank.Ace

// raw values
enum CollisionType : Int
{
    case Player = 1
    case Enemy = 2
}
let type = CollisionType.Player
if type == .Player
{
    print("It's a Player")
}
type.rawValue == 2  // false

// associated values
enum Computer
{
    case Desktop(Int, String)
    case Laptop(Int, String)
}
var something = Computer.Laptop(8, "i7")
switch something
{
case let .Laptop(ram, cpu):
    print("It's a \(cpu) laptop with \(ram) GB RAM.")
default:
    print("What else can it be?")
}

enum Planet : Int
{
    case Mercury = 1, Venus, Earth, Mars, Jupiter, Saturn, Uranus  // 1, 2, 3, ...
}
enum CompassPoint : String
{
    case North, South, East, West  // implicitly assigned raw values ("North", ...)
}

// recursive enumerations
enum ArithmeticExpression
{
    case Number(Int)
    indirect case Addition(ArithmeticExpression, ArithmeticExpression)
    indirect case Multiplication(ArithmeticExpression, ArithmeticExpression)
}
indirect enum ArithmeticExpression
{
    case Number(Int)
    case Addition(ArithmeticExpression, ArithmeticExpression)
    case Multiplication(ArithmeticExpression, ArithmeticExpression)
}

```

## Classes

* objects are passed by reference ("reference type")
* subclasses can override both stored and computed properties (and add a setter)
* subclasses can add property observers to inherited properties
* overriding can be prevented with `final` modifier; `final class` prevents subclassing

```swift

class ClassA
{
    // instance properties
    var name:String
    var id:Int

    // type properties
    static var storedTypeProperty = "Some value."
    // `class` instead of `static` allows for property overriding by subclasses
    class var computedTypeProperty:Int  // `class` is for computed props only
    {
        return 1
    }

    // - - - -

    init ()
    {
        name = "John Doe"
        id = 1
    }

    init (name:String, id:Int)
    {
        self.name = name
        self.id = id
    }

    deinit
    {
        print("Bye.")
    }

    // - - - -

    func aMethod (smth:Int, smthElse:Bool) -> String
    {
        return self.name
    }

    func aMethod (smth:Int, smthElse:Float) -> String
    {
        return self.name
    }

    private func aPrivM (smth:Int, smthElse:Bool) -> String
    {
        return self.aMethod(0, smthElse:true)
    }

    func description () -> String
    {
        return "My name is \(self.name) and my id is \(self.id)"
    }
}
var anObj = ClassA()
anObj.name = "Johnny Appleseed"
anObj.name
anObj.id
anObj.aMethod(0, smthElse:true)
anObj = ClassA(name:"Mary Jane", id:9)  // all parameter labels are used
print(anObj)
print(anObj.description())

class ClassB : ClassA
{
    var smth:String

    // - - - -

    override init ()
    {
        self.smth = "Something"
        super.init()
    }

    override func description () -> String
    {
        return "Hi there, my name is \(name) and my id is \(id)"
    }

    override func aMethod (smth:Int, smthElse:Float) -> String
    {
        super.aMethod(smth, smthElse)
        return self.name
    }

    // type method
    // `class` allows for overriding, `static` does not
    class func classMeth () -> String
    {
        return "Heya"
    }
}
anObj = ClassB()
print(anObj.description())

class MyClass
{
    // stored properties
    var myProperty:String
    var myOptionalProperty:String?

    // computed properties
    var myInt:Int = 1
    var doubleInt:Int
    {
        get {
            return myInt*2
        }

        set {
            myInt = newValue/2
        }
    }
    var doubleInt2:Int
    {
        get {
            return myInt*2
        }

        set(nv) {
            myInt = nv/2
        }
    }

    // property observers
    var myOutput:Int = 0
    {
        willSet {  // or `willSet(customName)`
            print("setting myOutput to \(newValue)")
        }

        didSet {  // or `didSet(customName)`
            if oldValue > 10
            {
                //
            }
        }
    }

    // methods
    func myMethod ()
    {
        // do something
    }

    // initializer
    init (myProperty:String)
    {
        // use self.varName if argument has the same name
        self.myProperty = myProperty
    }
}
let a = MyClass(myProperty: "Hello")
a.myProperty = "World"
a.myMethod()

// lazy stored properties
class DataManager
{
    lazy var importer = Importer()  // `Importer()` is deferred until first use
    var data = [String]()
}

```

## Structures

* objects are passed by copy ("value type"), same as with enumerations
* initializers are generated automatically from properties ("memberwise initializers")
* methods are not mutating by default
* mutating methods can substitute the object with another one by assigning to `self`
* cannot inherit from another structure, hence no type casting
* no `deinit`
* `String`, `Array`, `Dictionary`, and `Set` are structures (copying is "smart")

```swift

struct StructA
{
    var prop = 1234

    // - - - -

    func returnProp1 () -> Int
    {
        return prop
    }

    mutating func returnProp2 () -> Int
    {
        prop = 5678
        return prop
    }
}
var s = StructA()
s.returnProp1()
s.returnProp2()

```

## Initialization & Deinitialization

* when setting initial value for a stored property within an initializer, the value is set without calling any property observers
* specifying default property value as part of the property's declaration is preferable to specifying the property's value in the initializer
* initializers can be overloaded by signature (external parameter names) just as methods
* an initializer is the second and last place where a constant instance property can be set
* value types (structs, enums) can calls `self.init` within an initializer ("initializer delegation") for reducing code duplication
* designated initializers are the primary initializers for a class; a designated initializer fully initializes all properties introduced by that class and calls an appropriate superclass initializer to continue the initialization process up the superclass chain
* designated initializers are not marked with any modifier and a class can have multiple designated initializers
* a class without an explicit initializer get a default designated initializer implicitly (can be overridden by subclasses)
* designated initializers are "funnel" points through which initialization takes place
* convenience initializers are secondary, supporting initializers for a class, which call a designated initializer (with `self.init`) from the same class to create an instance of that class for a specific use case or input value type
* convenience initializers are marked with `convenience` modifier
* rules: a) a designated initializer must call a designated initializer from its immediate superclass b) a convenience initializer must call another initializer from the same class c) a convenience initializer must ultimately call a designated initializer
* designated initializers must always delegate up, convenience initializers must always delegate across
* two-phase initialization: 1: each stored property is assigned an initial value; 2: stored properties are optionally customized (in initializers)
* safety check 1 in two-phase initialization: a designated initializer must ensure that all of the properties introduced by its class are initialized before it delegates up to a superclass initializer; 2: a designated initializer must delegate up to a superclass initializer before assigning a value to an inherited property; 3: a convenience initializer must delegate to another initializer before assigning a value to any property; 4: an initializer cannot call any instance methods, read the values of any instance properties, or refer to self as a value until after the first phase of initialization is complete
* there is no need to write the `override` modifier when providing a matching implementation of a superclass convenience initializer because a superclass convenience initializer cannot be called for the subclass anyways
* automatic initializer inheritance: if a subclass doesn't define any designated initializers, it automatically inherits all of its superclass **designated** initializers; if a subclass provides an implementation of all of its superclass designated initializers, then it automatically inherits all of the superclass **convenience** initializers
* a failable initializer of a class, structure, or enumeration can delegate across to another failable initializer; if another initializer causes initialization to fail, the entire initialization process fails immediately
* it is possible to override a superclass failable initializer with a subclass nonfailable initializer but not the other way around
* deinitializers are only available on class types
* Swift automatically provides a default initializer without any arguments for any structure or base class that provides default values for all of its properties and does not provide at least one initializer itself

```swift

class ClassA
{
    let prop:Int

    init ()
    {
        self.prop = 1234
    }
}
class ClassB : ClassA
{
}
let o = ClassB()
print(o.prop)  // 1234

class Food
{
    var name: String
    init (name: String)
    {
        self.name = name
    }
    convenience init ()
    {
        self.init(name: "[Unnamed]")
    }
}

// failable initializer
struct Animal
{
    let species:String
    init? (species:String)
    {
        if species.isEmpty
        {
            return nil
        }
        self.species = species
    }
}
enum TemperatureUnit
{
    case Kelvin, Celsius, Fahrenheit

    init? (symbol:Character)
    {
        switch symbol
        {
        case "K":
            self = .Kelvin
        case "C":
            self = .Celsius
        case "F":
            self = .Fahrenheit
        default:
            return nil
        }
    }
}

class SomeClass
{
    // every subclass of the class must implement this initializer, marking it with `required`
    required init (someValue:String)
    {
        //
    }
}

class SomeClass
{
    let someProperty:SomeType = {
        // create a default value for someProperty inside this closure when initialized
        return someValue
    }()
}

class SomeClass
{
    deinit
    {
        // perform the deinitialization
    }
}

```

## Strong & Weak References

* `weak` reference is used whenever it is valid for that reference to become nil at some point during its lifetime; conversely, `unowned` reference is used when it is assumed to **always** have a value because the referenced object(s) never goes out of existence while the reference is in use

```swift

// capture list
let closure = { [unowned self, weak delegate = self.delegate!] in
    // closure body goes here
}

```

## Subscripts

```swift

subscript (index:Int) -> Int
{
    get {
        // return an appropriate subscript value here
    }

    set {
        // newValue
    }
}

subscript (index:Int) -> Int
{
    // return an appropriate subscript value here
}

subscript (row:Int, column:Int) -> Double
{
    //
}

```

## Extensions

* can: add computed instance properties and computed type properties, define instance methods and type methods, provide new initializers, define subscripts, define and use new nested types, make an existing type conform to a protocol
* cannot: override existing functionality

```swift

extension SomeType
{
    // new functionality to add to SomeType goes here
}

extension SomeType : SomeProtocol, AnotherProtocol
{
    // implementation of protocol requirements goes here
}

extension Rect
{
    init (center:Point, size:Size)
    {
        let originX = center.x - size.width/2
        let originY = center.y - size.height/2
        self.init(origin: Point(x: originX, y: originY), size: size)
    }
}

extension Int
{
    mutating func square ()
    {
        self = self*self
    }
}
var someInt = 3
someInt.square()

```

## Protocols

* a protocol defines a blueprint of methods, properties, and other requirements that suit a particular task or piece of functionality
* a protocol can be extended to provide default implementations for some functionality
* when marking a protocol instance method requirement as `mutating`, there's no need to write the mutating keyword when writing an implementation of that method
* protocols can be used as types
* it is possible to extend an existing type to adopt and conform to a new protocol
* one can use the `is` and `as` operators to check for protocol conformance, and to cast to a specific protocol

```swift

protocol ProtocolA
{
    func impThisMeth () -> Int
    var impThisVar:Bool { get set }
    mutating func adjust ()
}

class ClassP : ProtocolA
{
    var ivar:Bool

    // - - - -

    var impThisVar:Bool
    {
        get {
            return self.ivar
        }

        set {
            self.ivar = newValue
        }
    }

    init ()
    {
        ivar = true
    }

    func impThisMeth() -> Int
    {
        return 0
    }

    func adjust ()
    {
    }
}

// property requirements are always declared as `var` properties; can be satisfied with computed
protocol SomeProtocol
{
    var mustBeSettable:Int { get set }
    var doesNotNeedToBeSettable:Int { get }

    // can be satisfied with `class` type property or method too
    static var someTypeProperty:Int { get set }
    static func someTypeMethod ()
}

protocol SomeProtocol
{
    init (someParameter:Int)
}
class SomeClass : SomeProtocol
{
    required init (someParameter:Int)  // `required` is mandatory
    {
        // initializer implementation goes here
    }
}

protocol SomeProtocol
{
    init ()
}
class SomeSuperClass
{
    init ()
    {
        // initializer implementation goes here
    }
}
class SomeSubClass : SomeSuperClass, SomeProtocol
{
    // "required" from SomeProtocol conformance; "override" from SomeSuperClass
    required override init ()
    {
        // initializer implementation goes here
    }
}

// declaring protocol adoption with an extension
protocol TextRepresentable
{
    var textualDescription:String { get }
}
extension Dice : TextRepresentable
{
    var textualDescription:String
    {
        return "A \(sides)-sided dice"
    }
}

// protocol inheritance
protocol InheritingProtocol : SomeProtocol, AnotherProtocol
{
    // protocol definition goes here
}

// it is possible to limit protocol adoption to class types (and not structures or enumerations)
// by adding the class keyword to a protocol's inheritance list
protocol SomeClassOnlyProtocol : class, SomeInheritedProtocol
{
    // class-only protocol definition goes here
}

// protocol compositions
protocol Named
{
    var name:String { get }
}
protocol Aged
{
    var age:Int { get }
}
func wishHappyBirthday (celebrator:protocol<Named, Aged>)
{
    print("Happy birthday \(celebrator.name) - you're \(celebrator.age)!")
}

// optional protocol requirements
// implementing classes are marked with `@objc` and inherit from `NSObject`
@objc protocol CounterDataSource
{
    optional func incrementForCount (count:Int) -> Int
    optional var fixedIncrement:Int { get }
}
class Counter
{
    var count = 0
    var dataSource:CounterDataSource?

    func increment ()
    {
        // `incrementForCount` and `fixedIncrement` are optional types (not return types)
        if let amount = dataSource?.incrementForCount?(count)
        {
            count += amount
        }
        else if let amount = dataSource?.fixedIncrement
        {
            count += amount
        }
    }
}

// protocol extensions
extension RandomNumberGenerator  // `RandomNumberGenerator` is an existing protocol
{
    func randomBool () -> Bool
    {
        return random() > 0.5
    }
}

// protocol extension constrains
extension CollectionType where Generator.Element:TextRepresentable
{
    var textualDescription:String
    {
        let itemsAsText = self.map { $0.textualDescription }
        return "[" + itemsAsText.joinWithSeparator(", ") + "]"
    }
}

```

## Generics

```swift

func aGenFunc<T> (param:T) -> T
{
    print(param is Int)
    return param
}
aGenFunc(0)
aGenFunc("Hello")

enum OptionalValue <WrappedT>
{
    case None
    case Some(WrappedT)
}
var possibleInteger:OptionalValue<Int> = .None
possibleInteger = .Some(100)

// type constraints specify that a type parameter must inherit from a specific class, or
// conform to a particular protocol or protocol composition
func someFunction<T:SomeClass, U:SomeProtocol> (someT:T, someU:U)
{
    // function body goes here
}
func anyCommonElements
    <T:SequenceType, U:SequenceType where T.Generator.Element:Equatable,
        T.Generator.Element == U.Generator.Element> (lhs: T, _ rhs: U) ->
            Bool
{
    for lhsItem in lhs
    {
        for rhsItem in rhs
        {
            if lhsItem == rhsItem
            {
                return true
            }
        }
    }
    return false
}
anyCommonElements([1, 2, 3], [3])

// when extending a generic type, there's no need to provide a type parameter list as part of
// the extension's definition
extension Stack
{
    var topItem:Element?
    {
        return items.isEmpty ? nil : items[items.count - 1]
    }
}

// associated types
protocol Container
{
    associatedtype ItemType

    mutating func append (item:ItemType)
    var count:Int { get }
    subscript (i:Int) -> ItemType { get }
}
struct IntStack : Container
{
    // original IntStack implementation
    var items = [Int]()
    mutating func push (item:Int)
    {
        items.append(item)
    }
    mutating func pop () -> Int
    {
        return items.removeLast()
    }

    // conformance to the Container protocol
    typealias ItemType = Int
    mutating func append (item:Int)
    {
        self.push(item)
    }
    var count:Int
    {
        return items.count
    }
    subscript (i:Int) -> Int
    {
        return items[i]
    }
}

```

## Error Handling

* errors are represented by values of types that conform to the ErrorType protocol
* a throwing function propagates errors that are thrown inside of it to the scope from which it's called
* if none of the catch clauses handle the error, the error propagates to the surrounding scope
* `defer` statement lets execute a set of statements just before code execution leaves the current block of code (including via `throw`, `return`, `break` etc.); deferred actions are executed in reverse order of how they are specified

```swift

func makeASandwich () throws -> ReturnType
{
    // ...
}

do
{
    try makeASandwich()
    eatASandwich()
}
catch Error.OutOfCleanDishes
{
    washDishes()
}
catch Error.MissingIngredients(let ingredients)  // where ...
{
    buyGroceries(ingredients)
}

enum VendingMachineError : ErrorType
{
    case InvalidSelection
    case InsufficientFunds(coinsNeeded: Int)
    case OutOfStock
}
func ...
{
    // ...
    throw VendingMachineError.InsufficientFunds(coinsNeeded: 5)
}

func vend (itemNamed name:String) throws
{
    guard let item = inventory[name] else
    {
        throw VendingMachineError.InvalidSelection
    }

    guard item.count > 0 else
    {
        throw VendingMachineError.OutOfStock
    }

    guard item.price <= coinsDeposited else
    {
        throw VendingMachineError.InsufficientFunds(coinsNeeded: item.price - coinsDeposited)
    }

    // ...
}
func buyFavoriteSnack (person:String, vendingMachine:VendingMachine) throws
{
    let snackName = favoriteSnacks[person] ?? "Candy Bar"

    try vendingMachine.vend(itemNamed: snackName)  // propagate error up
    // or, disabling error propagation if no error can occur
    try! vendingMachine.vend(itemNamed: snackName)
    // or, converting to an optional value
    var optValue = try? vendingMachine.vend(itemNamed: snackName)
}

// throwing initializer
init (name:String, vendingMachine:VendingMachine) throws
{
    try vendingMachine.vend(itemNamed: name)
    self.name = name
}

func processFile (filename:String) throws
{
    if exists(filename)
    {
        let file = open(filename)
        defer
        {
            close(file)
        }
        while let line = try file.readline()
        {
            // Work with the file.
        }
        // close(file) is called here, at the end of the scope.
    }
}

// assertions
let age = -3
assert(age >= 0, "A person's age cannot be less than zero")
assert(age >= 0)

```

## Access Control

* `public` access enables entities to be used within any source file from their defining module, and also in a source file from another module that imports the defining module. One typically uses public access when specifying the public interface to a framework.
* `internal` access enables entities to be used within any source file from their defining module, but not in any source file outside of that module. One typically uses internal access when defining an app's or a framework's internal structure.
* `private` access restricts the use of an entity to its own defining source file. One uses private access to hide the implementation details of a specific piece of functionality.
* `internal` access is the default
* no entity can be defined in terms of another entity that has a lower (more restrictive) access level
* a unit test target can access any internal entity, if one marks the import declaration for a product module with the @testable attribute and compile that product module with testing enabled
* the access control level of a type also affects the default access level of that type's members (its properties, methods, initializers, and subscripts)
* a public type defaults to having internal members, not public members
* the access level for a tuple type is the most restrictive access level of all types used in that tuple; the access level for a function type is calculated as the most restrictive access level of the function's parameter types and return type; the individual cases of an enumeration automatically receive the same access level as the enumeration they belong to
* nested types defined within a private type have an automatic access level of private; nested types defined within a public type or an internal type have an automatic access level of internal
* a subclass cannot have a higher access level than its superclass
* a default initializer has the same access level as the type it initializes, unless that type is defined as `public` in which case the implicitly used access level is `internal`

```swift

// for stored or computed property, one can give a setter a lower access level than its
// corresponding getter
struct TrackedString
{
    private(set) var numberOfEdits = 0  // or `public private(set)`
}

```

## Operator Overloading

```swift

struct Vector2D
{
    var x = 0.0, y = 0.0
}
func + (left:Vector2D, right:Vector2D) -> Vector2D
{
    return Vector2D(x: left.x + right.x, y: left.y + right.y)
}
let vector = Vector2D(x: 3.0, y: 1.0)
let anotherVector = Vector2D(x: 2.0, y: 4.0)
let combinedVector = vector + anotherVector

// unary operators are using `prefix` and `postfix` modifiers
prefix func - (vector:Vector2D) -> Vector2D
{
    return Vector2D(x: -vector.x, y: -vector.y)
}

// compound assignment operators
func += (inout left:Vector2D, right:Vector2D)
{
    left = left + right  // using an existing operator implementation
}

// equivalence operators
func == (left:Vector2D, right:Vector2D) -> Bool
{
    return (left.x == right.x) && (left.y == right.y)
}
func != (left:Vector2D, right:Vector2D) -> Bool
{
    return !(left == right)
}

// custom operators are declared at a global level using `operator` keyword, and are marked
// with the `prefix`, `infix` or `postfix` modifiers
prefix operator +++ {}

```


# Swift 3 & 4

API naming convention optimization: the concluding parts of method names are now constituting the external label of the first parameter, removed redundancy in names.

```swift

addQuadCurve(to: endPoint, controlPoint: controlPoint)
FileManager.default.urls(for: .documentDirectory, in: .userDomainMask)
array.remove(at: 3)
names.index(of: "Anna")
animals.insert("Koala", at: 0)
helloString.appending("world")
UIColor.blue.withAlphaComponent(0.5)
Bundle.main
override func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int { ... }

```

GCD & Core Graphics

```swift

DispatchQueue.global(qos: .userInitiated).async {
    // ...
    DispatchQueue.main.async {
        // ...
    }
}

DispatchQueue.main.asyncAfter(deadline: .now() + delayInSeconds) {
    // ...
}

let concurrentPhotoQueue = DispatchQueue(label: "com.queue", attributes: .concurrent)

{
    guard let context = UIGraphicsGetCurrentContext() else {
        return
    }
    let startAngle: CGFloat = 0.0
    let endAngle = 2 * CGFloat.pi
    let strokeWidth: CGFloat = 1.0
    let center = CGPoint(x: self.frame.midX, y: self.frame.midY)
    let radius = self.frame.midX - strokeWidth
    context.setStrokeColor(UIColor.red.cgColor)
    context.setLineWidth(strokeWidth)
    context.setFillColor(UIColor.clear.cgColor)
    context.addArc(
        center: center,
        radius: radius,
        startAngle: startAngle,
        endAngle: endAngle,
        clockwise: false)
    context.drawPath(using: .stroke)
}

```

Lower camel case replaces upper camel case for enumeration cases.

```swift

UIStatusBarStyle.lightContent
SKLabelVerticalAlignmentMode.center

```

Modifying/non-modifying status in method naming.

```swift

let ages = [21, 10, 2]
ages.sorted()
var ages = [21, 10, 2]
ages.sort()

```

Replaces `self.dynamicType` with `Self`.

```swift

struct CustomStruct
{
    static func staticMethod () { ... }
    func instanceMethod ()
    {
        Self.staticMethod()
    }
}
let customStruct = CustomStruct()
customStruct.Self.staticMethod()

```

Adds inline sequences.

```swift

for view in sequence(first: someView, next: { $0.superview })
{
    // someView, someView.superview, someView.superview.superview, ...
}

for x in sequence(first: 0.1, next: { $0*2 }).prefix(while: { $0 < 4 })
{
    // 0.1, 0.2, 0.4, 0.8, 1.6, 3.2
}

```

Floating-point onstant type inference.

```swift

let circumference = 2*.pi*radius

```

Generics type constraints can go beneath the function signature.

```swift

func allItemsMatch
    <C1:Container, C2:Container>
    (_ someContainer:C1, _ anotherContainer:C2) -> Bool
    where C1.Item == C2.Item, C1.Item:Equatable
{
    // ...
}

```

Removes the need for a `characters` array on String, a string conforms to `Sequence` and `Collection` protocols.

```swift

let galaxy = "Milky Way 🐮"
for char in galaxy
{
    print(char)
}

galaxy.count       // 11
galaxy.isEmpty     // false
galaxy.dropFirst() // "ilky Way 🐮"
String(galaxy.reversed()) // "🐮 yaW ykliM"
// Filter out any none ASCII characters
galaxy.filter { char in
    let isASCII = char.unicodeScalars.reduce(true, { $0 && $1.isASCII })
    return isASCII
} // "Milky Way "

```

Adds the `Substring` type for referencing a subsequence on `String`.

```swift

let endIndex = galaxy.index(galaxy.startIndex, offsetBy: 3)
var milkSubstring:Substring = galaxy[galaxy.startIndex...endIndex]   // "Milk"

```

Sequence based Initialization.

```swift

let nearestStarNames = ["Proxima Centauri", "Alpha Centauri A", "Alpha Centauri B", "Barnard's Star", "Wolf 359"]
let nearestStarDistances = [4.24, 4.37, 4.37, 5.96, 7.78]
let starDistanceDict = Dictionary(uniqueKeysWithValues: zip(nearestStarNames, nearestStarDistances))
// ["Wolf 359": 7.78, "Alpha Centauri B": 4.37, "Proxima Centauri": 4.24, "Alpha Centauri A": 4.37, "Barnard's Star": 5.96]

```

Filtering and mapping for `Dictionary` and `Set` classes.

```swift

let closeStars = starDistanceDict.filter { $0.value < 5.0 }
let mappedCloseStars = closeStars.mapValues { "\($0)" }

```

Dictionary default values.

```swift

let siriusDistance = mappedCloseStars["Wolf 359", default: "unknown"]

```

Dictionary grouping.

```swift

let starsByFirstLetter = Dictionary(grouping: nearestStarNames) { $0.first! }
// ["B": ["Barnard's Star"], "A": ["Alpha Centauri A", "Alpha Centauri B"], "W": ["Wolf 359"], "P": ["Proxima Centauri"]]

```

Reserving capacity for `Sequence` and `Dictionary` protocols.

```swift

starWordsCount.capacity  // 6
starWordsCount.reserveCapacity(20) // reserves at least 20 elements of capacity
starWordsCount.capacity // 24

```

References key paths on types to get/set the underlying value of an instance.

```swift

let nameKeyPath = \ForceUser.name
let obiwanName = obiwan[keyPath: nameKeyPath]

```

Multi-line string literals.

```swift

let star = "⭐️"
let introString = """
A long time ago in a galaxy far,
far away....

You could write multi-lined strings
without "escaping" single quotes.

The indentation of the closing quotes
   below deside where the text line
begins.

You can even dynamically add values
from properties: \(star)
"""
print(introString)

```

One-sided ranges.

```swift

var planets = ["Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune"]
let outsideAsteroidBelt = planets[4...] // Before: planets[4..<planets.endIndex]
let firstThree = planets[..<4]          // Before: planets[planets.startIndex..<4]

```

Infinite sequence.

```swift

// Infinite range: 1...infinity
var numberedPlanets = Array(zip(1..., planets))
print(numberedPlanets) // [(1, "Mercury"), (2, "Venus"), ..., (8, "Neptune")]
planets.append("Pluto")
numberedPlanets = Array(zip(1..., planets))
print(numberedPlanets) // [(1, "Mercury"), (2, "Venus"), ..., (9, "Pluto")]

```

Pattern matching.

```swift

func temperature (planetNumber:Int)
{
    switch planetNumber
    {
        case ...2: // anything less than or equal to 2
            print("Too hot")
        case 4...: // anything greater than or equal to 4
            print("Too cold")
        default:
            print("Justtttt right")
    }
}

```

Generic subscripts.

```swift

subscript <Keys:Sequence> (keys:Keys) -> [Value] where Keys.Iterator.Element == Key
{
    // ...
}

let nameAndMoons = earthData[["moons", "name"]]
let nameAndMoons2 = earthData[Set(["moons", "name"])]

```

Associated type constraints.

```swift

protocol MyProtocol
{
    associatedtype Element
    associatedtype SubSequence : Sequence where SubSequence.Iterator.Element == Iterator.Element
}

```

Can define a type that conforms to a class as well as a set of protocols.

```swift

class MyClass
{
    var delegate:(View & MyProtocol)?
}

```

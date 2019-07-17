# Enumerations lab

Fork and clone this repo. On your fork, answer and commit the follow questions. When you are finished, submit the link to your repo on Canvas.


## Question 1

a) Define an enumeration called `iOSDeviceType` with member values `iPhone`, `iPad`, `iWatch`. Create a variable called `myDevice` and assign it one member value.

b) Adjust your code above so that `iPhone` and `iPad` have associated values of type String which represents the model number, eg: `iPhone("6 Plus")`. Use a switch case and let syntax to print out the model number of each device.
```swift
enum iOSDeviceType{
case iPhone
case iPad
case iWatch
}
var phone = iOSDeviceType.iPhone

switch phone {
case .iPhone:
print("X plus")
case .iPad:
print("Ipad pro 2019")
case .iWatch:
print("a fancy watch")
}
var myDevice = iOSDeviceType.iPhone
```

## Question 2

a) Write an enum called `Shape` and give it cases for `triangle`, `rectangle`, `square`, `pentagon`, and `hexagon`.

b) Write a method inside `Shape` that returns how many sides the shape has. Create a variable called `myFavoritePolygon` and assign it to one of the shapes above, then print out how many sides it has.

c) Re-write `Shape` so that each case has an associated value of type Int that will represent the length of the sides (assume the shapes are regular polygons so all the sides are the same length) and write a method inside that returns the perimeter of the shape.
```Swift
//a.
enum shape {
case triangle
case rectangle
case square
case pentagon
case hexagon
}

//b.
enum shape {
case triangle
case rectangle
case square
case pentagon
case hexagon

func enumChoice ()-> String{
switch myFavoritePolygon{
case .triangle:
return "Triangle has 3 sides"
default:
return "not my favorite shape"
}
}
}

let myFavoritePolygon = shape.triangle

print(myFavoritePolygon.enumChoice())

//c.
enum shape {
case triangle
case rectangle
case square
case pentagon
case hexagon

func enumChoice ()-> String{
switch myFavoritePolygon{
case .triangle:
return "Triangle has 3 sides"
case .rectangle:
return " Rectangle has 4 Sides"
case .square:
return "Square has 4 Sides"
case .pentagon:
return "Pentagon 5 Sides"
case .hexagon:
return "Hexagon has 6 Sides"
}
}
}

let myFavoritePolygon = shape.hexagon

print(myFavoritePolygon.enumChoice())

```

## Question 3

Write an enum called `OperatingSystem` and give it cases for `windows`, `mac`, and `linux`. Create an array of 10 `OperatingSystem` objects where each one is set to a random operating system. Then, iterate through the array and print out a message depending on the operating system.

```swift
enum OperatingSystem {
case windows
case mac
case linux
}
var arrOfSystem = [OperatingSystem.mac,OperatingSystem.windows,OperatingSystem.linux,OperatingSystem.mac,OperatingSystem.mac,OperatingSystem.windows,OperatingSystem.linux,OperatingSystem.mac,OperatingSystem.windows,OperatingSystem.mac]


for i in arrOfSystem{
switch i{
case .windows:
print("Most used")
case .mac:
print("Apple fans")
case .linux:
print("User control")
}
}
```

## Question 4

You are working on a game in which your character is exploring a grid-like map. You get the original location of the character and the steps he will take.

- A step .up will increase the y coordinate by 1.
- A step .down will decrease the y coordinate by 1.
- A step .right will increase the x coordinate by 1.
- A step .left will decrease the x coordinate by 1.
- Print the final location of the character after all the steps have been taken.

```swift
enum Direction {
    case up
    case down
    case left
    case right
}

var location = (x: 0, y: 0)
var steps: [Direction] = [.up, .up, .left, .down, .left]

// your code here
```
```swift
enum Direction{
case up
case down
case right
case left
}

var location = (x: 0, y: 0)
var steps: [Direction] = [.up, .up, .left, .down, .left]

for i in steps{
switch i{
case .up:
location.1 += 1
case .down:
location.1 -= 1
case .left:
location.0 -= 1
case .right:
location.0 += 1
}
}
print("You're at \(location)")
```


## Question 5

a) Define an enumeration named `HandShape` with three members: `.rock`, `.paper`, `.scissors`.

b) Define an enumeration named `MatchResult` with three members: `.win`, `.draw`, `.lose`.

c) Write a function called `match` that takes two `HandShapes` and returns a `MatchResult`. It should return the outcome for the first player (the one with the first hand shape).

Hint: Rock beats scissors, paper beats rock, scissor beats paper
```swift
enum HandShape{
case rock
case paper
case scissor
}
enum MatchResult{
case win
case lose
case draw
}

func matches(a: HandShape, b: HandShape) -> MatchResult {

switch a{
case .rock:
if  b == .scissor{
return .win
}
else if b == .paper{
return .lose
}
else{
return .draw
}

case .paper:
if b == .rock{
return .win
}
else if b == .scissor{
return .lose
}
else  {
return .draw
}

case .scissor:
if b == .rock{
return .lose
}
else if b == .paper{
return .win

}
else {
return .draw
}
}
}
print(matches(a: .rock, b: .paper))
```

## Question 6

a) You are given a `CoinType` enumeration which describes different coin values. Print the total value of the coins in the array `moneyArray` which contains tuples of type (`quantity`, `CoinType`).

```swift
enum CoinType: Int {
    case penny = 1
    case nickle = 5
    case dime = 10
    case quarter = 25
}

var moneyArray:[(Int,CoinType)] = [(10,.penny),
                                   (15,.nickle),
                                   (3,.quarter),
                                   (20,.penny),
                                   (3,.dime),
                                   (7,.quarter)]

// your code here
```
```swift
var sum = 0
for quantity in moneyArray{
sum += quantity.0 * quantity.1.rawValue
}
print(sum)
```

b) Write a method in the `CoinType` enum that returns an Int representing how many coins of that type you need to have a dollar. Then, create an instance of `CoinType` set to `.nickle` and use your method to print out how many nickels you need to have to make a dollar.
```swift
enum CoinType: Int {
case penny = 1
case nickle = 5
case dime = 10
case quarter = 25

func makeADollar ()-> Int{
switch self{
case .penny:
return 100 / CoinType.penny.rawValue
case .nickle:
return 100 / CoinType.nickle.rawValue
case .dime:
return 100 / CoinType.dime.rawValue
case .quarter:
return 100 / CoinType.quarter.rawValue
}
}
}

var randomCoins = CoinType.nickle
print(randomCoins.makeADollar())
```

## Question 7

a) Write an enum called `DayOfWeek` to represent the days of the week with a raw value of type String.

b) Given the array `poorlyFormattedDays`, write code that will produce an array of enums that match the days.

`let poorlyFormattedDays = ["MONDAY", "wednesday", "Sunday", "monday", "Tuesday", "WEDNESDAY", "thursday", "SATURDAY", "tuesday", "FRIDAy", "Wednesday", "Monday", "Friday", "sunday"]`

c) Write a method in `DayOfWeek` called `isWeekend` that determines whether a day is part of the weekend or not and write code to calculate how many week days appear in `poorlyFormattedDays`.
```swift
//a.
enum DayofWeek: String{
case sunday = "sunday"
case monday = "monday"
case tuesday = "tuesday"
case wednesday = "wednesday"
case thursday = "thursday"
case friday = "friday"
case saturday = "saturday"
}

//b.
//getting weird error not sure why
enum DayofWeek: String, CaseIterable{
case sunday = "sunday"
case monday = "monday"
case tuesday = "tuesday"
case wednesday = "wednesday"
case thursday = "thursday"
case friday = "friday"
case saturday = "saturday"
}

let poorlyFormattedDays = ["MONDAY", "wednesday", "Sunday", "monday", "Tuesday", "WEDNESDAY", "thursday", "SATURDAY", "tuesday", "FRIDAy", "Wednesday", "Monday", "Friday", "sunday"]


var days = DayofWeek.allCases.map{$0}


for i in poorlyFormattedDays{
days.append(DayofWeek(rawValue: i.lowercased())!)
}
print(days)

//c.

//not done some errors
enum DayofWeek: String{
case sunday = "sunday"
case monday = "monday"
case tuesday = "tuesday"
case wednesday = "wednesday"
case thursday = "thursday"
case friday = "friday"
case saturday = "saturday"

func isWeekend()-> Bool{
switch self {
case .sunday:
return true
case .saturday:
return true
default:
return false
}

}
}

let poorlyFormattedDays = ["MONDAY", "wednesday", "Sunday", "monday", "Tuesday", "WEDNESDAY", "thursday", "SATURDAY", "tuesday", "FRIDAy", "Wednesday", "Monday", "Friday", "sunday"]

var counter = 0
for i in poorlyFormattedDays{
if DayofWeek.saturday.isWeekend() == i.lowercased(){
counter += 1
}
}
```

## Question 8

a) Create an enum called `MetroLine` with cases for the colors of the metro train lines. Create an instance of `MetroLine`.

b) Modify your enum so that each case has an associated value of either Character or Int that will represent the train on that line. Create a new instance of `MetroLine` and give it an appropriate train letter or number.


c) Write code that prints the train letter or number of your instance of `MetroLine`.

```swift
//a.
enum MetroLine{
case purple
case red
case orange
case blue
case green

}
var subway = MetroLine.orange

//b.
enum MetroLine{
case purple(Int)
case red (Int)
case orange (Character)
case blue (Character)
case green (Int)

}
var subway = MetroLine.orange("F")
print(subway)

//c.
enum MetroLine{
case purple(Int)
case red (Int)
case orange (Character)
case blue (Character)
case green (Int)

}
var subway = MetroLine.orange("F")

switch subway {
case .purple(7):
print("7")
case .red(1):
print("1")
case .orange("F"):
print("F")
case .blue("A"):
print("A")
case .green(4):
print("4")
default:
print("not train")
}
print(subway)

```


## Question 9

a) Think of your own example of something that can be modeled as an enum and write it. Remember that enums allow you to create instances of a defined list of cases.

b) Add a method to your enum.... try to have the method make sense.

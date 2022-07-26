# ARC
 ARC and Memory Management in Swift

This is training project taken from [ARC and Memory Management in Swift](https://www.raywenderlich.com/966538-arc-and-memory-management-in-swift)

Object's Lifetime: 

* ***Allocation***: Takes memory from a stack or heap.
* ***Initialization***: `init` code runs.
* ***Usage***.
* ***Deinitialization***: `deinit` code runs.
* ***Deallocation***: Returns memory to a stack or heap.

<h2>Reference Cycles</h2>

Problem: objects can't be deallocated

![reference cycle](https://koenig-media.raywenderlich.com/uploads/2016/05/UserIphoneCycle.png)

<h3>Weak References</h3>

Solution: mark property **.owner** of Phone object as **weak**

![weak](https://koenig-media.raywenderlich.com/uploads/2016/05/UserIphoneCycleWeaked.png)

<h3>Unowned References</h3>



![unowned](https://koenig-media.raywenderlich.com/uploads/2016/05/Table.png)

`Contact` can exist without a `Number`, but a `Number` should not exist without a `Contact`.

Parent object should have a strong hold on a child object by convention - not the other way around.
This means that giving `Contact` a strong hold on a `Number`, and `Number` an unowned reference to a `Contact`, is the most convenient solution.

```swift
class Number {
  unowned var contact: Contact
  // Other code...
}
```

```swift
class Contact {
  var number: Number?
  // Other code...
}
```

![example of reference cycle](https://koenig-media.raywenderlich.com/uploads/2016/07/4.png)

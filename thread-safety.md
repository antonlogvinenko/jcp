## Thread safety
A class is thread safe if it **behaves correctly when accessed from multiple threads**, regardless of the scheduling or interleaving of the execution of those threads by the runtime environment, and with no additional synchronization or other coordination on the part of the calling code.

## State issues
Informally, an object's state is its data, stored in state variables such as instance or static fields. An object's state may include fields from other, dependent objects; HashMap's state is partially stored in the HashMap object itself, but also in many Map.Entry objects. An object's state encompasses any data hat can affect its externally visible behavior.

* *Stateless* - thread safe
* Immutable - no problems here
* Effectively immutable
* Mutable - this is a huge problem



## Effectively immutable objects problems:
* Publication safety

## Mutable objects problems:
* Not sharing - no problem here
* Sharing - big problem
* Escape - big problem

## Sharing mutable objects:
* Atomicity
    * Read-modify-write
    * Check-then-act
* Visibility
    * Reordering
    * Stale data
    * Non-atomic 64-bit operations

locks
synchronized block
synchronized method
volatile
thread confinement (ad-hoc, stack-confinement)
make stateless
make immutable
safe publishing
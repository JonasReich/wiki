# Properties
[Wiki](../readme.md)/[Unreal](readme.md)/Smart Pointers

Unreals implementation of smart pointers is modeled after the C++0x standard 
library's shared_ptr as well as Boost smart pointers.

## TSharedPtr<T>

TSharedPtr is a reference counting pointer that destorys the target object once the count has reached 0.
Because UObject are already managed by the GarbageCollector system, TSharedPtr's can't be used in conjunction
with UObjects.
```C++
// Create an empty shared pointer
TSharedPtr<FTreeNode> EmptyNode;

// Create a shared pointer to a new object
TSharedPtr<FTreeNode> Node(new FTreeNode());

// Create a shared pointer from an existing C++ pointer
FTreeNode* RawNodePtr = new FTreeNode();
TSharedPtr<FTreeNode> SharedNodePtr = MakeShareable(RawNodePtr);
```
Shared pointers can be reset using the Reset() method or by assigning null.
```C++
Node.Reset();
Node = null;
```

### Utility Functions
| Function               | Description                                                                 |
|------------------------|-----------------------------------------------------------------------------|
| MakeShareable()        | Create TSharedPtr from raw C++ pointer                                      |
| StaticCastSharedRef()  | Static cast utility function, typically used to downcast to a derived type  |
| ConstCastSharedRef()   | Converts a 'const' reference to 'mutable' smart reference                   |
| DynamicCastSharedRef() | Dynamic cast utility function, typically used to downcast to a derived type |
| StaticCastSharedPtr()  | Static cast utility function, typically used to downcast to a derived type  |
| ConstCastSharedPtr()   | Converts a 'const' smart pointer to 'mutable' smart pointer                 |
| DynamicCastSharedPtr() | Dynamic cast utility function, typically used to downcast to a derived type |

## Thread Safety
Regular shared pointers are only safe to access on a single thread. If you need multiple threads to have access, 
use the thread-safe versions of pointer classes:
* TThreadSafeSharedPtr<T>
* TThreadSafeSharedRef<T>
* TThreadSafeWeakPtr<T>
* TThreadSafeSharedFromThis<> 

These versions are a bit slower due to atomic reference counting, 
and behavior is mostly consistent with regular C++ pointers:
* Reads and copies are always thread-safe.
* Writes/resets must be synchronized to be safe.

## TSharedRef<T>
Non nullable version of SharedPtr. Behave exactly the same in all other regards.
Because of their non nullable property they can't be declared without initialization:
```C++
TSharedRef<UBool> EmptyBool;
```
You can convert shared pointers to references and vice versa.
Remember to check pointers for null before convert them to a reference to avoid a runtime assertion.
```C++
TSharedPtr<FTreeNode> SomeNodePtr = NodeRef;
NodeRef = SomeNodePtr.ToSharedRef();
```
You can derive your own class from *TSharedFromThis* to accquire a TSharedRef directly from an object.

## TWeakPtr<T>
Weak pointers store a weak reference to an object. Unlike a shared pointer, 
a weak pointer will not prevent an object from being destroyed.
Weak pointers are automatically emptied when their object is destroyed no matter who destroyed the object,
which allows you to safely cache pointers to volatile objects.
This also means, weak pointers might become empty when you are not expecting it and weak pointers can 
be used to break reference cycles.

### Initialization
Weak pointers are always created from shared pointers/references, or other weak pointers.
```C++
// Allocate a new tree node.
TSharedRef<FTreeNode> NodeOwner(new FTreeNode());

// Create a weak pointer to the new tree node.
TWeakPtr<FTreenode> NodeObserver(NodeOwner);
```

### Dereferencing and Accessing
To access a weak pointer's object, first promote it to a shared pointer by calling the Pin() method.
```C++
// Get access to the node through the weak pointer.
TSharedPtr<TFreeNode> LockedObserver(NodeObserver.Pin());

// Check that the shared reference was successfully created from the weak reference.
If(LockedObserver.IsValid())
{
    // Object still exists, so it can be accessed.
    LockedObserver->ListChildren();
}
```

## TWeakObjectPtr<T>
TWeakObjectPtr's are pointer wrappers that aren't actual smart pointers like the ones above.
It can be used with any type including UObjects and is meant to be used as a means of conveying
intent of holding only a weak reference to an object.
They have no functual benefit over using raw C++ pointers.

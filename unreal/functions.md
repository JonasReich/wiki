# Functions
[Wiki](../readme.md)/[Unreal](readme.md)/Functions

You can always use pure c++ functions, but UFunctions offer extended functionality

## Function Declaration
```c++
UFUNCTION([specifier, specifier, ...], [meta(key=value, key=value, ...)])
ReturnType FunctionName([Parameter, Parameter, ...]);
```
## Specifiers

[_Function Specifiers in UE4 Docs_](https://docs.unrealengine.com/en-US/Programming/UnrealArchitecture/Reference/Functions/Specifiers)
[_Metadata Specifiers in UE4 Docs_](https://docs.unrealengine.com/en-us/Programming/UnrealArchitecture/Reference/Metadata)

## Delegates

Delegates allow you to call member functions on C++ objects in a generic, yet type-safe way. Using delegates, you can dynamically bind to a member function of an arbitrary object, then call functions on the object, even if the caller does not know the object's type.

It is perfectly safe to copy delegate objects. Delegates can be passed around by value but this is generally not recommended since they do have to allocate memory on the heap. You should always pass delegates by reference when possible.

Both single-cast and multi-cast delegates are supported, as well as "dynamic" delegates which can be safely serialized to disk.

* __single-cast__: One target
* __multi-cast__: Multiple targets
	* __events__: Multicast delegates that are owned (and executed) by one specific class. Analogous to C# events compared to delegates.
* __dynamic__: Only work with UObjects, serializable, can be made assignable from blueprints with 'BlueprintAssignable' Specifier

### Declaration
| Delegate Type                          | Declaration macro                                                       |
|----------------------------------------|-------------------------------------------------------------------------|
| void Function()                        | DECLARE_DELEGATE(DelegateName)                                          |
| void Function(<Param>)                 | DECLARE_DELEGATE_OneParam(DelegateName, ParamType)                      |
| void Function(<Param1>, <Param2>)      | DECLARE_DELEGATE_TwoParams(DelegateName, Param1Type, Param2Type)        |
| void Function(<Param1>, <Param2>, ...) | DECLARE_DELEGATE_<Num>Params(DelegateName, Param1Type, Param2Type, ...) |
| <RetVal> Function(<Params>)            | DECLARE_DELEGATE_RetVal(RetValType, DelegateName, <ParamTypes>)         |

You can replace DELEGATE with another delegate type:
* MULTICAST_DELEGATE
* EVENT
* DYNAMIC_DELEGATE
* DYNAMIC_MULTICAST_DELEGATE

## TODO
Add Timers section
https://docs.unrealengine.com/latest/INT/Programming/UnrealArchitecture/Reference/Functions/index.html

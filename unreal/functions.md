# Functions
[Wiki](../readme.md)/[Unreal](readme.md)/Functions

You can always use pure c++ functions, but UFunctions offer extended functionality

## Function Declaration
```c++
UFUNCTION([specifier, specifier, ...], [meta(key=value, key=value, ...)])
ReturnType FunctionName([Parameter, Parameter, ...]);
```

## Function Parameter Specifiers

Inline keywords that are not part of C++11, but UE4 C++

* `out`

	Declares the parameter as being passed by reference allowing it to be modified by the function.

	`bool myFunc(out int x);` __???__

* `optional`

	Make certain function parameters optional, as a convenience to the caller. The default value of optional arguments can be specified by adding `= [value]`. For example: `function myFunc(optional int x = -1)`. In most cases, the default value for the type of variable, or zero (e.g. 0, false, "", none), is used when no values is passed to an optional parameter.

## Function Specifiers / Meta Properties

* `Exec` _[Specifier]_

	Executable from the Console CLI

* `BlueprintAutocast` _[Meta]_

	Used only by static BlueprintPure functions from BlueprintLibrary. A cast node will be automatically added for the return type and the type of the first parameter of the function. 

### Blueprint/C++ Interaction

* `BlueprintCallable` _[Specifier]_

	This function can be called from Blueprints or C++ and will be exposed to the user of Blueprint editing tools.

* `BlueprintImplementableEvent` _[Specifier]_

	overridden by blueprint event, do not not define!

* `BlueprintNativeEvent` _[Specifier]_

	Same as BlueprintImplementableEvent, but with default C++ implementation, which you'll have to declare as well like so:
	```c++
	UFUNCTION(BlueprintNativeEvent)
	void Function();
	void Function_Imeplementation();
	```
	Don't forget to add a 'Call Parent Function' node in blueprints, if you want the _Implementation function to still be executed when overriden.


* `BlueprintPure` _[Specifier]_

	This function fulfills a contract of producing no side effects, and additionally implies BlueprintCallable. Useful and clean way to implement getters.

* `SealedEvent` _[Specifier]_

	Can't be overriden in subclasses. Only valid for events. Declare other functions as `final` to achieve the same.

#### Restrict call scope

* `BlueprintProtected` _[Meta]_

	This function can only be called on 'this' in a blueprint. It cannot be called on another instance. 

* `DeprecatedFunction` _[Meta]_

	This function is deprecated, any blueprint references to it cause a compilation warning.

* `DeprecationMessage` _[Meta]_

	Used in conjunction with DeprecatedNode or DeprecatedFunction to customize the warning message displayed to the user. 

* `Latent` _[Meta]_

	Indicates that a BlueprintCallable function is Latent

* `LatentInfo` _[Meta]_

	For Latent BlueprintCallable functions indicates which parameter is the LatentInfo parameter

* `NotBlueprintThreadSafe` _[Meta]_

	Only valid in Blueprint Function Libraries. Mark this function as an exception to the class's general BlueprintThreadSafe metadata. 

* `UnsafeDuringActorConstruction` _[Meta]_

	Used by BlueprintCallable functions to indicate that this function is not to be allowed in the Construction Script. 

#### Display

* `AdvancedDisplay` _[Meta]_

	Used with a comma-separated list of parameter names that should show up as advanced pins (requiring UI expansion). Alternatively you can set a number, which is the number of paramaters from the start that should *not* be marked as advanced (eg 'AdvancedDisplay="2"' will mark all but the first two advanced).

* `Category` _[Specifier]_

	Specifies the category of the function when displayed in Blueprint editing tools.
	`Category = "Category Name"`
	`Category = "Category Name|Subcategory Name"`

* `CompactNodeTitle` _[Meta]_

	Indicates that a BlueprintCallable function should display in the compact display mode and the name to use in that mode.
	```c++
	UFUNCTION(BlueprintCallable, CompactNodeTitle = "Short Name")
	void OverlyLongFunctionNameThatDoesntFitOnANode(args);
	```

* `DisplayName` _[Meta]_

	The name to display for this class, property, or function instead of auto-generating it from the name.

* `HidePin` _[Meta]_

	For BlueprintCallable functions indicates that the parameter pin should be hidden from the user's view.

* `Keywords` _[Meta]_
	For BlueprintCallable functions provides additional keywords to be associated with the function for search purposes.

### Networking
* `BlueprintAuthorityOnly` _[Specifier]_

	This function will not execute from Blueprint code if running on something without network authority.

* `BlueprintCosmetic` _[Specifier]_

	This function is cosmetic-only and will not run on dedicated servers.

* `Client` _[Specifier]_

	Replicated and executed across clients. Provide implementation in _Implementation function, just as with BlueprintNativeEvents

* `NetMulticast` _[Specifier]_

	This function is both executed locally on the server and replicated to all clients, regardless of the Actor's NetOwner.

* `Reliable` _[Specifier]_

	Replication of calls to this function should be done on a reliable channel. Only valid when used in conjunction with Client or Server

* `Server` _[Specifier]_

	Replicated and executed across servers. Provide implementation in _Implementation function, just as with BlueprintNativeEvents

* `Unreliable` _[Specifier]_

	Replication of calls to this function can be done on an unreliable channel. Only valid when used in conjunction with Client or Server

### Specify Function Parameters

* `WorldContext` _[Meta]_

	Used by BlueprintCallable functions to indicate which parameter is used to determine the World that the operation is occurring within. 

	* `CallableWithoutWorldContext` _[Meta]_

		Used for BlueprintCallable functions that have a WorldContext pin to indicate that the function can be called even if the class does not implement the virtual function GetWorld(). 
* ~~`DefaultToSelf`~~ _[Meta]_ _(not reccommended)_

	Sets the default value of the Blueprint input pin to 'self.'
	Note: The pin set to DefaultToSelf doesn't appear to actually say "self," like Target does, making it difficult to know the pin has this property set


### ???

* `ArrayParm`
* `ArrayTypeDependentParams` _[Meta]_
* `AutoCreateRefTerm` _[Meta]_
* `BlueprintInternalUseOnly` _[Meta]_
* `CommutativeAssociativeBinaryOperator` _[Meta]_
* `CustomStructureParam` _[Meta]_
* `CustomThunk` _[Specifier]_
* `ExpandEnumAsExecs` _[Meta]_
* `HideSpawnParms` _[Meta]_
* `MaterialParameterCollectionFunction` _[Meta]_
* `NativeBreakFunc` _[Meta]_
* `NativeMakeFunc` _[Meta]_
* `ServiceRequest` _[Specifier]_
* `ServiceResponse` _[Specifier]_
* `WithValidation` _[Specifier]_

## TODO
Add Delegates and Timers section
https://docs.unrealengine.com/latest/INT/Programming/UnrealArchitecture/Reference/Functions/index.html

# Unreal Engine 4
[Wiki](../index.md)/Unreal

Link collection, which has to be turned into proper wiki entrys:

## Visual Studio Setup
* [Unreal VS Extension](https://docs.unrealengine.com/latest/INT/Programming/Development/VisualStudioSetup/UnrealVS/)
* [Visual Studio Setup](https://docs.unrealengine.com/latest/INT/Programming/Development/VisualStudioSetup/)

## [Source Control](source-control.md)

## Workflow
* Creating new source code files
* Compiling/Building/Packaging
* Plugin Creation
* Debugging

## [Coding Standard](coding-standard.md)

## General/Introductory Articels
* [Introduction to C++ Programming in UE4](https://docs.unrealengine.com/latest/INT/Programming/Introduction/index.html)
* [Unreal Engine 4 For Unity Developers](https://docs.unrealengine.com/latest/INT/GettingStarted/FromUnity/)

## Helper Functions

### Logging

#### Quick Usage
You can always use the LogTemp for quick usage. However a custom log category is reccommended to keep everything clean and sorted.
```UE_LOG(LogTemp, Warning, TEXT("Your message"));```

#### Defining A Custom Log Category

```C++
// LogCustom.h
DECLARE_LOG_CATEGORY_EXTERN(LogCustom, Log, All);
```
```C++
// LogCustom.cpp
DEFINE_LOG_CATEGORY(LogCustom);
```
You can then use the newly created custom log like this:
```C++
UE_LOG(LogCustom, Log, TEXT("Log message text"));
```
If the name of your log category is very long, a macro like this might be handy:
```C++
#define YOUR_LOG(Type, Message, ...) UE_LOG(LogCustom, Type, Message, ##__VA_ARGS__);
```
which then allows you to log like you would with the ```UE_LOG```
```C++
YOUR_LOG(Warning, TEXT("XY accessed before initialization"));
YOUR_LOG(Log, TEXT("Number of items: %s"), i)
```
#### On Screen Logging
```C++
GEngine->AddOnScreenDebugMessage(-1, 5.f, FColor::Red, TEXT("This is an on screen message!"));
```

#### Log Macros
[Unreal Wiki](https://wiki.unrealengine.com/Log_Macro_with_Netmode_and_Colour)



## Important Unreal Classes
* Gameplay Framework
	* Gamemode
	* Player Controller
	* Actor
	* Pawn
* Data types
	* int32, etc.
	* FString vs FText vs FName
	* [String Conversion](https://wiki.unrealengine.com/String_Conversions:_FString_to_FName,_FString_to_Int32,_Float_to_FString)
* Collections (TArray, TMap, etc.)

## Unreal C++
* C++/Blueprint Interaction 
* [Unreal Interfaces](https://wiki.unrealengine.com/Interfaces_in_C%2B%2B)
* [UFUNCTION](https://wiki.unrealengine.com/UFUNCTION)
* [UPROPERTY](https://wiki.unrealengine.com/UPROPERTY)
* Unreal Header Tool
* Automatically generated source code -> X.generated.h & GENERATED_BODY()
* TSubclassOf<T>
* Type-Casting
* Constructors

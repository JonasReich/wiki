# Logging
[Wiki](../index.md)/[Unreal](unreal.md)/Logging

## Quick Usage
You can always use the LogTemp for quick usage. However a custom log category is reccommended to keep everything clean and sorted.
```UE_LOG(LogTemp, Warning, TEXT("Your message"));```

## Defining A Custom Log Category

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
## On Screen Logging
```C++
GEngine->AddOnScreenDebugMessage(-1, 5.f, FColor::Red, TEXT("This is an on screen message!"));
```

## Log Macros
[Unreal Wiki](https://wiki.unrealengine.com/Log_Macro_with_Netmode_and_Colour)

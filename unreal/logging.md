# Logging
[Wiki](../readme.md)/[Unreal](readme.md)/Logging

## Quick Usage
The UE_LOG macro recieves the following parameters:
1. Log Category: You can always use the LogTemp category for temporary usage. However a custom log category should be created when you want to leave the logs in the code.
2. Log Level: [Log, Display, Verbose, VeryVerbose, Warning, Error]
3. Message + Params: ``TEXT("Chracter '%s' current health: %d"), *Character.GetName(), Character.HealthPoints``

```c++
UE_LOG(LogTemp, Warning, TEXT("Your message"));
```

## Defining a Custom Log Category

### Extern
This type is usable in multiple header and source files as long as they include ``LogCustom.h``.

```c++
// *.h
DECLARE_LOG_CATEGORY_EXTERN(LogCustom, Log, All);
```

```c++
// *.cpp
DEFINE_LOG_CATEGORY(LogCustom);
```

### Class
This type is usable only inside member functions of the class it's declared in.

```c++
// *.h
class Foo
{
	DECLARE_LOG_CATEGORY_CLASS(LogCustom, Log, All);
	// ...
};
```

```c++
// *.cpp
DEFINE_LOG_CATEGORY(LogCustom);
```

### Static
This type is only usable in a single source file.

```c++
// *.cpp
DEFINE_LOG_CATEGORY_STATIC(LogCustom, Log, All);
```

## Using a Custom Log Category

You can then use the newly created custom log like this:
```c++
UE_LOG(LogCustom, Log, TEXT("Log message text"));
```

## On Screen Logging
```c++
GEngine->AddOnScreenDebugMessage(-1, 5.f, FColor::Red, TEXT("This is an on screen message!"));
```

# Unreal Coding Standard
[Wiki](../index.md)/[Unreal](unreal.md)/Coding Standard

Most of the rules defined in Unreal's coding standard are pretty self explanatory and widely used anyways.
This page lists only the more specific/obscure rules. You can find a complete version [_here_](https://docs.unrealengine.com/latest/INT/Programming/Development/CodingStandard/#comments).

## Naming conventions
* PascalCase for everything - event member variables
* Typename prefixes

  |Type              | Prefix | Example       |
  |------------------|--------|---------------|
  |Template          | T      | TArray\<T>    |
  |UObject           | U      | UMyObject     |
  |AActor            | A      | AMyCharacter  |
  |SWdiget           | S      | SMyWidget     |
  |Interfaces        | I      | IInteractable |
  |Enums             | E      | EBuildingType |
  |Boolean Variables | b      | bIsActive     |
  |Other             | F      | FMath         |
  
* Prefix out parameters with 'Out', e.g. ```int32 DoSomeCalculation(int32 InputA, int23 InputB, bool bOutWasSuccessful);```

## C++ Types
* Size of default int is platform specific, therefore use explicitly sized variants, e.g. ```int32```. There are unsigned variants as well, e.g. ```uint32```
* Always use ```nullptr``` instead of ```NULL``` macro
* Avoid using ```auto``` unless it's necessary (e.g. lambda types)
* Enum classes should always be used in favor of namespaced enums

## Comments
Function comments should follow this style, especially in the case of BlueprintCallable Ufunctions, because only then they are incorporated into the corresponding Blueprint nodes by UHT.
{% highlight c++ %}
/**
 * Single line function description
 * @param FirstParameter - Single line parameter description
 * @param SecondParameter - Description #2
 * @return Description of return value
 */
float DoSomething(float& FirstParameter, float& SecondParameter);
{% endhighlight %}

## General
* Always place all braces. This means no if without curly braces.
* Always place curly braces on new lines (Exception: one line lambdas, empty function definitions)
* Pointers/references always use this style ```UObject* Object```. Neither ~~```UObject * Object```~~, nor ~~```UObject *Object```~~. This makes searching  for them a lot easier.

# Logging
[Wiki](../index.md)/[Unreal](unreal.md)/Logging

## Quick Usage
You can always use the LogTemp for quick usage. However a custom log category is reccommended to keep everything clean and sorted.

{% highlight c++ %}
UE_LOG(LogTemp, Warning, TEXT("Your message"));
{% endhighlight %}

## Defining A Custom Log Category

{% highlight c++ %}
// LogCustom.h
DECLARE_LOG_CATEGORY_EXTERN(LogCustom, Log, All);
{% endhighlight %}

{% highlight c++ %}
// LogCustom.cpp
DEFINE_LOG_CATEGORY(LogCustom);
{% endhighlight %}

You can then use the newly created custom log like this:
{% highlight c++ %}
UE_LOG(LogCustom, Log, TEXT("Log message text"));
{% endhighlight %}

If the name of your log category is very long, a macro like this might be handy:
{% highlight c++ %}
#define YOUR_LOG(Type, Message, ...) UE_LOG(LogCustom, Type, Message, ##__VA_ARGS__);
{% endhighlight %}

which then allows you to log like you would with the ```UE_LOG```
{% highlight c++ %}
YOUR_LOG(Warning, TEXT("XY accessed before initialization"));
YOUR_LOG(Log, TEXT("Number of items: %s"), i)
{% endhighlight %}

## On Screen Logging
{% highlight c++ %}
GEngine->AddOnScreenDebugMessage(-1, 5.f, FColor::Red, TEXT("This is an on screen message!"));
{% endhighlight %}

## Log Macros
[_Unreal Wiki_](https://wiki.unrealengine.com/Log_Macro_with_Netmode_and_Colour)

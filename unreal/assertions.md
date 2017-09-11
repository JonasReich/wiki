# Assertions
[Wiki](../readme.md)/[Unreal](readme.md)/Assertions

Source: ```/UE4/Engine/Source/Runtime/Core/Public/Misc/AssertionMacros.h```

__```checkCode(expression);```__

_???_

__```checkNoEntry();```__

* Mark code that should never execute

__```checkNoReentry();```__ / __```checkNoRecursion();```__

* Function must not be called recursively

__```unimplemented();```__

* Mark virtual function as not implemented/not callable on specific class

| macro | executes if ```DO_CHECK = 0``` | ```DO_GUARD_SLOW``` | print message | context info  | print callstack |
|---------------------------------------------|---|---|---|---|---|
| ```check(expression);```                    |   |   |   |   |   |
| ```verify(expression);```                   | X |   |   |   |   |
| ```checkf(expression, ...);```              |   |   | X | X |   |
| ```verifyf(expression, ...);```             | X |   | X | X |   |
| ```checkSlow();```                          |   | X |   |   |   |
| ```checkfSlow();```                         |   | X | X | X |   |
| ```verifySlow();```                         | X | X |   |   |   |
| ```ensure(expression);```                   |   |   |   |   | X |
| ```ensureMsg(expression, message);```       |   |   | X |   | X |
| ```ensureMsgf(expression, message, ...);``` |   |   | X | X | X |

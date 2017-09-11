# Assertions
[Wiki](../readme.md)/[Unreal](readme.md)/Assertions

Source: ```/UE4/Engine/Source/Runtime/Core/Public/Misc/AssertionMacros.h```

__checkCode(expression);__

_???_

__checkNoEntry();__

* Mark code that should never execute

__checkNoReentry();__ / __checkNoRecursion();__

* Function must not be called recursively

__unimplemented();__

* Mark virtual function as not implemented/not callable on specific class


| macro                                 | ~~DO_CHECK~~ | DO_CHECK | ~~DO_GUARD_SLOW~~ | DO_GUARD_SLOW | print message | context info  | print callstack |
|---------------------------------------|--------------|----------|-------------------|---------------|---------------|---------------|-----------------|
| check(expression);                    |              | halt     |                   |               |               |               |                 |
| verify(expression);                   | execute      | halt     |                   |               |               |               |                 |
| checkf(expression, ...);              |              | halt     |                   |               | X             | X             |                 |
| verifyf(expression, ...);             | execute      | halt     |                   |               | X             | X             |                 |
| checkSlow()                           |              | halt     |                   | X             |               |               |                 |
| checkfSlow()                          |              | halt     |                   | X             | X             | X             |                 |
| verifySlow()                          | execute      | halt     |                   | X             |               |               |                 |
| ensure(expression)                    |              | ?        |                   |               |               |               | X               |
| ensureMsg(expression, message);       |              | ?        |                   |               | X             |               | X               |
| ensureMsgf(expression, message, ...); |              | ?        |                   |               | X             | X             | X               |

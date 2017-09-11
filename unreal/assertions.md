# Assertions
[Wiki](../readme.md)/[Unreal](readme.md)/Assertions

Source: ```/UE4/Engine/Source/Runtime/Core/Public/Misc/AssertionMacros.h```

checkCode(expression);

// ???

checkNoEntry();

* Mark code that should never execute

checkNoReentry(); = checkNoRecursion();

* Function must not be called recursively

unimplemented();

* Mark virtual function as not implemented/not callable on specific class


| macro                                 | DO_CHECK = 0      | DO_CHECK = 1 | DO_GUARD_SLOW = 0 | DO_GUARD_SLOW = 1 | print message | print message + context info | print callstack |
|---------------------------------------|-------------------|--------------|-------------------|-------------------|---------------|------------------------------|-----------------|
| check(expression);                    |                   | halt         |                   |                   |               |                              |                 |
| verify(expression);                   | execute assertion | halt         |                   |                   |               |                              |                 |
| checkf(expression, ...);              |                   | halt         |                   |                   | [x]           | [x]                          |                 |
| verifyf(expression, ...);             | execute assertion | halt         |                   |                   | [x]           | [x]                          |                 |
| checkSlow()                           |                   | halt         |                   | [x]               |               |                              |                 |
| checkfSlow()                          |                   | halt         |                   | [x]               | [x]           | [x]                          |                 |
| verifySlow()                          | execute assertion | halt         |                   | [x]               |               |                              |                 |
| ensure(expression)                    |                   | ?            |                   |                   |               |                              | [x]             |
| ensureMsg(expression, message);       |                   | ?            |                   |                   | [x]           |                              | [x]             |
| ensureMsgf(expression, message, ...); |                   | ?            |                   |                   | [x]           | [x]                          | [x]             |

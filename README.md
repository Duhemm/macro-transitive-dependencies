# Example project

This project shows a complex dependency graph :

Client => __Provider__ -> Relay4 => Relay3 -> Relay2 => Relay1 -> Helper

 * __A__ means that A is a macro provider
 * A -> B means that A depends internally on B (A and B are in the same project)
 * A => B means that A depends externally on B (A and B are in disting projects)

The macro defined by `Provider.scala` simply returns the return value of `Relay4.relay4` (which returns the return value of `Relay3.relay3`, which returns the return value of `Relay2.relay2`, which returns the return value of `Relay1.relay1`, which returns the return value of `Helper.foo`).

Changing the return value of `Helper.foo` should trigger the recompilation of `Client.scala`.

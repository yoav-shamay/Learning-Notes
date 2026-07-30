## Engines
### LCG

### mt19937
Can recover from 624 consecutive 32-bit output.
Recovering state for getting future/past outputs from 32 bit outputs:
[ExtendedRandChttps://pypi.org/project/extendedrandcrack/](https://pypi.org/project/extendedrandcrack/) - can recover for any 624 and has rewind
https://github.com/twisteroidambassador/mt19937-reversible
has time travel (`rewind`), works with any 624 consecutive outputs
https://github.com/icemonster/symbolic_mersenne_cracker/tree/main
allows to recover from partial inputs.
#### Math Properties
- Linear mod 2 (untested)
#### Technical details
The `mt19937` state is made out of 624 numbers.
The state is cyclic mod 624.
Each time it's at some index at this state, does some computation based on the current state to assign a new value.
Then it moves to the next index
It returns the output of `temper(new_val)`, where `temper` is easily reversible.
This means the state can be easily recreated by the output of `untemper(out1), untemper(out2), ..., untemper(out624)`.
### SplitMix
Can recover seed and gamma from 2 consecutive outputs.
All details are described in this paper: https://gee.cs.oswego.edu/dl/papers/oopsla14.pdf), including how to recover state.
## Common Libraries
### Python `random` module
Is [[#mt19937]].
Note that 128 bit output is equivalent for 4 32 bit outputs (the first one being the least significant bits).
In case of a partial one, like `getrandbits(8)`, it will take the 8 most significant bits.
Note that seeding from `seed` is different from https://en.wikipedia.org/wiki/Mersenne_Twister#Initialization
### Haskell `System.Random`
Is [[#SplitMix]].
Bounded rand Haskell implementation from seed and gamma: https://web.archive.org/web/20200520071940/https://www.pcg-random.org/posts/bounded-rands.html
### Glibc `rand()`
See [[glibc random prediction and breaking]]
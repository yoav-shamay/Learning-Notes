Shown as `__gmpz_smth`.
Mapping to function name is simple - `__gmpz_name` is simply `mpz_name` in docs.
Manual is in https://gmplib.org/manual/
The gmpz parameter is a pointer and is passed by reference.
## mpz_t type
MIGHT BE PREDEFINED IN IDA.
Note that internally it's an array of one element, which practically mean that functions receive a pointer to it, but it's still allocated in the stack.

```c
typedef struct
{
  int _mp_alloc;
  int _mp_size;
  unsigned long int *_mp_d;
} __mpz_struct;

typedef __mpz_struct mpz_t[1];
```
### `_mp_size` Field
The number of limbs, which is the length of `mp_d`, but minus it if the number is negative.
`_mp_size` field is relative to zero as the number is, which means:
- positive if the value is positive
- zero if the value is zero
- negative if the value is negative
### `mp_d` field
An array of "limbs". basically value in base `2^64` little-endian.
This means that `mp_d[0]` is the first `2^64` bits.
Note that `mpz` doesn't use 2's complement but instead negative numbers are represented with negative `_mp_size`.
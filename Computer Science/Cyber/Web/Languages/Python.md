## Default Parameters
Default parameters are evaluated once and then passed by reference.
This means that if a default parameter is a secret value, getting it once means getting it in all calls.
It also means that if it's mutable, then modifying in one call means that it will be modified forever.
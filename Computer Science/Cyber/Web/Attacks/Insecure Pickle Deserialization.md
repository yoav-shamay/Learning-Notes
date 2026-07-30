When called `pickle.loads` on user input. Can lead to RCE.
Called Pickle Bomb.
## Creating a Pickle Bomb
as pickle doesn't normally serialize function definitions it's difficult to actually generate a pickle bomb.
The idea is that pickle uses object `__reduce__` to get the callable method and parameters to reconstruct the object. - tuple of `(method, params)`.
So you pickle an object with reduce of `(eval, ("code',))`, and use it as the payload.
In python2, make sure the class inherits `object`.
TODO code example.
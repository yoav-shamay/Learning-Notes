## Debugging
Do this:
https://stackoverflow.com/questions/61003292/debugging-javascript-in-vs-code-console
Use `launch.json` inside `.vscode` folder
Create it if it doesn't exist.
Press `F5` to run.
## Proxy
Can be used to intercept access of object at a specific position
```js
const handler = {
  get(target, prop, receiver)
  {
    if (prop == 1684)
    {
      console.log("1684 access");
    }
    else if (prop == 1)
    {
      console.log("1 access");
    }
    return Reflect.get(target, prop, receiver);
  }
}
//let current_object = {};
let current_object = new Proxy({}, handler);
```
## Tips
- Use `console.trace("msg")` to log stack trace.
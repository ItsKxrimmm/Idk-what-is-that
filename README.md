you aim randomly but shoot the target with the same xray logic
```js
//by Kxrimmm
const base = Module.findBaseAddress("libg.so");
const addInput = new NativeFunction(base.add(0x5EC798), "pointer", ["pointer", "pointer"]);

Interceptor.attach(addInput, {
  onEnter: args => [20, 21].forEach(i => args[1].add(i).writeU8(1)) || args[1].add(16).writeInt(1000001)
});```

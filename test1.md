``` javascript
let info = { name: "fzb" };

const weakRef = new WeakRef(info);

const finalizationRegistry = new FinalizationRegistry(() => {
  console.log("对象已经被销毁");
});
finalizationRegistry.register(info);
info = null;

console.log(weakRef.deref()?.name);
setTimeout(() => {
  console.log(weakRef.deref()?.name);
}, 10000);
```
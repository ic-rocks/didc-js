# didc-js

A JS/Wasm package for generating Candid bindings.

## Building

```shell
cargo install wasm-pack
wasm-pack build --target bundler
wasm-opt --strip-debug -Oz pkg/didc_bg.wasm -o pkg/didc_bg.wasm
```

## Usage

```js
const didc = import("pkg/didc_js");

didc.then((mod) => {
  const service = `service : {
    add : (int32, int32) -> (int32) query;
  }`;
  const bindings = mod.generate(service); // Bindings { js: "...", ts: "...", motoko: "..." }
});
```

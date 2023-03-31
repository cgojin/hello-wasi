# running-wasm-by-wasmtime

Running wasm/wasi by wasmtime.

## Build and Run native app.

```sh
cargo build
target/debug/hello
    Hello, world!
```

## Build and Run wasm/wasi app

```sh
# add wasm32-wasi target, first only
rustup target add wasm32-wasi

# install wasmtime, first only
curl https://wasmtime.dev/install.sh -sSf | bash
# or install cargo-wasi, first only
cargo install cargo-wasi

# build .wasm
cargo build --target wasm32-wasi

# run .wasm
wasmtime target/wasm32-wasi/debug/hello.wasm
    Hello, world!

# build & run .wasm
cargo wasi run
    Hello, world!

# install wasm-tools, first only
cargo install wasm-tools

# show export methods
wasm-tools print target/wasm32-wasi/debug/hello.wasm | grep "(export" 
  (export "memory" (memory 0))
  (export "_start" (func $_start))
  (export "__main_void" (func $__main_void))
```

## References

- [wasmtime](https://github.com/bytecodealliance/wasmtime)

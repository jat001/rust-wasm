# rust-wasm

## Debugging

0. Install [`wasm-bindgen-cli`](https://github.com/rustwasm/wasm-bindgen?tab=readme-ov-file#install-wasm-bindgen-cli) and [C/C++ DevTools Support (DWARF)](https://chromewebstore.google.com/detail/cc++-devtools-support-dwa/pdcpmagijalfljmkmjngeonclgbbannb)

1. Build

   ```shell
   cargo build --target wasm32-unknown-unknown
   wasm-bindgen --keep-debug --web --out-dir pkg target/wasm32-unknown-unknown/debug/rust_wasm.wasm
   ```

   `wasm-pack` is not used because it does not support `--keep-debug` option. See [rustwasm/wasm-pack#1351](https://github.com/rustwasm/wasm-pack/issues/1351).

2. Serve

   ```shell
   python3 -m http.server
   ```

   Or use any other http server you like.

3. Open `http://localhost:8000`

4. Open Chrome DevTools and go to **Sources** tab.

   You should see `top` -> `file://` -> `${workspaceFolder}/src` -> `lib.rs` under **Page** pane.

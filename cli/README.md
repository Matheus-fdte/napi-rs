# `@napi-rs/cli`

> Cli tools for napi-rs

## Commands

### Debug mode

```bash
DEBUG="napi:*" napi [command]
```

### `napi build`

> Build command. Build rust codes and copy the dynamic lib binary file to the dist dir.

#### `--platform`

> default `false`

Append `platform-arch-[abi]` name to dist file. eg: `index.darwin-x64.node`.

#### `--release`

> default `false`

Is release build. This flag will be passed to `Cargo` directly.

#### `--features`

> default `''`

Cargo features, passthrough to `cargo build` command.

#### `--config,-c`

> default `package.json`

`napi-rs` config file name. `napi-rs` config example :

```js
{
  "name": "@native-binding/fib",
  "version": "0.1.0",
  "napi": {
    "name": "fib", // binary name
    "triples": {
      "defaults": true, // default true, if this value is true, will build `x86_64-pc-windows-msvc`, `x86_64-apple-darwin` and `x86_64-unknown-linux-gnu`
      "addition": [
        "x86_64-unknown-linux-musl",
        "x86_64-unknown-freebsd",
        "aarch64-unknown-linux-gnu"
      ]
    }
  }
}
```

#### `--cargo-name`

> default `undefined`

If not set, cli will read the `package.name` field in `Cargo.toml` under `process.cwd()`. The `-` in the name will be replaced with `_`.

#### `--target`

> default `undefined`

This value will be passed to `Cargo build` command directly. eg: `napi build --target x86_64-unknown-linux-musl`

#### `--cargo-flags`

> default `undefined`

Other flags you want pass to `Cargo build`.

### `napi artifacts`

> Copy artifact files in Github actions.

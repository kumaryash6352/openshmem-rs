# OpenSHMEM-rs 

Rust bindings for the OpenSHMEM 1.5 (and soon 1.6) communication API.

Quick start:

```rust
let ctx = ShmemCtx::init()?;
let my_pe = ctx.my_pe().raw();
let npes = ctx.n_pes();
println!("Hello from PE {my_pe}!");
```

# Examples

See [./examples/](./examples/) for example programs.

# Building

This library depends on `openshmem-sys`. Building the sys crate
requires the environment variable `SHMEM_INSTALL_DIR` to point to
a directory containing your OpenSHMEM installation. Your
`SHMEM_INSTALL_DIR` should contain a `lib/` and a
`include/`. For example, this is the output of `tree` on the
`SHMEM_INSTALL_DIR` for Sandia OpenSHMEM.

```.bash
├── ...
├── include/
│   ├── mpp/
│   ├── shmem-def.h
│   ├── shmem.fh
│   ├── shmem.h
│   ├── shmemx-def.h
│   ├── shmemx.fh
│   └── shmemx.h
├── lib/
│   ├── libsma.0.dylib
│   ├── libsma.a
│   └── ...
└── ...
```

We currently test with Sandia OpenSHMEM as the underlying OpenSHMEM
implementation.

## Developing

If you want rust-analyzer to function correctly, you'll need to pass
`SHMEM_INSTALL_DIR` to rust-analyzer.

### VSCode

Add this to your user settings JSON.
```json
  ...
  "rust-analyzer.server.extraEnv": { "SHMEM_INSTALL_DIR": "~/my-shmem-install-dir" },
  ...
```

### Emacs (lsp-mode)

Add this to your configuration.

```elisp
(setq lsp-rust-analyzer-cargo-extra-env ["SHMEM_INSTALL_DIR", "~/my-shmem-install-dir"])
```

# Prior Work

Rebecca Hassett and Tony Curtis at Stony Brook University created the
RustySHMEM project, which this library draws heavy inspiration from.
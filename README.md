# RollMRC Binary Package

This package contains a prebuilt Linux x86_64 RollMRC executable and the
shared libraries required to run it. You do not need to install OpenCV on the
target machine; use `run.sh` to load the bundled `.so` files automatically.

## Package Layout

```text
.
├── rollmrc          # RollMRC executable
├── run.sh           # launcher; sets LD_LIBRARY_PATH to ./lib
├── lib/             # bundled shared libraries
├── scripts/example  # example checking script
└── data/            # example layout files
```

## Quick Start

Run from the package root:

```bash
chmod +x run.sh rollmrc
./run.sh scripts/example
```

The program prints check timing and violation counts to the terminal.

## Script Commands

Supported input formats: `png`, `poly`.

```text
load <layout_path>
set space <value>
set width <value>
set bend <value>
set min_area <value>
set sample_step <value>
check [space|width|bend|minarea|all] [threads]
```

Units:

- `space`, `width`, `bend`: nm
- `min_area`: square nm
- `sample_step`: positive sampling step
- `threads`: optional positive integer

Example:

```text
set sample_step 20
load data/post_opc_alu_M1.poly
set space 50
set width 50
set bend 10
set min_area 10000
check minarea
```

## Notes

- Always run the package through `./run.sh` unless you manually set
  `LD_LIBRARY_PATH=./lib`.
- This binary package is intended for Linux x86_64 systems with a compatible
  glibc version.
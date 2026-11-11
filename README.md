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
└── data/            # the 22 layouts used in the paper
```

## Quick Start

Run from the package root:

```bash
chmod +x run.sh rollmrc
./run.sh scripts/example
```

The script path may be given with or without `-s`, and an explicit thread count
can be passed on the command line:

```bash
./run.sh -s scripts/example
./run.sh -t 8 scripts/example
```

The program prints check timing and violation counts to the terminal. Running
`./run.sh` with no arguments starts the interactive shell.

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

Contours are used as supplied: no Douglas--Peucker simplification is applied at
any `sample_step`. The step only controls the uniform densification of the input
contours before the rolling-ball queries. Older scripts that still contain
`set simplify ...` or `set simplify_eps ...` remain runnable; those settings are
accepted and ignored.

Example:

```text
set sample_step 16
load data/post_opc_alu_M1.poly
set space 50
set width 50
set bend 20
set min_area 10000
check all
```

## Example Layouts

`data/` contains the 22 layouts used in the paper. The `post_opc_{alu,gcd,arbiter}_M{1..4}.poly`
files are the Calibre pxOPC masks for the 45 nm ALU, GCD, and Arbiter circuits;
`CurvILT_mask{1..10}.poly` are the post-ILT masks from the ICCAD 2013 benchmarks.
All shipped layouts are vector `.poly` files. Coordinates in the Calibre masks
are on a 0.1 nm grid, and the CurvILT masks on a 1 nm grid. `scripts/example`
runs all four rules on one ALU layout.

## Notes

- Always run the package through `./run.sh` unless you manually set
  `LD_LIBRARY_PATH=./lib`.
- This binary package is intended for Linux x86_64 systems with a compatible
  glibc version.
- The bundled binary is built for the x86-64-v2 baseline, so it runs on any
  x86-64 CPU made in the last decade rather than only on the build machine.

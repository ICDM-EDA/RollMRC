# Third-Party Components

The `lib/` directory contains unmodified shared libraries from upstream
projects. They are shipped only so that `rollmrc` runs without installing
OpenCV on the target machine. Each library remains under its own license.

| Component | Files | License | Upstream |
| --- | --- | --- | --- |
| OpenCV 4.14 | `libopencv_*.so.414` | Apache License 2.0 | https://github.com/opencv/opencv |
| libjpeg-turbo | `libjpeg.so.62` | IJG / BSD-3-Clause | https://github.com/libjpeg-turbo/libjpeg-turbo |
| libpng | `libpng16.so.16` | libpng License | http://www.libpng.org/pub/png/libpng.html |
| libtiff | `libtiff.so.5` | libtiff License (BSD-like) | http://www.libtiff.org |
| JBIG-KIT | `libjbig.so.2.1` | GPL-2.0 | https://www.cl.uni-hamburg.de/~mgk25/jbigkit/ |
| libwebp | `libwebp.so.7`, `libwebpdemux.so.2`, `libwebpmux.so.3` | BSD-3-Clause | https://chromium.googlesource.com/webm/libwebp |
| zlib | `libz.so.1` | zlib License | https://zlib.net |
| GCC runtime | `libstdc++.so.6`, `libgcc_s.so.1`, `libgomp.so.1` | GPL-3.0 with GCC Runtime Library Exception | https://gcc.gnu.org |
| GNU C Library | `libm.so.6`, `libpthread.so.0`, `libdl.so.2` | LGPL-2.1-or-later | https://www.gnu.org/software/libc/ |

The source code for each component is available at the upstream address
listed above. License texts accompany the corresponding upstream releases.

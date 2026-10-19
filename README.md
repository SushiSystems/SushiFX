# SushiFX

A fork of the AMD FidelityFX SDK that keeps its Vulkan backend alive, for engines that want FSR 3.1 upscaling and frame interpolation on Vulkan.

Everything else in the tree (the DirectX 12 backend, the samples, the Cauldron framework) is AMD's code as published. It is not maintained here.

## What you get

| You take | From |
| --- | --- |
| `amd_fidelityfx_vk.dll`, built from source | `ffx-api/bin/`, after the build below |
| The five-function C API (`ffxCreateContext`, `ffxDestroyContext`, `ffxDispatch`, `ffxQuery`, `ffxConfigure`) | `ffx-api/include/ffx_api/`, described in [ffx-api.md](docs/getting-started/ffx-api.md) |

Do not use `PrebuiltSignedDLL/amd_fidelityfx_vk.dll`. It is AMD's signed binary, unchanged, and it
carries the descriptor pool defect below.

## Build

Needs Windows, the Vulkan SDK, CMake and Ninja. A clone cannot rebuild the shader compiler until
the ignored binaries under `sdk/tools/ffx_shader_compiler/libs` are fetched from AMD's release.

```
cmake -S ffx-api -B build/api -G Ninja -DCMAKE_BUILD_TYPE=Release -DFFX_API_BACKEND=VK_X64
cmake --build build/api
```

The repository has no test suite and no project CLI yet.

## Why it exists

AMD's FSR SDK moved to a v2 line that is DirectX 12 only. Its readme lists "Vulkan is currently
not supported in SDK" among the known issues. The Vulkan backend survives only in the 1.1.x line,
whose last release is v1.1.4 (May 2025). This fork starts from that tag, upstream commit
`c6efa6bf7f2027b3ec94f28578bb5965eabb9e55`, imported unchanged as `e5005fe`. `git diff e5005fe`
lists everything the fork changes.

The import leaves out the 49 files `.gitignore` excludes: the binaries and libraries under the
`bin/`, `lib/` and `x64/` folders of `framework/cauldron/framework/libs`, `sdk/libs` and
`sdk/tools/ffx_shader_compiler/libs`, about 216 MB.

### The descriptor pool defect

`sdk/src/backends/vk/ffx_vk.cpp` builds a six-entry `VkDescriptorPoolSize` array and sets
`poolSizeCount = 5`. The sixth entry is `VK_DESCRIPTOR_TYPE_STORAGE_BUFFER`, so the pool has no
storage-buffer capacity. The FSR3 upscaler declares no buffer resources and works. Frame
interpolation declares `FI_Counters` as a buffer; on drivers that do not return
`VK_ERROR_OUT_OF_POOL_MEMORY` the allocation appears to succeed, the descriptor is unbacked, and
every generated frame is black with a clean return code. The signed DLL contains the same
instruction sequence at RVA `0x18001e232`, so the fix has to come from the library source.
Commit `0457c0a` fixes it.

## Status

The Vulkan backend configures under Ninja and builds `amd_fidelityfx_vk.dll` from source. The
DirectX 12 backend, the samples and Radeon hardware are unverified: development and testing run
on NVIDIA Ampere, and reports from RDNA are welcome. The open findings are in the
[estate audit](docs/agent/2026_10_05_ESTATE_AUDIT/REPORT.md).

## Documentation

[docs/index.md](docs/index.md) is AMD's manual, kept as published. AMD's original readme is
[UPSTREAM_README.md](UPSTREAM_README.md), renamed because `readme.md` and `README.md` cannot
coexist on a case-insensitive filesystem.

## Licence

MIT, in [LICENSE.txt](LICENSE.txt). The file is AMD's and stays as it is. Changes made here are
MIT as well, Copyright (c) 2026 Sushi Systems, and the files they touch keep AMD's header. The
DirectX Shader Compiler, Agility SDK and PIX binaries under the `libs/` folders are Microsoft's,
under the `LICENSE-MS.txt` files beside them.

AMD, FidelityFX and the AMD marks belong to Advanced Micro Devices, Inc. This project is not
affiliated with or endorsed by AMD. Vulkan is a registered trademark of the Khronos Group Inc.

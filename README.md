# SushiFX

A fork of the AMD FidelityFX SDK that keeps its Vulkan backend alive.

**Scope:** FSR 3.1 upscaling and frame interpolation, on Vulkan. Nothing else. The DirectX 12
backend, the samples and the Cauldron framework come along because they are part of the tree
AMD published, but they are not maintained here.

**Status:** nothing has been built yet. The first question this project has to answer is
whether the Vulkan backend compiles from source at all, shaders included. Until that is
answered, treat every claim below as intent.

## Why it exists

AMD's FSR SDK moved to a v2 line, and that line is DirectX 12 only. Its readme lists
"Vulkan is currently not supported in SDK" among the known issues, and the public tree carries
`Kits/FidelityFX/backend/dx12` with no Vulkan sibling and six signed DirectX 12 DLLs with no
Vulkan counterpart. The Vulkan backend exists only in the 1.1.x line, whose last release was
v1.1.4 in May 2025. That is the commit this fork starts from.

A Vulkan engine that wants FSR 3.1 therefore depends on a subtree its upstream no longer
carries on any branch. That is the gap this fork fills.

There is also a specific defect to fix. `sdk/src/backends/vk/ffx_vk.cpp` builds a six-entry
`VkDescriptorPoolSize` array and then sets `poolSizeCount = 5`. The sixth entry is
`VK_DESCRIPTOR_TYPE_STORAGE_BUFFER`, so the pool is created with no storage-buffer capacity.
The FSR3 upscaler declares no buffer resources and works; frame interpolation declares
`FI_Counters` as a buffer, and on drivers that do not return `VK_ERROR_OUT_OF_POOL_MEMORY` the
allocation appears to succeed, the descriptor is unbacked, and every generated frame is black
with a clean return code. The same instruction sequence is present in the signed
`amd_fidelityfx_vk.dll`, at RVA `0x18001e232`, which is why the fix cannot come from outside
the library.

## Where this starts

The import commit is AMD's tree exactly as published at the `v1.1.4` tag, upstream commit
`c6efa6bf7f2027b3ec94f28578bb5965eabb9e55`, released May 2025. Every commit above it is local
work, so `git diff` against that commit is the complete list of what this fork changes.

## Hardware

Developed and tested on NVIDIA Ampere. No RDNA hardware is available to this project, so
results on Radeon parts are unverified and reports are welcome. FSR is vendor-agnostic by
design, which is the reason a fork maintained on the wrong vendor's card is worth anything at
all.

## Licence and attribution

Upstream is MIT and stays MIT; see [LICENSE.txt](LICENSE.txt), which is AMD's and is not to be
removed or replaced. Changes made here are MIT as well.

AMD, FidelityFX and the AMD marks belong to Advanced Micro Devices, Inc. This project is not
affiliated with AMD, is not endorsed by AMD, and does not speak for it. Vulkan is a registered
trademark of the Khronos Group Inc.

AMD's original readme is preserved as [UPSTREAM_README.md](UPSTREAM_README.md), renamed only
because `readme.md` and `README.md` cannot coexist on a case-insensitive filesystem.

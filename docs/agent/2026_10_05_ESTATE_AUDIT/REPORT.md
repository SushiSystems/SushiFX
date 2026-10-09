# Estate audit: sushifx

**Status:** Complete. Read-only audit of 2026-10-05; nothing in the repository was changed.

One auditing agent per dimension read the tree and a second agent checked each finding against
the files. A finding marked *confirmed* was re-read by the reviewer; *unclear* means the reviewer
could not settle it; *found by review* means the first pass missed it and nobody re-checked it.
Refuted findings are listed and not counted. No build, test or project CLI was run.

| Dimension | High | Medium | Low | Refuted |
| --- | --- | --- | --- | --- |
| Licence | 4 | 7 | 4 | 0 |
| Layout and hygiene | 3 | 5 | 3 | 0 |

## Licence

### Facts

- Repository: D:/Projects/sushifx, branch main tracking origin https://github.com/SushiSystems/SushiFX.git, 1737 tracked files, working tree clean, no git tags.
- This repository is not Apache-2.0 and never was. D:/Projects/sushifx/LICENSE.txt is the MIT licence text headed 'This file is part of the FidelityFX SDK. Copyright (C) 2024 Advanced Micro Devices, Inc.'
- D:/Projects/sushifx/sdk/LICENSE.txt is byte-identical to the root LICENSE.txt (diff reports no difference). D:/Projects/sushifx/docs/license.md is the same MIT text with 'Copyright © 2024 Advanced Micro Devices, Inc.'
- What upstream MIT permits: use, copy, modify, merge, publish, distribute, sublicense and sell, by any person, free of charge. What it requires: the AMD copyright notice and the permission notice stay in all copies or substantial portions. No trademark grant, no patent grant.
- Other licence documents in the tree: sdk/include/FidelityFX/host/backends/dx12/license.txt (MIT, Copyright (c) 2024 Microsoft, covers d3dx12.h); framework/cauldron/framework/libs/AGS/LICENSE.txt and libs/acs/LICENSE.txt (AMD FidelityFX MIT text, 2024).
- More licence documents: libs/imgui/LICENSE.txt (MIT, 2014-2024 Omar Cornut); libs/json/License.txt (MIT, 2013-2017 Niels Lohmann); libs/memoryallocator/license.txt (MIT, 2017-2024 AMD); libs/vectormath/LICENSE.txt (BSD-3-Clause, 2006-2007 Sony Computer Entertainment Inc.).
- More licence documents: libs/dxc/LICENSE-LLVM.txt, LICENSE-MIT.txt, LICENSE-MS.txt, present twice (framework/cauldron/framework/libs/dxc and sdk/tools/ffx_shader_compiler/libs/dxc). LICENSE-MS.txt is the proprietary 'Microsoft Software License Terms, Microsoft DirectX Shader Compiler'.
- More licence documents under sdk/tools/ffx_shader_compiler/libs: MD5/LICENSE (MIT, 2015 Michael), SPIRV-Reflect/LICENSE (Apache-2.0), tiny-process-library/LICENSE (MIT, 2015-2020 Ole Christian Eidheim). samples/thirdparty/samplercpp/readme.txt names a source URL (eheitzresearch.wordpress.com) and states no licence.
- No NOTICE, COPYING, AUTHORS or THIRD_PARTY file exists anywhere in the tree.
- Source census (tracked .c .cpp .h .hpp .hlsl .glsl .bat .rc .cmake, CMakeLists.txt, CMakeCompileShaders.txt): 1299 files; 1136 outside libs/ and thirdparty/, 163 inside. By type overall: h 579, cpp 238, hlsl 216, glsl 155, cmake 71, hpp 25, bat 12, rc 2, c 1. No Python, TypeScript or shell source.
- Header variant A, 'This file is part of the FidelityFX SDK' + AMD MIT: 1130 of the 1136 non-vendored source files (h 477, hlsl 215, cpp 213, glsl 155, cmake 52, bat 12, hpp 6). Examples: sdk/src/backends/vk/ffx_vk.cpp, CMakeLists.txt, sdk/toolchain.cmake. 1218 tracked files carry the phrase in total.
- Non-vendored source with no header: 6 files (h 3, rc 2, cmake 1): ffx-api/src/resource/ffx_api_dll.rc, ffx-api/src/resource/resource.h, framework/cauldron/application/icon/cauldron.rc, framework/cauldron/application/icon/resource.h, samples/hybridshadows/CMakeLists.txt, sdk/include/FidelityFX/host/backends/dx12/d3dx12.h (Microsoft, covered by the sibling license.txt).
- AMD copyright line variants across all tracked text: 'Copyright (C) 2024 Advanced Micro Devices, Inc.' 1215; '(C) 2025' 1 (sdk/src/shared/ffx_message.cpp); '(c) 2023 ... All rights reserved' 3; '(c) 2017-2024' 3; 'Copyright(c) 2023' 2 (translucencyps.hlsl, samples/vrs/shaders/motionvectorsps.hlsl); 'Copyright 2024' 2 (.clang-format, .clang-tidy); '(c) 2024 All rights reserved' 2; '(c) 2020' 2; '(c) 2019-2024' 2; '(c) 2019-2022' 1; '© 2024' 1.
- Vendored header variants (163 files): Microsoft MIT two-line header (agilitysdk, dxheaders, pix), MIT Baldur Karlsson 2019-2024 (renderdoc_app.h), public domain (stb), AMD MIT 'All rights reserved' (AGS, acs, antilag2, memoryallocator). 20 vendored source files have no copyright or licence word in their first 40 lines: imgui 9, tiny-process-library 4, vectormath 3, MD5 3, SPIRV-Reflect 1; each of those folders has a LICENSE file.
- No file in the tree carries a Sushi Systems header, copyright line or licence block. 'git grep -i sushi' matches one file: README.md.
- Copyright holders named: Advanced Micro Devices, Inc. (2017 to 2025); Microsoft / Microsoft Corporation (2024 or undated); Omar Cornut; Niels Lohmann; Sony Computer Entertainment Inc.; Baldur Karlsson; Michael (MD5); Ole Christian Eidheim. Sushi Systems and Mustafa Garip appear in no copyright line.
- Machine-readable licence declarations: none. There is no pyproject.toml, setup.py, package.json, sushi-module.toml, Dockerfile, conda file, vcpkg.json or conanfile. No CMake file declares a licence. Doxyfile sets PROJECT_NAME = "FidelityFX SDK", PROJECT_NUMBER = "1.0" and takes ./docs/license.md as input (Doxyfile:7-8, 126). .gitlab-ci.yml:220 packages ./sdk/LICENSE.txt.
- Prose statements: README.md:49-50 'Upstream is MIT and stays MIT; see LICENSE.txt, which is AMD's and is not to be removed or replaced. Changes made here are MIT as well.' README.md:52-54 disclaims AMD affiliation and names AMD and Khronos marks.
- Upstream prose kept verbatim: UPSTREAM_README.md:73-75, docs/index.md:74-76 and docs/getting-started/index.md:42-44 each say 'AMD FidelityFX SDK is open source, and available/distributed under the MIT license'.
- git shortlog -sne HEAD: one author, '6 Mustafa Garip <garipm@mef.edu.tr>'. Six commits, all dated 2026-08-30.
- Fork point: commit 421e80a 'Import AMD FidelityFX SDK 1.1.4'; README.md:37-39 states it equals upstream tag v1.1.4, commit c6efa6bf7f2027b3ec94f28578bb5965eabb9e55.
- Sushi changes since the fork (git diff 421e80a HEAD --stat: 7 files, 160 insertions, 35 deletions): README.md added (57 lines); readme.md renamed to UPSTREAM_README.md unchanged; ffx-api/CMakeLists.txt; sdk/toolchain.cmake; sdk/include/FidelityFX/gpu/CMakeCompileShaders.txt; sdk/src/backends/vk/ffx_vk.cpp (+8 -1); sdk/include/FidelityFX/gpu/fsr3upscaler/ffx_fsr3upscaler_callbacks_glsl.h (1 line).
- The five modified upstream files keep the AMD header unchanged and carry no Sushi notice, no 'modified by' line and no date of change. The only place Sushi authorship is stated is README.md and the git history.
- Vendored third-party components and where each notice lives: imgui (MIT, LICENSE.txt), nlohmann json (MIT, License.txt), D3D12MemAlloc/VMA (MIT, license.txt), vectormath (BSD-3, LICENSE.txt), stb (public domain, in-file only), renderdoc (MIT, in renderdoc_app.h only), PIX (MIT, in-file only; two copies: framework libs/pix and sdk/libs/pix).
- Vendored, continued: Agility SDK and DirectX-Headers (Microsoft MIT in-file headers only; three copies: libs/agilitysdk, libs/dxheaders, shader compiler libs/agilitysdk); AGS and ACS (AMD MIT LICENSE.txt, shipped as DLL/LIB plus header); AntiLag2 (AMD MIT in-file; two copies); DXC (three licence files); MD5, SPIRV-Reflect, tiny-process-library (LICENSE each); samplercpp blue-noise tables (no licence).
- 31 binaries are tracked: PrebuiltSignedDLL/amd_fidelityfx_{dx12,vk}.{dll,lib}; 18 AGS/ACS DLL and LIB files; libs/renderdoc/renderdoc.dll; sdk/tools/binary_store/{D3D12Core.dll, d3d12SDKLayers.dll, d3dconfig.exe, dxcompiler.dll, dxil.dll, glslangValidator.exe, FidelityFX_SC.exe}; sdk/tools/media_delivery/MediaDelivery.exe.
- Fetched at build or run time: Vulkan SDK through find_package(Vulkan REQUIRED) (ffx-api/CMakeLists.txt:160, sdk/src/backends/vk/CMakeLists.txt:39, framework/cauldron/framework/CMakeLists.txt:52); sample media through sdk/tools/media_delivery/MediaDelivery.exe called by UpdateMedia.bat:47. No FetchContent, ExternalProject, vcpkg, pip or npm dependency.
- There is no docs/reference/CHANGELOG.md and no changelog of Sushi releases. No tag, no package metadata and no release is recorded in the tree.

### Corrections from review

- F7 and the fact 'samplercpp blue-noise tables (no licence)': wrong. All nine samples/thirdparty/samplercpp/samplerBlueNoiseErrorDistribution_*.cpp files open with the AMD MIT header ('This file is part of the FidelityFX SDK. Copyright (C) 2024 Advanced Micro Devices, Inc.'). Only readme.txt lacks a licence.
- Copyright holders list is incomplete. Holders named inside AMD-headed, non-vendored source and missing from the audit: Simon Wallner 2011 (framework/rendermodules/skydome/shaders/skydomeproc.hlsl:24), MJP 2019 (framework/rendermodules/taa/shaders/taa.hlsl:88), Inigo Quilez 2014 (sdk/include/FidelityFX/gpu/brixelizer/ffx_brixelizer_common_private.h:56), Playdead 2015 (ffx_brixelizergi_main.h:90, ffx_denoiser_reflections_common.h:123 and :226), Eric Heitz 2018 (ffx_brixelizergi_main.h:315), David Hoskins 2014 (sdk/include/FidelityFX/gpu/dof/ffx_dof_blur.h:563), RSA Data Security 1990 (sdk/tools/ffx_shader_compiler/src/DXBCChecksum.cpp:56 and .h:56), Morgan McGuire, BSD (ffx_brixelizer_debug_visualization.h:40-42).
- The header-variant facts list only AMD MIT for non-vendored source. Three non-vendored shaders carry an Apache-2.0 block as well: framework/rendermodules/gbuffer/shaders/gbufferps.hlsl:23, framework/rendermodules/translucency/shaders/translucencyps.hlsl:25, samples/vrs/shaders/motionvectorsps.hlsl:25. The audit named two of them only as carriers of a 'Copyright(c) 2023' year variant.
- F9 '13 separate LICENSE files': 16 third-party licence files are tracked (the dxc trio exists twice); 13 is the count of distinct texts. With LICENSE.txt, sdk/LICENSE.txt and docs/license.md the tree holds 19 licence documents.
- 'cmake 71' in the census: only 3 files have the .cmake extension; the other 68 are CMakeLists.txt and CMakeCompileShaders.txt. The total of 1299 is right.
- '31 binaries are tracked' is right for dll, exe and lib (recomputed 31), but the pattern leaves out four .exp files under libs/acs and framework/cauldron/framework/libs/AGS/amd_ags.chm, which are also binary AMD redistributables: 36 in all.
- Recomputed and correct: 1737 tracked files; 1299 source, 1136 non-vendored, 6 without header; 1218 files with the FidelityFX phrase; all eleven AMD copyright-line variant counts; one author with 6 commits; 7 files, +160 -35 since 421e80a; LICENSE.txt identical to sdk/LICENSE.txt.

### Findings

#### L1. [high] The planned Apache-2.0 to non-commercial move does not apply to this repository as stated

Evidence: D:/Projects/sushifx/LICENSE.txt is AMD's MIT text ('Copyright (C) 2024 Advanced Micro Devices, Inc.'), not Apache-2.0. 1218 tracked files carry 'This file is part of the FidelityFX SDK' with the AMD MIT header. git diff 421e80a HEAD --stat: 7 files changed, 160 insertions, 35 deletions, so Sushi owns roughly 160 lines out of 1737 files.

Recommendation: Treat sushifx as an exception in the relicensing programme. AMD's copyright cannot be relicensed and its MIT notice must stay on every file. The owner has to decide between two options: (a) leave the whole repository MIT, which is what README.md:49-50 already says, or (b) keep AMD's files under MIT and put only Sushi's own changes under the new licence. Under (b) anyone can still take the AMD original commercially, so the restriction would cover only the 160 changed lines.

Review: confirmed. LICENSE.txt is AMD's MIT text (2024); git grep counts 1218 files with the FidelityFX phrase; git diff 421e80a HEAD --stat gives 7 files, 160 insertions, 35 deletions. 'Never Apache-2.0' holds for the six commits in the local history.

#### L2. [high] Sushi changes are already published under MIT and that grant cannot be withdrawn

Evidence: README.md:50 'Changes made here are MIT as well.' The branch tracks origin/main at https://github.com/SushiSystems/SushiFX.git with no local divergence (git status -sb: '## main...origin/main'), so commits 130694d, 5cb3c24, 8d6a039, 0457c0a and 3cdb28d are published with that statement.

Recommendation: Accept that everything up to 3cdb28d stays MIT for anyone who already has it. A new licence can only cover commits made after the change, and README.md:49-50 has to be rewritten in the same commit to say where the line falls.

Review: confirmed. README.md:49-50 reads 'Changes made here are MIT as well'; git status -sb shows main...origin/main with no divergence. Caveat: this compares against the local remote-tracking ref without a fetch, so 'published' rests on the last push or fetch, not on a look at GitHub.

#### L3. [high] The Sushi boxed licence header must not be applied to this tree

Evidence: The source-comments skill prescribes a Sushi licence block opening every source file, and the task plans a header rewrite across all repositories. Here 1130 of 1136 non-vendored source files carry AMD's MIT header (e.g. sdk/src/backends/vk/ffx_vk.cpp, sdk/toolchain.cmake, CMakeLists.txt), and the MIT condition in LICENSE.txt requires that notice to stay in all copies.

Recommendation: Exclude D:/Projects/sushifx from any bulk header rewrite and from tools/documentation/check_source_comments.py's licence-block rule, or give the checker an explicit upstream-fork mode. Replacing or wrapping the AMD header would remove a required notice.

Review: confirmed. Recomputed 1130 of 1136 non-vendored source files with the AMD header. The source-comments skill does prescribe a boxed licence block per file, and the MIT text requires the AMD notice to stay. An upstream-fork mode in the checker is a clean single-purpose fix.

#### L4. [high] Proprietary Microsoft terms on the DirectX Shader Compiler binaries impose their own conditions

Evidence: framework/cauldron/framework/libs/dxc/LICENSE-MS.txt:16 'you may install and use any number of copies of the software, and solely for use on Windows'; lines 38-48 set distribution requirements, an indemnity to Microsoft and a ban on putting the code under a licence that forces source disclosure. Same file at sdk/tools/ffx_shader_compiler/libs/dxc/LICENSE-MS.txt. Binaries: sdk/tools/binary_store/dxcompiler.dll, dxil.dll.

Recommendation: These terms are a vendor SDK licence of the kind the dependencies skill rejects. They came with the AMD import and the README says the DX12 side is unmaintained. Ask the owner whether to drop the DXC, Agility SDK and DX12 binaries from the fork; if they stay, the repository notice must say they are Microsoft's under their own terms and outside any Sushi licence.

Review: confirmed. framework/cauldron/framework/libs/dxc/LICENSE-MS.txt:16 has the Windows-only wording; lines 36-50 carry the distribution requirements, indemnity and the copyleft ban; the sdk/tools copy is byte-identical (cmp). dxcompiler.dll and dxil.dll are tracked in sdk/tools/binary_store. The dependencies skill rejects vendor SDK licences that restrict redistribution.

#### L5. [medium] Modified upstream files carry no notice of modification or of Sushi authorship

Evidence: ffx-api/CMakeLists.txt, sdk/toolchain.cmake, sdk/include/FidelityFX/gpu/CMakeCompileShaders.txt, sdk/src/backends/vk/ffx_vk.cpp and sdk/include/FidelityFX/gpu/fsr3upscaler/ffx_fsr3upscaler_callbacks_glsl.h were changed after 421e80a and still open with only the AMD header. 'git grep -i sushi' matches README.md alone. No NOTICE file exists.

Recommendation: MIT does not require a change notice, so this is not a breach today. It becomes a defect the moment Sushi changes get their own terms: a reader cannot tell which lines are AMD's. Add a root NOTICE (or a section in README.md) that says: this is AMD FidelityFX SDK 1.1.4, upstream commit c6efa6bf, MIT, copyright AMD; files changed by Sushi Systems are listed here; Sushi changes are copyright Mustafa Garip and Sushi Systems under <chosen licence>. In each changed file keep the AMD block intact and add one line below it, 'Modifications Copyright (c) 2026 Mustafa Garip & Sushi Systems', rather than the Sushi boxed header from the source-comments skill.

Review: confirmed. The five changed files appear in git diff --stat; git grep -lIi sushi returns README.md alone; no NOTICE is tracked. The recommendation is brick-shaped (one notice file, one line per changed file below the intact AMD block).

#### L6. [medium] Redistributed binaries with no licence file beside them

Evidence: sdk/tools/binary_store/ holds D3D12Core.dll, d3d12SDKLayers.dll, d3dconfig.exe (Microsoft Agility SDK redistributables), glslangValidator.exe and FidelityFX_SC.exe with no licence document in the folder. sdk/tools/ffx_shader_compiler/libs/glslangValidator/ holds only CAULDRONREADME.md and CMakeLists.txt. sdk/tools/media_delivery/MediaDelivery.exe has no licence. framework/cauldron/framework/libs/renderdoc/renderdoc.dll has its MIT text only inside include/renderdoc_app.h.

Recommendation: Record each binary's origin, version and licence in the repository notice. glslang is distributed under a mix of BSD, MIT, Apache-2.0 and GPL-3 with a Bison exception; its licence text has to ship with the executable. The Agility SDK redistributables fall under Microsoft's Agility SDK licence, which was not found in the tree.

Review: confirmed. git ls-files shows sdk/tools/binary_store with seven binaries and no licence file, glslangValidator/ with only CAULDRONREADME.md and CMakeLists.txt, MediaDelivery.exe alone, and renderdoc/ with no LICENSE. The glslang licence mix is the auditor's outside knowledge and was not checked against the tree.

#### L7. [medium] Blue-noise sampler tables have no licence

Evidence: samples/thirdparty/samplercpp/readme.txt gives only 'Source: https://eheitzresearch.wordpress.com/762-2/' and a description. The nine samplerBlueNoiseErrorDistribution_*.cpp files in the same folder carry no licence statement that I found.

Recommendation: Without a stated licence there is no right to redistribute. The samples are outside the fork's declared scope (README.md:5-7); the clean answer is to remove samples/thirdparty/samplercpp, which needs the owner's decision since it deletes imported files. Otherwise find and record the authors' terms.

Review: unclear. readme.txt is as quoted, but the evidence sentence is wrong: all nine samplerBlueNoiseErrorDistribution_*.cpp files open with AMD's 'This file is part of the FidelityFX SDK' MIT header. The provenance gap is real (third-party data under an AMD header, source page states no licence in the tree), but 'no licence statement' is false and the remedy differs: AMD asserts MIT over these files, and the same author's code carries an MIT notice at sdk/include/FidelityFX/gpu/brixelizergi/ffx_brixelizergi_main.h:315.

#### L8. [medium] Prebuilt signed AMD DLLs sit next to source that no longer matches them

Evidence: PrebuiltSignedDLL/amd_fidelityfx_vk.dll and amd_fidelityfx_dx12.dll (plus .lib) are tracked. README.md:28-31 states the signed amd_fidelityfx_vk.dll still contains the descriptor-pool defect that commit 0457c0a fixes in sdk/src/backends/vk/ffx_vk.cpp.

Recommendation: The binaries are AMD's, signed by AMD, and are not Sushi work; no Sushi licence can cover them. State that in the notice, or remove the folder with the owner's approval so nobody takes the AMD-signed binary for the fork's output.

Review: confirmed. PrebuiltSignedDLL holds four tracked files; README.md:24-31 says the signed amd_fidelityfx_vk.dll contains the same poolSizeCount defect that the fork fixes in ffx_vk.cpp.

#### L9. [medium] Third-party notices embedded inside AMD-headed source were not inventoried

Evidence: A search for 'Copyright' outside libs/ and thirdparty/ finds MIT blocks for Simon Wallner (framework/rendermodules/skydome/shaders/skydomeproc.hlsl:23-24), MJP (framework/rendermodules/taa/shaders/taa.hlsl:85-88), Inigo Quilez (sdk/include/FidelityFX/gpu/brixelizer/ffx_brixelizer_common_private.h:54-56), Playdead (sdk/include/FidelityFX/gpu/brixelizergi/ffx_brixelizergi_main.h:90; sdk/include/FidelityFX/gpu/denoiser/ffx_denoiser_reflections_common.h:123, 226), Eric Heitz (ffx_brixelizergi_main.h:315), David Hoskins (sdk/include/FidelityFX/gpu/dof/ffx_dof_blur.h:563) and a BSD attribution to Morgan McGuire (sdk/include/FidelityFX/gpu/brixelizer/ffx_brixelizer_debug_visualization.h:40-42). The audit's holder list and third-party inventory name none of them, and its facts imply every non-vendored file is AMD MIT only.

Recommendation: Add these to the third-party inventory that F9 proposes, each with file, line, holder and licence. Any header tooling or fork-mode checker must treat the whole file as untouchable, since these notices sit in the middle of files, not at the top.

Review: found by review.

#### L10. [medium] RSA MD5 licence in the shader compiler imposes its own identification clause

Evidence: sdk/tools/ffx_shader_compiler/src/DXBCChecksum.cpp:54-74 and DXBCChecksum.h:56 carry 'Copyright (C) 1990, RSA Data Security, Inc.' with the condition that the software be identified as the 'RSA Data Security, Inc. MD5 Message Digest Algorithm' in all material mentioning it, and that the notices be retained. Both files open with the AMD MIT header. The brief asked for third-party licences that impose their own terms; the audit does not mention this one.

Recommendation: Record it in the repository notice with the required identification wording. It is not MIT and no Sushi or AMD header changes that.

Review: found by review.

#### L11. [medium] Apache-2.0 blocks in three non-vendored shaders

Evidence: framework/rendermodules/gbuffer/shaders/gbufferps.hlsl:23, framework/rendermodules/translucency/shaders/translucencyps.hlsl:23-25 ('Portions Copyright 2024 Advanced Micro Devices, Inc.' followed by the Apache-2.0 notice) and samples/vrs/shaders/motionvectorsps.hlsl:25 carry an Apache-2.0 licence block below the AMD MIT header. No Apache-2.0 text or NOTICE for these files is tracked outside sdk/tools/ffx_shader_compiler/libs/SPIRV-Reflect/LICENSE. The audit states the repository 'is not Apache-2.0 and never was' without this exception.

Recommendation: List the three files in the notice as dual-notice files (AMD MIT plus Apache-2.0 portions) and keep both blocks. Apache-2.0 section 4 requires the licence text to accompany redistribution, so the notice should point to a copy.

Review: found by review.

#### L12. [low] Third-party notices are scattered, with no single inventory

Evidence: Notices live in 13 separate LICENSE files plus in-file headers. stb, renderdoc, pix (two copies), agilitysdk (two copies), dxheaders and antilag2 (two copies) have no licence file in their folder, only headers; each has a CAULDRONREADME.md or FFX_SDK_README.md that names no licence. There is no third_party/<name>/README.md with source URL, version and licence as the dependencies skill requires.

Recommendation: Add one third-party inventory to the repository notice listing each component, its version, licence and the path of its notice. Do not restructure the upstream folders; that would break 'git diff against the import commit is the complete list of changes' (README.md:38-39).

Review: confirmed. Folder listing confirms stb, renderdoc, pix (2), agilitysdk (2), dxheaders and antilag2 (2) have no licence file. The count '13' holds only if the duplicated dxc trio is counted once; 16 third-party licence files are tracked, 19 with the three AMD ones.

#### L13. [low] Six non-vendored source files carry no licence header

Evidence: ffx-api/src/resource/ffx_api_dll.rc, ffx-api/src/resource/resource.h, framework/cauldron/application/icon/cauldron.rc, framework/cauldron/application/icon/resource.h, samples/hybridshadows/CMakeLists.txt, sdk/include/FidelityFX/host/backends/dx12/d3dx12.h.

Recommendation: Leave them as imported. Four are Visual Studio resource files, d3dx12.h is Microsoft's and covered by sdk/include/FidelityFX/host/backends/dx12/license.txt, and the root LICENSE.txt covers the rest. Adding headers to upstream files widens the diff against upstream for no legal gain.

Review: confirmed. grep -L over the 1136 non-vendored source files returns exactly the six listed paths. Leaving them untouched is the right call for a fork.

#### L14. [low] Upstream documentation and Doxyfile still present the tree as AMD's SDK

Evidence: Doxyfile:7 PROJECT_NAME = "FidelityFX SDK"; docs/index.md:74 and docs/getting-started/index.md:42 say 'AMD FidelityFX SDK is open source, and available under the MIT license'; docs/license.md names only AMD. None mentions the fork or Sushi's changes.

Recommendation: If Sushi changes take a separate licence, docs/license.md and these two pages would then state the licence incompletely. Add the fork notice to docs/license.md below AMD's text at that point; leave the AMD paragraphs as they are. Any generated documentation must not present itself as AMD's (README.md:52-54 already disclaims affiliation).

Review: confirmed. Doxyfile:7-8 and :126, docs/index.md:74 and docs/getting-started/index.md:42 read as quoted. Not a defect today; it becomes one only if Sushi changes take separate terms, which the finding says.

#### L15. [low] Source comment added by the fork breaks the comment rule

Evidence: sdk/src/backends/vk/ffx_vk.cpp, in CreateBackendContextVK above 'descriptorPoolCreateInfo.poolSizeCount = (uint32_t)FFX_ARRAY_ELEMENTS(poolSizes);': seven consecutive '//' lines explaining the history and reason for the fix (added by 0457c0a).

Recommendation: Outside the licence dimension but found while measuring Sushi's changes: the source-comments skill allows one '//' line stating an invariant. Move the explanation to a design document and leave one line. Reported for the code-review dimension to pick up.

Review: confirmed. git diff 421e80a HEAD on sdk/src/backends/vk/ffx_vk.cpp shows seven consecutive '//' lines with history and rationale above the poolSizeCount line. Outside the licence dimension, as the finding states; the fix (one invariant line, reason in a design document) matches the source-comments skill.

### Not checked

- Whether GitHub releases, packages or forks exist for SushiSystems/SushiFX; only the local clone was read, and it has no tags.
- The full text of the 20 vendored source files that show no licence word in their first 40 lines (imgui 9, tiny-process-library 4, vectormath 3, MD5 3, SPIRV-Reflect 1); only the folder LICENSE files were read.
- The individual headers of the nine samples/thirdparty/samplercpp .cpp files beyond a search for licence wording; the authors' terms on the source website were not fetched.
- The licence of the sample media bundle that MediaDelivery.exe downloads, and of fonts or assets embedded in imgui (docs/FONTS.md lists Apache-2.0, OFL-1.1 and MIT fonts).
- Version resources and embedded licence strings inside the 31 tracked binaries.
- The complete Microsoft DXC licence (LICENSE-MS.txt) was read only at its installation, distribution and restriction clauses; the Agility SDK licence text was not found in the tree and so not read.
- LICENSE-LLVM.txt and LICENSE-MIT.txt under libs/dxc were listed but not read.
- Non-source tracked files (json configs, .idl, .md, .xml, .yml, images) were not classified by header; the 1299-file census covers code, shader, CMake, batch and resource files only.
- The untracked, git-ignored build/ directory, per the task's exclusion.
- Whether upstream AMD has changed the licence of later FidelityFX SDK lines; only the v1.1.4 import in this repository was examined.
- No legal opinion: whether Turkish or other law treats the 160 changed lines as separately copyrightable was not assessed.

## Layout and hygiene

### Facts

- Repository: D:/Projects/sushifx, branch main, remote origin https://github.com/SushiSystems/SushiFX.git; local main is level with origin/main (0 ahead, 0 behind). No second remote pointing at AMD's upstream.
- History is 6 commits, all authored 2026-08-30 by Mustafa Garip: 421e80a import of AMD FidelityFX SDK 1.1.4 (1736 files), 130694d README front door, 5cb3c24 non-Visual-Studio generator, 8d6a039 shader dependency list, 0457c0a descriptor pool sixth entry, 3cdb28d luma history format.
- Total divergence from the import (git diff --stat 421e80a HEAD): 7 files, 160 insertions, 35 deletions: README.md (new), readme.md renamed to UPSTREAM_README.md, ffx-api/CMakeLists.txt, sdk/toolchain.cmake, sdk/include/FidelityFX/gpu/CMakeCompileShaders.txt, sdk/include/FidelityFX/gpu/fsr3upscaler/ffx_fsr3upscaler_callbacks_glsl.h, sdk/src/backends/vk/ffx_vk.cpp.
- git status is clean: no uncommitted and no untracked files. Ignored and present on disk: build/ (63 MB; build/api and build/vk Ninja trees with CMakeCache.txt), ffx-api/bin/ (21 MB; amd_fidelityfx_vk.dll, .exp, .lib, vulkan-1.dll, ffx_sdk/), sdk/bin/ (476 KB), plus several upstream libs/*/bin and libs/*/lib folders caught by the [Bb]in/ rule.
- Top-level tree (all tracked except build/): .clang-format, .clang-tidy, .editorconfig, .gitattributes, .gitignore, .gitlab-ci.yml (AMD's CI), four sample .bat build scripts plus UpdateMedia.bat, CMakeLists.txt, common.cmake, sample.cmake, Doxyfile, FidelityFXSDKLayout.xml, modules.rst, LICENSE.txt (AMD MIT), README.md (Sushi), UPSTREAM_README.md (AMD), docs/ (238 files, AMD manual), ffx-api/ (34), framework/ (492, Cauldron), samples/ (110), sdk/ (839), PrebuiltSignedDLL/ (4).
- 1737 tracked files. Sizes on disk: .git 106 MB, sdk 174 MB, framework 145 MB, docs 89 MB, build 63 MB, ffx-api 21 MB, PrebuiltSignedDLL 16 MB, samples 10 MB.
- Version numbers declared: FFX_SDK_VERSION 1.1.4 in sdk/include/FidelityFX/host/ffx_interface.h:50-60; FFXDLL_VERSION 1.0.1 in ffx-api/CMakeLists.txt:77-79; project(... VERSION 1.0.0) in CMakeLists.txt:44; docs/whats-new/index.md titled 1.1.4. All four are AMD's values; they disagree with each other upstream too. No Sushi version is declared anywhere.
- Git tags: none. No pyproject.toml, package.json or sushi-module.toml. No Sushi changelog; the only changelog-like files are AMD's docs/whats-new/*.md and the vendored imgui CHANGELOG.txt.
- CI: .gitlab-ci.yml only, inherited from AMD (GitLab runners tagged windows/amd64, calls cmake directly, 13 build jobs and a package job; format_check is 'echo Coming soon!'). No .github/ folder, so nothing runs on the GitHub remote.
- tools/ does not exist at the root; none of the four Sushi checkers are present. sdk/tools/ is AMD's (binary_store, media_delivery, ffx_shader_compiler).
- .gitignore is 379 lines: the Visual Studio template, AMD's /media/, /media-cache/ and GDK output folders, then a trailing block '# Build trees and in-source build output.' with build/, sdk/bin/, ffx-api/bin/. It is byte-identical between the import commit and HEAD.
- Tracked binaries (all from the AMD import): 11 .dll, 4 .exe, 16 .lib, 4 .pdf, 129 .png/.jpg, 45 .svg. Largest: renderdoc.dll 21.5 MB, sdk/tools/binary_store/dxcompiler.dll 17.8 MB, docs/samples/media/blur/blur.png 9.8 MB, MediaDelivery.exe 9.4 MB, PrebuiltSignedDLL/amd_fidelityfx_vk.dll 9.3 MB, PrebuiltSignedDLL/amd_fidelityfx_dx12.dll 6.7 MB.
- No AGENTS.md, CLAUDE.md, imgui.ini, egg-info, tracked CMakeCache, compile_commands.json, compiler probe files, .orig/.rej/.bak leftovers are tracked. The only file in the tree that mentions Sushi is README.md.
- Divergence is recorded in two places only: README.md section 'Where this starts' (upstream commit c6efa6bf7f2027b3ec94f28578bb5965eabb9e55, tag v1.1.4) and the commit messages. There is no patch list, NOTICE or fork changelog file.

### Corrections from review

- CI fact says '13 build jobs and a package job'. .gitlab-ci.yml has 12 build_* jobs (lines 25-182), one format_check and one package job (line 197).
- Fact 4 treats the nine ignored libs/*/bin and libs/*/lib folders as build-like residue ('caught by the [Bb]in/ rule') and fact 5 says everything at the top level is tracked except build/. Those nine folders hold 49 files of AMD's published tree, about 216 MB (226,556,988 bytes), dated with the import and never committed. Two of them (dxc/lib) are caught by the x64/ rule at .gitignore:25, not by [Bb]in/.
- The tracked-binary fact lists '11 .dll, 4 .exe, 16 .lib, 4 .pdf, 129 .png/.jpg, 45 .svg' and omits the 1 tracked .ico; the audit's own verification output does show it. The conclusion is unaffected.
- Sizes 'sdk 174 MB, framework 145 MB' are on-disk sizes that include the 216 MB of ignored, uncommitted upstream binaries, so they overstate what git carries in those folders.

### Findings

#### L1. [high] README status is false: it says nothing has been built, while the history and the disk show a built and verified Vulkan DLL

Evidence: D:/Projects/sushifx/README.md:9-11 '**Status:** nothing has been built yet ... treat every claim below as intent.' Commit 0457c0a says 'Verified in the binary this tree builds: the same instruction at the same stack offset now writes 6.' D:/Projects/sushifx/ffx-api/bin/amd_fidelityfx_vk.dll exists, and build/api, build/vk are configured Ninja trees. README.md:22-30 still describes the descriptor pool defect as 'a specific defect to fix', but sdk/src/backends/vk/ffx_vk.cpp:1539 already reads poolSizeCount = (uint32_t)FFX_ARRAY_ELEMENTS(poolSizes).

Recommendation: Rewrite the Status and defect paragraphs to match the four commits that landed after the README: what builds, under which generator, what was fixed, what is still unverified (DX12, samples, Radeon hardware).

Review: confirmed. README.md:9-11 still says nothing has been built; ffx-api/bin/amd_fidelityfx_vk.dll (9,320,960 bytes, 2026-08-30 03:25) exists, commit 0457c0a claims a verified binary, and sdk/src/backends/vk/ffx_vk.cpp:1539 holds the fix that README.md:24-32 describes as still to do.

#### L2. [high] The shipped prebuilt Vulkan DLL still carries the defect the fork exists to fix

Evidence: D:/Projects/sushifx/PrebuiltSignedDLL/amd_fidelityfx_vk.dll (9,332,432 bytes) and amd_fidelityfx_vk.lib are tracked as imported from AMD. README.md:27-30 states this very DLL has the poolSizeCount = 5 instruction at RVA 0x18001e232. The source fix is in sdk/src/backends/vk/ffx_vk.cpp:1539, but the fixed binary lives only in the ignored ffx-api/bin/. A consumer who takes PrebuiltSignedDLL/ from this fork gets black generated frames.

Recommendation: Owner decision: either state in README.md and beside the folder that PrebuiltSignedDLL/ is AMD's unmodified, defective binary and must not be used for Vulkan, or publish the fixed build as a release asset on a tag. Do not overwrite AMD's signed file in place under the same name.

Review: confirmed. PrebuiltSignedDLL/amd_fidelityfx_vk.dll is tracked at 9,332,432 bytes and differs from the local build (9,320,960). That it carries the defect rests on README.md:30-32 and commit 0457c0a; nobody disassembled it, and the audit says so under not_checked. The recommendation leaves AMD's signed file alone, which is the right shape.

#### L3. [high] The import silently dropped 49 upstream files (about 216 MB), so a clone is not AMD's tree and cannot rebuild the shader compiler

Evidence: git ls-files -o -i --exclude-standard -- framework sdk/libs sdk/tools lists 49 files, 226,556,988 bytes, all dated 2026-08-30 01:44 (the import time), in nine folders: framework/cauldron/framework/libs/{agilitysdk/bin, dxc/bin, dxc/lib, pix/bin}, sdk/libs/pix/bin, sdk/tools/ffx_shader_compiler/libs/{agilitysdk/bin, dxc/bin, dxc/lib, glslangValidator/bin}. git check-ignore -v attributes them to D:/Projects/sushifx/.gitignore:30 ([Bb]in/) and :25 (x64/). D:/Projects/sushifx/sdk/tools/ffx_shader_compiler/libs/glslangValidator/CMakeLists.txt:26-27 references bin/x64/glslangValidator.exe in the source tree, so upstream ships it. The import message (421e80a) and README.md:34-36 both say the tree is exactly as AMD published. The Vulkan DLL build itself uses the tracked sdk/tools/binary_store/FidelityFX_SC.exe (sdk/CMakeLists.txt:172), so the fork's stated scope still builds from a clone; rebuilding ffx_shader_compiler, the DX12 path and the Cauldron samples would not. I did not fetch upstream to confirm AMD tracks these 49 files.

Recommendation: Owner decision between two recorded states: force-add the 49 files in one commit so the tree matches upstream, or keep them out and say in the README and the divergence record that the import omits the ignored bin/ and lib/ folders, naming them. Either way correct the 'exactly as published' sentence in README.md. This also bears on F8: about 216 MB of the unmaintained weight is already absent from git.

Review: found by review.

#### L4. [medium] No tag and no fork version, so no consumer can pin a fixed state

Evidence: git tag prints nothing. Versions in the tree are all AMD's: sdk/include/FidelityFX/host/ffx_interface.h:50-60 (1.1.4), ffx-api/CMakeLists.txt:77-79 (FFXDLL 1.0.1), CMakeLists.txt:44 (1.0.0). Three behaviour fixes (0457c0a, 3cdb28d, 8d6a039) and one build change (5cb3c24) sit above the import with nothing naming them. The upstream base point is not tagged either; it is referenced only by hash 421e80a in prose.

Recommendation: Tag the import commit as the upstream base (for example upstream-v1.1.4) and decide a fork version scheme that keeps AMD's number visible (for example v1.1.4-sushi.1). Leave AMD's version macros untouched so the ABI version check still matches.

Review: confirmed. git tag prints nothing; ffx_interface.h:50/55/60 = 1.1.4, ffx-api/CMakeLists.txt:77-79 = 1.0.1, CMakeLists.txt:44 = 1.0.0. One flaw in the recommendation: under SemVer 'v1.1.4-sushi.1' is a pre-release and sorts below v1.1.4, and versioning-and-release reserves suffixes for pre-releases. The scheme needs an owner decision, not that example.

#### L5. [medium] Divergence from upstream is recorded only in commit messages; there is no file that lists it

Evidence: git diff --stat 421e80a HEAD shows 7 files changed. README.md:34-38 says 'git diff against that commit is the complete list of what this fork changes' and gives no list. There is no CHANGELOG, NOTICE or patch index anywhere in the tree (git ls-files matches only framework/cauldron/framework/libs/imgui/docs/CHANGELOG.txt). A source archive or GitHub zip download carries no history, so the record is lost there.

Recommendation: Add one fork changelog file, kept outside AMD's docs/ pages so upstream files stay unedited, with one line per local change and the file it touches. Location is an owner decision, since docs/ here is AMD's Doxygen manual and not the Sushi docs tree.

Review: confirmed. git diff --stat 421e80a HEAD gives 7 files, 160 insertions, 35 deletions. README.md:34-38 points at git diff and lists nothing. No CHANGELOG, NOTICE or patch index is tracked.

#### L6. [medium] The import commit is not byte-for-byte AMD's tree, although its message and the README say it is

Evidence: git show 421e80a:.gitignore ends with '# Build trees and in-source build output.\nbuild/\nsdk/bin/\nffx-api/bin/' (D:/Projects/sushifx/.gitignore:376-379), a block in the fork's wording that already covers [Bb]uild/ at line 31; git diff 421e80a HEAD -- .gitignore is empty, so it entered with the import. The import message says 'The tree exactly as AMD published it' and README.md:34-36 repeats it. I could not compare against the AMD repository offline, so this is an inference from the text, not a confirmed diff.

Recommendation: Diff 421e80a against upstream c6efa6bf7f2027b3ec94f28578bb5965eabb9e55 once. If the .gitignore block is local, say so in the divergence record; history should not be rewritten since main is already pushed.

Review: confirmed. The conclusion holds, on stronger evidence than the audit cites. .gitignore:376-379 and line 31 are as stated and the block came in with the import. Beyond that, 49 files AMD shipped sit on disk with the import timestamp (2026-08-30 01:44) and were never committed, because .gitignore:25 (x64/) and :30 ([Bb]in/) exclude them. See missed item 1.

#### L7. [medium] No CI runs on the forge the fork lives on

Evidence: D:/Projects/sushifx/.gitlab-ci.yml is AMD's GitLab pipeline (runner tags windows/amd64, lines 9-12; format_check at lines 19-23 is 'echo Coming soon!'). The remote is github.com/SushiSystems/SushiFX and there is no .github/ folder. The Ninja configure path added in 5cb3c24 and the dependency fix in 8d6a039 have no automated check, and the inherited jobs use the Visual Studio driver flags (line 4), not the generator the fork added support for.

Recommendation: Add one GitHub workflow that configures and builds the Vulkan SDK and ffx-api DLL, the only scope README.md:5 claims. Keep .gitlab-ci.yml as upstream's file or state in the README that it is inert here.

Review: confirmed. .gitlab-ci.yml:4, 9-12 and 19-23 are as quoted; no .github/ folder. The job count is 12 build jobs, not 13. The recommended workflow has to call cmake directly because the fork has no project CLI; that departs from continuous-integration rule 1 and should be stated as a fork exception.

#### L8. [medium] README gives no build line for the one thing the fork added

Evidence: D:/Projects/sushifx/README.md has 57 lines and no configure or build command. Commit 5cb3c24 made the Vulkan build configure under Ninja and 8d6a039 made it build, and build/api and build/vk exist locally, but the generator, the FFX_API_BACKEND=VK_X64 setting and the source directory (ffx-api) are written nowhere in the tree. UPSTREAM_README.md and the root .bat scripts describe the Visual Studio path only.

Recommendation: Add one build section to README.md with the exact configure and build lines used to produce ffx-api/bin/amd_fidelityfx_vk.dll, and the Vulkan SDK version it was built against. Fold it into the README rewrite F1 already asks for, as one edit.

Review: found by review.

#### L9. [low] No agent instruction file, so the fork's rules are not stated in the repository

Evidence: No AGENTS.md or CLAUDE.md at D:/Projects/sushifx (root listing; grep for 'sushi' matches README.md only). The rule that matters most here, that upstream files are edited minimally and LICENSE.txt is 'not to be removed or replaced' (README.md:49-50), is written for readers, not for an agent about to apply Sushi layout, comment or licence-header rules to AMD's sources.

Recommendation: Add a short AGENTS.md/CLAUDE.md stating that this is an upstream fork: Sushi layout, source-comment and licence-header rules do not apply to imported files, AMD's MIT headers stay, and each local change is recorded in the divergence file. This matters for the planned licence-header pass across the Sushi repositories.

Review: confirmed. No AGENTS.md or CLAUDE.md at the root; grep -i sushi matches README.md only. Low severity is right, but the planned licence-header pass makes it the cheapest guard against an agent rewriting AMD's MIT headers.

#### L10. [low] 31 third-party binaries and about 90 MB of sample media are carried in git for parts the fork declares unmaintained

Evidence: README.md:5-7 limits scope to FSR 3.1 on Vulkan and says DX12, samples and Cauldron 'are not maintained here'. Tracked regardless: framework/cauldron/framework/libs/renderdoc/renderdoc.dll (21.5 MB), sdk/tools/binary_store/dxcompiler.dll (17.8 MB), d3d12SDKLayers.dll (5.8 MB), D3D12Core.dll (3.3 MB), sdk/tools/media_delivery/MediaDelivery.exe (9.4 MB), PrebuiltSignedDLL/amd_fidelityfx_dx12.dll (6.7 MB), docs/ at 89 MB with duplicated images (docs/techniques/media/super-resolution-upscaler/upscaler-debug-overlay.svg and docs/samples/media/super-resolution/upscaler-debug-overlay.svg, 7.3 MB each). .git is 106 MB. All of it is upstream content, so this is a scope question, not a hygiene error.

Recommendation: Owner decision: keep the tree whole (simplest diff against upstream, current state) or prune the unmaintained subtrees in one recorded commit. Do not prune piecemeal; sdk/tools/binary_store holds the shader compiler the Vulkan build needs.

Review: confirmed. 11 dll + 4 exe + 16 lib = 31. renderdoc.dll 21,535,496; dxcompiler.dll 17,802,672; both upscaler-debug-overlay.svg copies 7,266,675 bytes. docs 89M, .git 106M. Framed as an owner decision, which fits a fork.

#### L11. [low] Root carries upstream helper files that no longer work or mislead in this fork

Evidence: D:/Projects/sushifx/BuildSamplesSolutionDX12.bat, BuildSamplesSolutionVK.bat, CleanAllGeneratedData.bat, ClearMediaCache.bat, UpdateMedia.bat, FidelityFXSDKLayout.xml, modules.rst, Doxyfile sit at the root as imported. UPSTREAM_README.md was renamed from readme.md (commit 130694d), while AMD's pages link by absolute repository paths such as '/docs/samples/index.md' (UPSTREAM_README.md:3-9), so the GitHub landing page no longer shows AMD's index and any upstream reference to readme.md is dead. A grep of docs/**/*.md for 'readme.md' found no such reference, so nothing in docs/ is broken by the rename.

Recommendation: Leave the upstream files in place (moving them widens the diff against AMD). Add one line to README.md naming which root scripts are upstream's and untested here.

Review: confirmed. The eight root files are tracked as listed; UPSTREAM_README.md:3-9 uses absolute /docs/ paths. Low severity is right. Leaving upstream files in place keeps the diff against AMD small.

### Not checked

- Byte comparison of the import commit 421e80a against AMD's upstream commit c6efa6bf7f2027b3ec94f28578bb5965eabb9e55; no network fetch was made, so F5 is an inference.
- Whether the tracked PrebuiltSignedDLL/amd_fidelityfx_vk.dll really contains the defect at RVA 0x18001e232; taken from README.md and commit 0457c0a, not disassembled.
- Contents of build/, ffx-api/bin/ and sdk/bin/ beyond a two-level listing (excluded by the task).
- GitHub-side state: repository visibility, description, default branch protection, releases, whether GitHub Actions is enabled.
- Comparison with sibling Sushi repositories' layout; the task says to judge this one as a fork, so no sibling was opened.
- Licence compatibility of each vendored binary under framework/cauldron/framework/libs and sdk/tools/binary_store (178 tracked files under framework libs alone); belongs to the licence dimension.
- Line-ending and .gitattributes behaviour (the file has no rule for .glsl, .cmake or .bat); not examined for actual CRLF damage.
- The 238 files under docs/ were not read for broken links or stale content beyond a grep for 'readme.md'.
- Whether docs/whats-new lacks a version_1_1_4.md page upstream as well (index.md line 46 has the subpage commented out).

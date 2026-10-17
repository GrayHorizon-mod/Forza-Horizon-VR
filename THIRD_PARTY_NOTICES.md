# Third-party notices

GrayHorizon's own code (the mods' `xinput1_3.dll` and `GrayHorizon Settings.exe`) is licensed under PolyForm Noncommercial 1.0.0 (see `LICENSE.md`). The following third-party parts keep their own licenses.

## OpenXR Loader (`openxr_loader.dll`, version 1.0.22, all three games)

Copyright (c) 2017-2020 The Khronos Group Inc. and contributors.
Licensed under the **Apache License, Version 2.0** (full text in `LICENSE-APACHE-2.0.txt`).

Source: https://github.com/KhronosGroup/OpenXR-SDK-Source

You may replace this file with any newer official OpenXR loader build.

## OpenXR headers (built into `xinput1_3.dll`, OpenXR SDK 1.1.63)

Copyright 2017-2026 The Khronos Group Inc.
SPDX-License-Identifier: Apache-2.0 OR MIT

Source: https://github.com/KhronosGroup/OpenXR-SDK

## NVIDIA DLSS (`nvngx_dlss.dll` 310.9.1 shipped with FH4; the NGX SDK library in all three mods)

These mods use NVIDIA DLSS. `nvngx_dlss.dll` is NVIDIA's runtime, redistributed unmodified under the NVIDIA RTX SDKs License, which also covers the NGX SDK library linked into each mod's DLL. FH5 and FH6 use the `nvngx_dlss.dll` that comes with the game. NVIDIA retains all rights to it; it may not be reverse engineered, modified or redistributed on its own, apart from this mod.

Copyright (c) NVIDIA Corporation. All rights reserved. NVIDIA, RTX and DLSS are trademarks and/or registered trademarks of NVIDIA Corporation in the U.S. and other countries.

SDK and license: https://github.com/NVIDIA/DLSS

## AMD FidelityFX SDK (`amd_fidelityfx_loader_dx12.dll`, `amd_fidelityfx_upscaler_dx12.dll`, FSR SDK v2.3.0, shipped with FH4)

The FH4 mod uses AMD FidelityFX Super Resolution (FSR). The two DLLs are AMD's signed runtime, redistributed unmodified in binary form under the following license. The mod's source uses the SDK's API headers.

Copyright (C) Advanced Micro Devices, Inc.
 
REDISTRIBUTION: Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to install, reproduce, copy and distribute copies of the Software, in binary form only, and to permit persons to whom the Software is provided to do the same, provided that the following conditions are met: 
 
No reverse engineering, decompilation, or disassembly of this Software is permitted. 
 
Redistributions must reproduce the above copyright notice, this permission notice, and the following disclaimers and notices in the Software documentation and/or other materials provided with the Software. 
 
DISCLAIMER: THE USE OF THE SOFTWARE IS AT YOUR SOLE RISK.  THE SOFTWARE 
IS PROVIDED "AS IS" AND WITHOUT WARRANTY OF ANY KIND AND COPYRIGHT 
HOLDER AND ITS LICENSORS EXPRESSLY DISCLAIM ALL WARRANTIES, EXPRESS AND 
IMPLIED, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF 
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NON-INFRINGEMENT. 
COPYRIGHT HOLDER AND ITS LICENSORS DO NOT WARRANT THAT THE SOFTWARE WILL 
MEET YOUR REQUIREMENTS, OR THAT THE OPERATION OF THE SOFTWARE WILL BE 
UNINTERRUPTED OR ERROR-FREE.  THE ENTIRE RISK ASSOCIATED WITH THE USE OF 
THE SOFTWARE IS ASSUMED BY YOU.  FURTHERMORE, COPYRIGHT HOLDER AND ITS 
LICENSORS DO NOT WARRANT OR MAKE ANY REPRESENTATIONS REGARDING THE USE 
OR THE RESULTS OF THE USE OF THE SOFTWARE IN TERMS OF ITS CORRECTNESS, 
ACCURACY, RELIABILITY, CURRENTNESS, OR OTHERWISE. 
 
DISCLAIMER: UNDER NO CIRCUMSTANCES INCLUDING NEGLIGENCE, SHALL COPYRIGHT HOLDER AND ITS LICENSORS OR ITS DIRECTORS, OFFICERS, EMPLOYEES OR AGENTS ("AUTHORIZED REPRESENTATIVES") BE LIABLE FOR ANY INCIDENTAL, INDIRECT, 
SPECIAL OR CONSEQUENTIAL DAMAGES (INCLUDING DAMAGES FOR LOSS OF BUSINESS 
PROFITS, BUSINESS INTERRUPTION, LOSS OF BUSINESS INFORMATION, AND THE 
LIKE) ARISING OUT OF THE USE, MISUSE OR INABILITY TO USE THE SOFTWARE, 
BREACH OR DEFAULT, INCLUDING THOSE ARISING FROM INFRINGEMENT OR ALLEGED 
INFRINGEMENT OF ANY PATENT, TRADEMARK, COPYRIGHT OR OTHER INTELLECTUAL 
PROPERTY RIGHT EVEN IF COPYRIGHT HOLDER AND ITS AUTHORIZED 
REPRESENTATIVES HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGES.  IN 
NO EVENT SHALL COPYRIGHT HOLDER OR ITS AUTHORIZED REPRESENTATIVES TOTAL 
LIABILITY FOR ALL DAMAGES, LOSSES, AND CAUSES OF ACTION (WHETHER IN 
CONTRACT, TORT (INCLUDING NEGLIGENCE) OR OTHERWISE) EXCEED THE AMOUNT OF 
US$10.

SDK: https://github.com/GPUOpen-LibrariesAndSDKs/FidelityFX-SDK

## AMD FidelityFX RCAS (the sharpening pass in all three mods)

The anti-aliasing sharpening pass is a re-implementation of the RCAS algorithm from AMD FidelityFX Super Resolution 1.0.

Copyright (c) 2021 Advanced Micro Devices, Inc. All rights reserved.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

Source: https://github.com/GPUOpen-Effects/FidelityFX-FSR

## Forza Horizon 4, 5 and 6

Forza Horizon 4, Forza Horizon 5 and Forza Horizon 6 are © Microsoft / Playground Games. GrayHorizon contains no game code or game assets. It only hooks the running game on your own PC. It is not affiliated with or endorsed by Microsoft, Playground Games, NVIDIA or AMD.

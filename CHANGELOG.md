# Changelog

## [1.3-cuda13] - 2026-03-26

### Changed
- Replaced `cudaThreadSynchronize()` with `cudaDeviceSynchronize()` (deprecated since CUDA 4, removed in CUDA 12)
- Removed `cudaThreadExit()` call (redundant with existing `cudaDeviceReset()`)
- Replaced `deviceProp.clockRate` with `cudaDeviceGetAttribute(cudaDevAttrClockRate)` (removed from `cudaDeviceProp` in CUDA 13)
- Replaced `deviceProp.kernelExecTimeoutEnabled` with `cudaDeviceGetAttribute(cudaDevAttrKernelExecTimeout)` (removed from `cudaDeviceProp` in CUDA 13)
- Replaced `_ConvertSMVer2Cores()` with inline `convertSMVer2Cores()` covering Volta through Hopper+
- Updated Makefile and shell script to target `sm_75`/`sm_80`/`sm_90` (Turing, Ampere, Hopper)
- Updated Makefile and shell script to remove CUDA SDK samples paths

### Removed
- Dependency on `helper_cuda.h` and `helper_functions.h` from CUDA SDK samples (not shipped with CUDA 13 toolkit)
- Legacy compute targets `sm_20`/`sm_30` (unsupported since CUDA 12)
- CUDA SDK samples include/library paths from build system

### Added
- Inline `checkCudaErrors()` and `getLastCudaError()` macros in `MC-GPU_v1.3.h`
- Inline `convertSMVer2Cores()` function for GPU core count estimation
- Inline `gpuGetMaxGflopsDeviceId()` function for GPU auto-selection
- CUDA 13 migration notes in source code change log
- Validation Jupyter notebook (`validation/validation.ipynb`)

### Validated
- Cross-sections match NIST XCOM database to <0.1% at 60 keV
- Primary beam attenuation matches Beer-Lambert law to 0.042% (10M histories)
- Energy conservation verified (absorbed + detected + escaped = 100%)
- Results consistent with published MC-GPU benchmarks (Fernandez Bosman et al. 2021, Massera et al. 2022, AAPM TG-195)

## [1.3] - 2012-12-12

- Original release of MC-GPU v1.3 for projection radiography and cone-beam CT
- CUDA 5 compatible
- See MC-GPU_v1.3_README.pdf for original documentation

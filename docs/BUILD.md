# Build Teraburst VR

Download the named `teraburst-vr-source.zip` release asset and extract it. The repository's automatic ZIP is the project page, not the complete engine/source delivery.

The source asset contains the host/port, `engine-source.bundle` pinned to MAME 0.289 (`f34f02505e32c1993c6a782b6814232cbfc74e36`),16 exported engine patches, vendored host headers, SDL and OpenXR source snapshots under `source-deps`, and `SOURCE-DEPENDENCIES.json` with dependency hashes. `VERSION` supplies the public software version. Read component notices in `CREDITS.md`, `licenses` and the dependency source trees.

## Tools

Use Windows with MSYS2 MinGW64 GCC/make and the MAME build dependencies, Git, Python 3.12+, CMake 3.22+ and Ninja. Quest additionally uses Android SDK platform 36.1/build-tools 36.0.0, NDK 29.0.14206865 and JDK 21. The Gradle wrapper is SHA256-pinned. Both engine and host must be rebuilt with the same native headers/ABI.

## Host checks

From a MinGW-enabled shell with its runtime DLL directory on PATH:

```powershell
cmake -S . -B build/host -G Ninja -DCMAKE_BUILD_TYPE=Release
cmake --build build/host
ctest --test-dir build/host --output-on-failure
python -B -m unittest discover -s tests -v
```

The GPU checks require a working desktop OpenGL context. Private owned-game captures are not required by the public regression suite.

## Engine and Quest

`tools/build-engine.ps1` accepts `-MsysRoot`, `-PythonPath`, `-WorkEngine`, `-Platform Windows|Android` and `-Jobs`. Android also needs `-AndroidNdk` and `-SdlRoot`. It restores the supplied bundle when needed, verifies the pinned revision, exports the native port headers and applies the engine patches. Use a dedicated short build path without spaces.

First build/install the supplied SDL source for Android ARM64 and build the supplied OpenXR Android loader. Then run `tools/build-quest.ps1` with all mandatory paths: `-MsysRoot`, `-PythonPath`, `-WorkRoot`, `-AndroidSdk`, `-JavaHome`, `-CMakePath`, `-NinjaPath`, `-SdlInstall` (the compiled ARM64 SDL install) and `-OpenXRLoader` (the compiled ARM64 loader `.so`). `-Offline` is available after Gradle's normal dependencies have been cached. The script verifies the native ARM64 DRC and signed APK.

For Windows, build the engine with `-Platform Windows` and the CMake host above. Build the supplied OpenXR SDK's Windows loader with `DYNAMIC_LOADER=ON` and `BUILD_API_LAYERS=OFF`.

`tools/package.py --help` lists required paths for the APK, Windows engine/host/loader and dependency audit. `tools/package-source.py --help` lists the pinned bundle and SDL/OpenXR source paths for the complete source delivery. The scripts use `VERSION` for local filenames. Public downloads use the stable names documented in README.

A missing local development key is generated under ignored `private/` by the Quest build script. It will not match the published app's signing identity; use your own package identity or a separate test device for independently signed builds. Release credentials are not included in source archives.

## Owned game files

The supported canonical set is `terabrst.zip` (July 17, 1998 US UEL), with 11 validated original payloads. No disk image is required. `python -B tools/game_files.py PATH/TO/terabrst.zip` verifies the actual contents; game files stay private and are never part of a source or software package.

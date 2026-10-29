# Teraburst VR v0.1.0 validation

The release preserves the physically accepted Quest 3S gameplay, then removes the temporary default FPS overlay. Existing version 5 preview settings migrate the overlay Off without changing saved world size, depth, stereo, hand layout or gun choices. Version 6 explicit diagnostic On/Off choices persist.

The user confirms that the final preview works amazingly, FPS is good, the 3D effect/scale feels right, native reticles/lasers line up, automatic recoil/haptics work and P1/P2 joining is correct. The final laser colours are native blue/P1 and red/P2. A process-attributed run measured median 72.000 XR app submissions/s against a 72 Hz target; native scene-update cadence varies with the game. Emulator-speed percentages and scene updates are distinct from headset frame pacing.

Release checks cover 29 native CTests and 8 Python tests. They exercise actual OpenGL rendering, stereo/depth, HUD independence, ray/shot alignment, reticle transparency/scale/texture reuse, gun visibility/automatic recoil, acknowledgement-driven joins, late acknowledgements, focus/tracking safety, three distinct credit pulses, saved settings/migrations, RTC and source/package rejection of game data.

Matching Quest ARM64 and Windows builds are produced from the pinned MAME 0.289 commit and 16 exported patches. Clean extracted-source tests, clean patch application, portable dependencies, APK runtime ELF identity, signing continuity, installed APK readback and release-download SHA256 are recorded for the release. No game media, extracted native weapon/reticle data, private caches or signing keys are published.

Complete routes, later bosses, every controller/runtime and physical PCVR headset play remain outside acceptance. Upstream incomplete-game/imperfect-sound flags remain. The captured world covers the original arcade camera; no hidden scenery or extra camera angle is invented.

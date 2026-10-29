# Validation - 2026-10-28

## Physical feedback

The user confirmed automatic RTC initialization, real stereo scenery, two visible working guns after explicit P2 join/menu return, and P2 remaining out until X. The latest FPS/audio optimization was physically tested and accepted as much better and good now, with some remaining room for improvement. The accepted FPS APK was2391b91273d25d335bf075f188cbdd8481697284f11f108a638108e6f83450b0. Its live session includes extended full-speed intervals; slower intervals and audio shortages remain possible.

The close stereo trial was accepted for clear depth but felt miniature. The current calibration enlarges that trial eightfold (StereoSceneScale=.8), keeps World size adjustable, scales its near plane, and preserves the native lens, independent HUD and cabinet aiming. The user now accepts the larger calibration and rifle appearance; reduced depth and a high/forward pivot prompted the current follow-up. Grip-position anchoring and separately adjustable depth are awaiting physical acceptance.

## Current software checks

All24 native CTests pass, including actual OpenGL stereo separation, centered image invariance, per-object depth, HUD independence, ray/shot alignment, close native geometry at minimum World size, native gun hot loading in both hands and menu return. Decoder tests cover bounds, unknown commands, indices, opaque payload consumption, rolling corner history, BE ROM words, rear grip and forward muzzle. Cache tests reject unknown, corrupt, truncated or extended data. Existing texture ownership, RTC, input, P2, persistence, fog and profiling regressions also pass. Python media/package/patch tests pass8/8.

A/X produce three distinct100ms coin pulses separated by releases, then Start. Production-input tests cover30/72/90/120Hz, short/held buttons, focus/menu cancellation and player isolation. Automatic P2 layouts remain session-only; explicit manual layouts persist. The exact Gun cycle is In-game3 / Arcade0 / Zapper1. Old Custom2 migrates to3; explicit0/1/3 choices persist. Settingsversion4 adds depth_strength1..2 (default1.5).

The current depth presentation keeps X/Y scale unchanged and applies diag(1,1,1/strength) to world meshes and both background paths. HUD/raster panels retain the physical eye matrix. Inverse world rays preserve native hit coordinates for cabinet projection/occlusion, and transformed hits align the physical laser. Real GPU tests verify increased separation with invariant physical height/disparity ratio, fixed HUD, both backgrounds, Original mode and close geometry at maximum strength. The tradeoff is an expanded view and compressed camera-Z dimensions.

The native rifle uses the runtime grip position with aim orientation in one combined pose for model/muzzle/game/menu rays. Physical offset logs and user feedback are still required.

## Independent separation prototype

User requests the current1.5x angular picture with the miniature trial's stronger disparity. New separation defaults1 (baseline) and supports5.25 trial. One predicted cyclopean center per frame drives physicalVP*S(C,g)*D for world/backgrounds and the identical inverse world ray for aiming. Fixed HUD/panels/guns and submitted real eye poses/FOV remain unchanged. Original native hit coordinates still govern cabinet projection and occlusion. Negative-ray intersections remain misses.

The production GPU renderer measures near disparity13.5111pixels at baseline versus69.5111 at separation5.25, close to miniature71. Centered angular height/placement stays unchanged; inferred height/disparity falls as expected. Tests cover translated/rotated heads, virtual-eye equivalence, both backgrounds, Original mode, minworld/maxdepth/gain, fixed HUD and exact both-gun images, native ray alignment and behind-ray rejection. No physical comfort or unchanged inferred scale is claimed. High gain can feel miniature and can produce apparent scene swim; default1 preserves the accepted view.

## Performance evidence

The guarded PPC idle-loop macro preserves the shared scheduler target and exact architectural phase: only complete16-cycle empty-queue/frame-ready loops are skipped, with at least48cycles retained. Code fingerprints, precise PC, live registers, TOC/stack, queue equality, IRQ/FIT/PIT and DMA checks plus a runtime phase observer reject unknown states. Rejected spin/all-budget prototypes were never enabled in an installed build.

Windows solo/P2/service/save-load comparisons match all native WAV, sampled raster and normalized scene files exactly. Matched Quest ARM64 reference/enabled tests completed90native seconds using the same library: all18 WAV/images/PPC/SHARC RAM files and logged native times/PCs match exactly. Busy-stage60-80 mean speed was96.72% versus103.95% (20 samples each), with slightly lower average enabled CPU frequencies. This headless check excludes XR and does not prove full-speed play in all scenes.

Earlier accepted changes retain exact-content texture caching,16 normalized Voodoo specializations, one native HUD draw reused for raster output, readonly ROM fast paths, four workers, profiling off by default, and capture producer storage reuse. The instruction-level68000 core change is not a bus-cycle/PCM-bit-identical claim against the original bus core.

## Native tutorial rifle

The complete owned UEL program record[0x295010,0x295288) is fingerprinted before decoding:28 packed vertices,22 UVs, six material triples and42 source faces using three materials. Every corner advances the same rolling history; opaque extra words are consumed without claiming they are normals. Authored source apertures remain open. All22 observed body/grip triangles match native captures; maximum reconstructed-camera residual is0.00480 game units. Geometric normals use two-sided lighting.

The gun is reconstructed at runtime after the game data reaches RUNNING. Native memory-region words are host-normalized; standalone ROM-file decoding uses explicit BE bytes. A startup-readiness regression prevents an early empty region from permanently rejecting the model. Three native mip images are copied once from verified body/sibling TMU blocks and checked by exact hashes before publication or private caching. The live TMU bases relocate; relative offsets remain0x800/0x900 bytes after the body. Unrelated LOD-zero artwork was identified and rejected. No extracted game geometry, pixels, ROMs or private cache is included in the APK/source archive.

Fresh60-second and cached5-second desktop integration runs both publish all42faces/three textures automatically. Strict cache hashes and logs are recorded privately.

The controller uses the rear pistol grip; the actual muzzle is at(0,.072,-.248)m before user gun scale/angle. Side/front GPU previews were inspected and an initially reversed axis was corrected before delivery. Other weapon models, including any shotgun, are not identified or automatically selected. Native visual selection does not infer accepted native shots, ammo or weapon pickups.

## Delivery and remaining acceptance

The engine is pinned MAME0.289 commit f34f02505e32c1993c6a782b6814232cbfc74e36. The exported stack now contains16 patches. Builds, archive checks, clean extracted-source tests, portable PC dependency audit and installed APK checksum are recorded in artifact-validation.json and the final delivery-check report after packaging.

Complete routes, later bosses and every physical aiming/bomb scenario remain unaccepted. Upstream MACHINE_NOT_WORKING and MACHINE_IMPERFECT_SOUND flags remain. Geometry covers the native submitted view; leaning outside it can expose gaps. Wider view is unavailable.

The accepted baseline/Original near plane stays .008m. Only active stereo gain divides it, preserving baseline depth precision; regressions cover baseline policy and an overlapping far-depth pair. Independent review reports no remaining actionable findings. Final matching Windows and Quest builds pass, and installed APK readback matches the signed build. New high-separation physical acceptance is pending. Exact package checks and hashes are recorded in artifacts/artifact-validation.json and the overseer report.

## Native reticle and laser follow-up

The user accepts depth1.75/separation1.5 as excellent. Their flat targeting bracket and unstable laser report was traced to the actual blue/red64x64 LOD2 bracket textures. Their textured triangles, including empty centers, were eligible ray targets and could feed back through the native gun coordinates. Stereo rendering and gameplay aiming now exclude only those verified decoded-content fingerprints. Flat HUD triangles no longer compete with world hits. Other artwork and LODs are retained; no extracted game pixels are distributed.

Private real-texture GPU and aiming regressions failed before the fix and pass afterward for both colors, with an unverified same-ID lookalike retained. Public scene-depth regressions cover flat HUD passthrough at the accepted calibration. Independent review caught retained gameplay DSP/lens data in service: frame selection now explicitly uses the untouched native raster whenever service controls are active. Composition regressions cover that retained-lens case, panel input, Original, gameplay and null frames. All24 native checks pass. New headset reticle/laser acceptance remains pending; the previous FPS/audio and1.75/1.5 acceptance is preserved. Exact final delivery checks are recorded outside the source archive in artifacts/artifact-validation.json and the overseer report.

## Prepared aiming, laser-tip reticle and automatic feedback

The user accepts the preceding bracket removal/3D aiming and their1.75 depth/1.5 separation calibration, but reports possible FPS loss. The active recent engine log was near99-100% native speed. New immutable-snapshot/World-size-owned AimGeometry caches native unprojection and UI classification for both tracked rays. The slow path remains the mismatch fallback. The same owned1035-triangle frame is checked ray-by-ray against the uncached result. Paired Quest CPU runs, including a cache rebuild each3rays, measure median51.3872us before and34.3027us afterward: about33.2% less picker CPU time. This is not a global game-FPS result.

The verified blue/red native images and captured quad half-span/focal ratios now feed physical laser-tip markers. GPU checks verify reference size at1.8m, approximately half angular height at3.6m, real binocular disparity, transparent centers, Laser Off and tracking loss. Images load only from owned captured data at runtime. World-space bracket filtering, unknown-art preservation and optimized aiming are checked with both actual owned textures. Original/service native rasters remain complete.

Saved dual layouts no longer assign P2 a gameplay hand until explicit P2 Start. Policy and GPU regressions cover P1-only startup, explicit P2, both native coordinate mappings, hand transitions and Solo Bomb from either hand before joining. The three-coin rising-edge protocol is preserved.

AutomaticFeedback produces bounded10Hz visual/haptic ticks only while tracked, focused gameplay delivers a held native trigger. It generates no native trigger edges, ammunition counts or timing changes. Existing30ms haptic pulses honor the haptics setting;80ms recoil recovery, flash and smoke repeat with feedback ticks. Tests cover independent players, no catch-up burst, offscreen stop/resume, focus/tracking/ownership suspension and fresh input. Actual GPU depth confirms repeated recoil without another trigger edge and return to rest on release; repeated eye draws retain effect idempotence. All26 native checks pass. Headset FPS/reticle/haptic acceptance of this new build remains pending and is recorded separately from software validation.

## Native player lifecycle and frame-pacing follow-up

The user accepts marker/recoil/haptics/3D but still reports P1/P2 issues and major FPS loss. The prior98-100% measurement was active emulator speed, not rendered headset FPS. Quest Home VrApi statistics were identified by PID and excluded from Teraburst evidence. Actual visible-app FPS remains pending.

Confidential Mission's read-only reference separates Solo Start roles, saved pair layout and acknowledged native P2 lifecycle. A reproduced Teraburst bug assigned Solo A to P2 under a saved P1-left layout. Solo now keeps A/P1 and X/P2 until native dual play; held Start ownership is preserved. New read-only native captures validate per-player phases in July UEL RAM:0out,1intro/tutorial,2play,3continue,4revive,5gameover fade. P1-only, P2-only, dual, continue/restart and137s attract runs were compared, with static game/date signature matching all24 full snapshots and fine-grained transitions catching phases4/5. The16th engine patch publishes this guarded profile through ABI0x54455203. P2 requests need native P1/both controllers; its gun waits for native acknowledgement, and hides on native continue/out. Acknowledgements take precedence over pending timeout, including delayed and tracking-change samples.

GPU regression confirmed equal immutable reticle images at different addresses caused repeated texture redefinition. Exact-content/dimension/LOD reuse now prevents those uploads with identical marker pixels. This is a verified redundant operation, not a measured explanation of the whole FPS complaint. FrameCadence reports wall-time app submissions, distinct native video updates, interval percentiles and late submission intervals; those are not compositor stale frames. Optional enumerated Meta runtime counters query app/compositor frame times and drops, at most8 per5s. All29 native tests pass. Headset FPS and new P1/P2 acceptance remain pending. Sources: local Confidential Mission host/player-assignment tests and Meta's official logcat-statistics definitions.

## Visible FPS and distinct native scene cadence

The user now accepts P1/P2 ownership, reticle, recoil/haptics and3D. The5b07b965 gameplay log records approximately72/72 XR app submissions, varying observed raster updates and generally4..8ms sampled app GPU times. This does not yet explain the perceived scene-FPS regression. The earlier accepted FPS build also has roughly244 native video advances per300 XR frames during full-speed intervals, consistent with the same72Hz submission target; no refresh-rate change has been made.

RawFrame now preserves native Voodoo buffer-swap sequence and steady-clock wall timestamp through raster composition. ABI0x54455204 matches both rebuilt engine and host. Observed source swaps, snapshots skipped between XR samples and95th-percentile scene age are distinct from native raster updates, emulation speed and compositor drops. No game timing or interpolation is changed.

A small head-relative FPS label updates once per second, showing app submissions/target FPS and observed3D source updates/s. The additive show_fps key defaults On, round-trips Off and has an actual menu toggle before Quit. One owned replaceable status texture avoids accumulating an image per changing number. GPU regressions verify visibility/Off/focus suppression,100 changing labels with one texture, unchanged service/Quit navigation and the default acknowledged left-P1/right-P2 pair. All29native tests pass; independent final review is clean and matching Windows/Quest builds pass. Headset readability and remaining scene-FPS behavior await the visible-counter playtest; no global FPS fix is claimed from adding diagnostics.

## Accepted FPS and native player colour match

The user now reports FPS is good and the mod feels much better overall on APKc0ead43a80b03e62628645ce328cb4fe7cb0d40d6e68e63514ff9924bfbe1818. The process-attributed run (PID23683) contains23five-second samples,22with calibrated game geometry. App submission median72.000Hz, range71.951..72.066Hz; observed native scene median56.462updates/s, with busy-scene dips. This is physical user acceptance plus scoped telemetry, not a promise of identical scene cadence in every route.

The user's final colour choice is to retain native blue/P1 and red/P2 brackets and swap only the gameplay laser/fallback-dot palette. The one-line tint change gives P1 blue and P2 red. Native pixels, texture reuse, ray hits, marker size, settings, menu purple, recoil, haptics and frame cadence are unchanged. The accepted FPS APK/source/PCVR archives are retained privately as rollback.

## v0.1.0 public release

The user accepts the completed mod and explicitly authorizes its GitHub page/release. Version6 settings retire the temporary preview FPS overlay to Off while retaining calibration; an explicit later diagnostic choice persists. Public README/BUILD/TESTING and attributed promotional banners replace stale development-page claims. Exact clean tests, matching builds, package/signature/readback and downloaded release hashes are recorded in the external release report.

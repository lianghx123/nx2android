# PR317: Odyssey Metro stock-driver recording

[Download or play the 30-second recording](https://raw.githubusercontent.com/lianghx123/nx2android/codex/pr317-stock-video-20261126/metro-stock-split-on.mp4).

Recorded on 2026-11-26 for [shirai91/nx2android#317](https://github.com/shirai91/nx2android/pull/317).

- Source: upstream main `2b6c4eeb92aba198dd7edb5c3526537f6110afd7` plus PR317 profile/registry configuration. Freshly rewritten modules, 27,996/27,996 freshly exported Vulkan shaders and a new host; no other unmerged PR.
- Device: Lenovo Y700 TB321FU / Snapdragon 8 Gen 3 (SM8650) / Adreno 750 / Android 16.
- Driver: stock Qualcomm 512.762.40, Vulkan 1.3.128, verified in the running app. No custom driver is packaged.
- Game: Super Mario Odyssey 1.4.1 (v393216), docked, original game graphics resources. No historical fixed-1440p patch applied.
- Controls: `DM_VK_PASS_SPLIT=256`, `DM_VK_PASS_SPLIT_DEPTH=1`; actual depth passes splitting after 256 draws are logged during the run.
- Route: player-controlled Metro streets, running/jumping near ground, walls and taxis and turning the camera. No gameplay input sent by the assistant.
- Video: 29.96 seconds, 1,820 frames, 2560x1600 screen capture. Screen dimensions do not establish internal rendering dimensions. This H.264 review copy preserves every frame and native screen dimensions; a higher-bitrate original is retained locally.
- Observations: the player reported no LRZ blocks, nearby geometry flicker/disappearance, or one-frame dark lights. The route sheet and eight strongest temporal-spike candidate triplets showed no obvious instance. The process remained unchanged and no new [RED] lines appeared during recording. The existing startup conditional-render diagnostic remains in the local complete log.
- Scope: a bounded moving-camera correctness check on this Adreno 750 stock driver, not a new performance A/B or exhaustive qualification of other GPUs/drivers.

SHA-256 of `metro-stock-split-on.mp4`: `1eac725b6722b9e1bf6993348a0d8214aac96b94ebd44e691e8f119af0d70b83`.

This separate evidence branch holds only the requested gameplay recording and its description; it is not a software release or a proposed change to the PR's code tree.

# roblox

## Client black-screen fix

The black-screen issue was caused by malformed embedded **client-side modules/scripts** inside an older place asset revision (`place 97793725257596 MMZ(1).rbxl`).
Server simulation still ran, but client startup logic failed early, leaving Roblox UI visible over an unrendered scene.

The repository default asset is now the corrected file:

- `place 97793725257596 MMZ.rbxl`

The stale `MMZ(1)` copy is not the default asset and should not be used.

## Verification steps

1. Open `place 97793725257596 MMZ.rbxl` in Roblox Studio.
2. Run **Play** / **F5**.
3. Confirm the client renders the world (not a black screen) and player/camera startup completes.
4. Open the Developer Console and verify there are no startup errors from embedded client modules/LocalScripts.

## Tooling limitations in this environment

This repository is binary-place-only and has no automated lint/test suite. Roblox client runtime verification must be performed in Roblox Studio.

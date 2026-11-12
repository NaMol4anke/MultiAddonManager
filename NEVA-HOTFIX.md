# NEVA SteamRT3 hotfix for CS2 1.41.9.7

Community hotfix, not an official MultiAddonManager release.

- Source: `Source2ZE/MultiAddonManager` commit `7fc2d6f35fe8af05511fba3d5c9d59ca06dc2391`, including the upstream Linux ReplyConnection signature fix.
- Built against SDK `81020d1a26b9d4321b9f030c96929ec18e8c0cff` from alliedmodders/s2sdk#124, addressing the network-message handle layout and lookup slots.
- Linux SteamRT3 only. The original source and contributor attribution are retained.

Both changes are required: the signature fix alone does not fix network-message handling.

## Install through NEVA Egg

Use `NaMol4anke/MultiAddonManager` release `v1.7.3-neva.2`, asset
`MultiAddonManager-v1.7.3-neva.2-steamrt3.tar.gz`. Extract into `game/csgo`.

Change the Egg MAM updater repository to `NaMol4anke/MultiAddonManager` and set
`MAM_RELEASE_TAG=v1.7.3-neva.2` in the SMS provisioning environment.
Managed SMS startup sets `RELEASE_FREEZE=1`. Keep `INSTALL_MULTIADDONMANAGER=1`
for SponsorBoards; SMS supplies the Workshop IDs through `MAM_EXTRA_ADDONS`.

## Validation and limits

Release publication requires a SteamRT3 build against the fixed SDK, expected
loader/binary paths, no package symlinks, archive checks and SHA256 checksums.
BUILD-PROVENANCE.txt records the source and dependency SHAs.
A live CS2 test with the patched CSS, NAP and actual Workshop boards is still required.

Back up existing files, version tracking and settings before installation.
If Workshop boards cannot be validated before the match, disable MAM installation
and rename `game/csgo/addons/metamod/multiaddonmanager.vdf` to `.vdf.disabled`
while the server is stopped, and remove board assignments. Changing the installer
flag alone does not unload the existing plugin. Keep the patched CSS for NAP.

Upstream references:
- https://github.com/Source2ZE/MultiAddonManager/issues/84
- https://github.com/Source2ZE/MultiAddonManager/commit/7fc2d6f35fe8af05511fba3d5c9d59ca06dc2391
- https://github.com/alliedmodders/s2sdk/pull/124
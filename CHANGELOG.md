# Changelog

## [4.0.0](https://github.com/MikeJennes/treehouse/compare/v3.1.8...v4.0.0) (2026-11-07)


### ⚠ BREAKING CHANGES

* **cmd:** `treehouse return` now exits 3, not 0, when it leaves a dirty worktree in place, and `treehouse get` does the same when its subshell exits leaving one dirty. Callers that read exit 0 as "the slot was released" were reading the bug this fixes; scripts under `set -e`, or using `treehouse return "$p" && next-step`, will now stop or branch differently at a dirty abort. Pass --force to clean and return, or treat exit 3 as "not returned".
* **cmd:** the `treehouse destroy --force` flag is removed. Replace it with the specific --include-unlanded / --include-in-use / --include-leased flag(s) for the risk you intend to override, plus --yes, and pass an explicit pool path to --all.

### Features

* add --root flag and TREEHOUSE_ROOT env for the worktree root ([#93](https://github.com/MikeJennes/treehouse/issues/93)) ([1764698](https://github.com/MikeJennes/treehouse/commit/1764698cbdb7e71c35c7dd6b991ded0e90a6c721))
* add Nix package manager install support ([#113](https://github.com/MikeJennes/treehouse/issues/113)) ([f19a652](https://github.com/MikeJennes/treehouse/commit/f19a652b6d84978dc6a4d6effaf147ae96d8edec))
* add no-fetch worktree acquisition ([d77e3f8](https://github.com/MikeJennes/treehouse/commit/d77e3f807d69b8aff4edab9fb0727b7f6e52cd5d))
* add opt-in branch creation to treehouse get ([#150](https://github.com/MikeJennes/treehouse/issues/150)) ([00819d6](https://github.com/MikeJennes/treehouse/commit/00819d6e583cf2c779a36ddc223eed64a431273e))
* add per-acquisition file seeding manifests ([#131](https://github.com/MikeJennes/treehouse/issues/131)) ([f7f8d6c](https://github.com/MikeJennes/treehouse/commit/f7f8d6c6b78d0c20d858887a369b7f29c7876c90))
* **cmd:** add global prune mode ([#26](https://github.com/MikeJennes/treehouse/issues/26)) ([103e21a](https://github.com/MikeJennes/treehouse/commit/103e21a0e85e320d4fad22eca45453fb95bf1b31))
* **cmd:** make destroy safe by default ([#37](https://github.com/MikeJennes/treehouse/issues/37)) ([be45d40](https://github.com/MikeJennes/treehouse/commit/be45d40ad0a42f0d5b3ae939673d82393db7694b))
* **cmd:** report checked-out branches in status ([#134](https://github.com/MikeJennes/treehouse/issues/134)) ([ad740a1](https://github.com/MikeJennes/treehouse/commit/ad740a1ccbe4fbd3b9573204fe891e6088837b6d))
* **cmd:** return a worktree by name and add return --all ([#143](https://github.com/MikeJennes/treehouse/issues/143)) ([2b86f48](https://github.com/MikeJennes/treehouse/commit/2b86f48bb8eed14919e0ddef720bab8edcd60c46))
* **config:** add configurable root for pool directory ([#12](https://github.com/MikeJennes/treehouse/issues/12)) ([7fae82a](https://github.com/MikeJennes/treehouse/commit/7fae82a0b546fdebf19fec02052e3761015c3fe1))
* **fileclone:** add opt-in APFS sharing for fresh Git worktrees ([#153](https://github.com/MikeJennes/treehouse/issues/153)) ([ae70188](https://github.com/MikeJennes/treehouse/commit/ae70188324a86c930e4a4a3b2860fa73ec548d11))
* initial project setup ([e253955](https://github.com/MikeJennes/treehouse/commit/e253955cda6e3634a6891dfe889278da2c125114))
* **nix:** add flake.nix and flake.lock ([#15](https://github.com/MikeJennes/treehouse/issues/15)) ([6b0ea8d](https://github.com/MikeJennes/treehouse/commit/6b0ea8da487adb324464d69da5b84a4e9dd109a4))
* **pool:** add durable worktree leases ([#35](https://github.com/MikeJennes/treehouse/issues/35)) ([749054c](https://github.com/MikeJennes/treehouse/commit/749054cb3636156811047a230c6d0ee5a43b2179))
* **pool:** add lease command to durably lease an existing worktree ([#128](https://github.com/MikeJennes/treehouse/issues/128)) ([5932367](https://github.com/MikeJennes/treehouse/commit/59323676a8fdb630f6b8e98f07465203b617a78c))
* **pool:** add stable lease identities ([#68](https://github.com/MikeJennes/treehouse/issues/68)) ([ba6adcb](https://github.com/MikeJennes/treehouse/commit/ba6adcb2f307a4904b64a14824b3ed1019c9926d))
* **pool:** add user lifecycle hooks ([#22](https://github.com/MikeJennes/treehouse/issues/22)) ([388252d](https://github.com/MikeJennes/treehouse/commit/388252d9e71805d21ab8b97e1fb5b3d86c4d2e88))
* **pool:** automatically free safe recovered slots ([#159](https://github.com/MikeJennes/treehouse/issues/159)) ([e0fef0a](https://github.com/MikeJennes/treehouse/commit/e0fef0ade3e9963c540bfbe4515f1f551aaed1e6))
* **pool:** classify orphaned worktrees during prune ([#28](https://github.com/MikeJennes/treehouse/issues/28)) ([424e055](https://github.com/MikeJennes/treehouse/commit/424e05588de092ab3c4ec21f4b7f8f8e999feb74))
* **pool:** make where a new pool worktree is placed configurable ([#140](https://github.com/MikeJennes/treehouse/issues/140)) ([5e3d185](https://github.com/MikeJennes/treehouse/commit/5e3d185fd2e9456013e15d3f6efbef345ba29925))
* **pool:** opt-in unique worktree directory names for get ([#126](https://github.com/MikeJennes/treehouse/issues/126)) ([363e12f](https://github.com/MikeJennes/treehouse/commit/363e12ffc96972720ce8db6006cba380b8011157))
* **pool:** seed ignored files from .worktreeinclude ([#129](https://github.com/MikeJennes/treehouse/issues/129)) ([fa1f9a6](https://github.com/MikeJennes/treehouse/commit/fa1f9a625b603a68896fb6c7eb948b77425d8730))
* **pool:** support configurable base branch for get ([#119](https://github.com/MikeJennes/treehouse/issues/119)) ([2ccd9df](https://github.com/MikeJennes/treehouse/commit/2ccd9df2ee9c360d3668a16506c564b909752638))
* **prune:** add safe stale worktree pruning ([#24](https://github.com/MikeJennes/treehouse/issues/24)) ([829f25a](https://github.com/MikeJennes/treehouse/commit/829f25a36cac61fd7060bfce12056e3359f8ea09))
* **status:** show current worktree status ([e92c8a7](https://github.com/MikeJennes/treehouse/commit/e92c8a7e7b75084c477b932f9f9685e2ecfbc202))
* use latest default branch for worktree ([9d68410](https://github.com/MikeJennes/treehouse/commit/9d68410d9e7449bf7ca9a605f6e805fc11de93c8))
* **vcs:** add opt-in Jujutsu (jj) workspace backend behind a VCS seam ([#100](https://github.com/MikeJennes/treehouse/issues/100)) ([4319915](https://github.com/MikeJennes/treehouse/commit/4319915adf194b48994b223200f80cd9c456cdbe))
* **vcs:** slot-flavor dispatch, flavor-aware acquire, and markerless fail-closed hardening ([#110](https://github.com/MikeJennes/treehouse/issues/110)) ([c464682](https://github.com/MikeJennes/treehouse/commit/c464682ca39fbadb60b4612fa735f9b528cf42a3))


### Bug Fixes

* add /v3 major version suffix to module path ([#167](https://github.com/MikeJennes/treehouse/issues/167)) ([3765505](https://github.com/MikeJennes/treehouse/commit/37655058d3be0a40866cb2ba01486c22cad3d44b))
* app update permission error ([cbf6fe9](https://github.com/MikeJennes/treehouse/commit/cbf6fe9a96e3a13a1c6e417bdb875537868c9702))
* CI failures ([f580e02](https://github.com/MikeJennes/treehouse/commit/f580e02fa9ce87ca0346c20645e5131e2d146bfd))
* **ci:** make update-vendor-hash fork-aware for checkout and push ([#105](https://github.com/MikeJennes/treehouse/issues/105)) ([b87fb0d](https://github.com/MikeJennes/treehouse/commit/b87fb0d559e981ccb78a57b2f9b1e77dc866c4dd))
* **ci:** suppress pull_request runs on release-please PRs ([#77](https://github.com/MikeJennes/treehouse/issues/77)) ([cee8600](https://github.com/MikeJennes/treehouse/commit/cee86003b04b46436857927137c89331b1ef563a))
* **cli:** expose version flag and set rootCmd.Version ([238d63f](https://github.com/MikeJennes/treehouse/commit/238d63ff49536d2b7256d3a66a6d71db1f99ba4f))
* **cmd:** detach worktrees before pool reuse ([#19](https://github.com/MikeJennes/treehouse/issues/19)) ([14d5fd7](https://github.com/MikeJennes/treehouse/commit/14d5fd725203af3465e8045e7e7c25346452c8ed))
* **cmd:** exit non-zero when a dirty worktree is not returned ([#138](https://github.com/MikeJennes/treehouse/issues/138)) ([1ef79fb](https://github.com/MikeJennes/treehouse/commit/1ef79fbbc23c4d0375d57a94ef0b0309a681ad63))
* **cmd:** paste-safe dirty non-TTY return --force hints ([#122](https://github.com/MikeJennes/treehouse/issues/122)) ([4738d5a](https://github.com/MikeJennes/treehouse/commit/4738d5abe2325cf56b87a530d29782a4fdab3d8e))
* **cmd:** resolve main repo root for pool commands run inside a worktree ([#51](https://github.com/MikeJennes/treehouse/issues/51)) ([8c8bf8f](https://github.com/MikeJennes/treehouse/commit/8c8bf8f340bba75cc5c1527e8420c6eea9340ceb))
* **config:** warn when repository hooks are ignored ([#141](https://github.com/MikeJennes/treehouse/issues/141)) ([178b244](https://github.com/MikeJennes/treehouse/commit/178b244a0742591537dd3f5a1d22df43864f36c1))
* detect squash-merged worktrees ([#88](https://github.com/MikeJennes/treehouse/issues/88)) ([4785c18](https://github.com/MikeJennes/treehouse/commit/4785c18d419c0b4b78937fee21a3014cf56e96bb))
* **get:** skip reclaiming a pool slot that holds unlanded work ([#104](https://github.com/MikeJennes/treehouse/issues/104)) ([be71725](https://github.com/MikeJennes/treehouse/commit/be717257be7f075b44bf9383303c30aada44f47d))
* ignore in-project pool via .git/info/exclude ([e2e3689](https://github.com/MikeJennes/treehouse/commit/e2e3689aec660ea85705dcba121692feb23f8ac5))
* install under ~/.local/bin when in PATH ([9586e78](https://github.com/MikeJennes/treehouse/commit/9586e78db4c312b507f0e47bfe77ad2a504d5843))
* **installer:** resolve latest release without GitHub API ([#197](https://github.com/MikeJennes/treehouse/issues/197)) ([c084a5f](https://github.com/MikeJennes/treehouse/commit/c084a5f6434608d02824b55c7d28d620dacdb3ce))
* **nix:** drop x86_64-darwin and update flake.lock ([#182](https://github.com/MikeJennes/treehouse/issues/182)) ([8a1bdc4](https://github.com/MikeJennes/treehouse/commit/8a1bdc4275a6ccda7aa3256d1e2f0bfc53bc709b))
* pin nix-build to flake-locked nixpkgs and extract package.nix ([#135](https://github.com/MikeJennes/treehouse/issues/135)) ([5a3cead](https://github.com/MikeJennes/treehouse/commit/5a3cead3f48a3d3f45ea042a5535a1050842b646))
* **pool:** adopt pre-3.0 state instead of quarantining it as recovered ([#156](https://github.com/MikeJennes/treehouse/issues/156)) ([da962d7](https://github.com/MikeJennes/treehouse/commit/da962d74c970cd5026f07aa552a2797afa90b363))
* **pool:** guard against invalid worktree registrations ([#200](https://github.com/MikeJennes/treehouse/issues/200)) ([77305c6](https://github.com/MikeJennes/treehouse/commit/77305c6753ac92b049bc1d6902d05742605c8961))
* **pool:** let prune and destroy reclaim worktrees from other clones in a shared pool ([#146](https://github.com/MikeJennes/treehouse/issues/146)) ([32bd5c3](https://github.com/MikeJennes/treehouse/commit/32bd5c3874149550fe25176851ca6a320aec795e))
* **pool:** make state persistence atomic and recoverable ([#55](https://github.com/MikeJennes/treehouse/issues/55)) ([eb81461](https://github.com/MikeJennes/treehouse/commit/eb814618cc8b1ae2c22f94b15b4aa4a25f036aab))
* **pool:** preserve worktree identity across symlinked pool paths ([#208](https://github.com/MikeJennes/treehouse/issues/208)) ([6652741](https://github.com/MikeJennes/treehouse/commit/665274165fa33f21374f9610efb49e2e025fea04))
* **pool:** prune stale worktree registrations before adding in get ([8f2c575](https://github.com/MikeJennes/treehouse/commit/8f2c575b6dabd3dbb127c6415d800d475973f90b)), closes [#31](https://github.com/MikeJennes/treehouse/issues/31)
* **pool:** reclaim empty leftover slot directories on get ([#186](https://github.com/MikeJennes/treehouse/issues/186)) ([cd4aa64](https://github.com/MikeJennes/treehouse/commit/cd4aa6408e19e5c08f67ddc2e2e653f4614af012))
* **pool:** report only the processes return would terminate in status ([#139](https://github.com/MikeJennes/treehouse/issues/139)) ([013b4d9](https://github.com/MikeJennes/treehouse/commit/013b4d9d44f485ed4e94ebb47dc1d0d064425be8))
* **pool:** reuse a pooled worktree only for the clone that owns it ([#145](https://github.com/MikeJennes/treehouse/issues/145)) ([3a634d8](https://github.com/MikeJennes/treehouse/commit/3a634d88cf1c39d401e048a143706db6327f3aa1))
* **pool:** stop get from deregistering live slots it cannot see ([#198](https://github.com/MikeJennes/treehouse/issues/198)) ([72fa18d](https://github.com/MikeJennes/treehouse/commit/72fa18d1fd2566369ef8ea5cf4fed0fcf3b57046)), closes [#194](https://github.com/MikeJennes/treehouse/issues/194)
* **process:** safely clean up lingering worktree processes ([#17](https://github.com/MikeJennes/treehouse/issues/17)) ([a0c0a33](https://github.com/MikeJennes/treehouse/commit/a0c0a33cf55c8ba1fa1b1ccd96814de4ccf6031f))
* **process:** wait for SIGKILLed processes to be reaped before return runs git ([#102](https://github.com/MikeJennes/treehouse/issues/102)) ([431bc3a](https://github.com/MikeJennes/treehouse/commit/431bc3afce43fb55526bfa7271e520e343195aee))
* recheck app update when cached version is stale ([db62bf7](https://github.com/MikeJennes/treehouse/commit/db62bf77578c772bef7dc1a7e9ef22fea7a99ed0))
* **return:** refuse to reset a worktree that still has live writers ([#103](https://github.com/MikeJennes/treehouse/issues/103)) ([78f01e8](https://github.com/MikeJennes/treehouse/commit/78f01e83248576e3ef8baf290f344b5455a47d9d))
* **shell:** start supported user shells as interactive login sessions ([#120](https://github.com/MikeJennes/treehouse/issues/120)) ([f911063](https://github.com/MikeJennes/treehouse/commit/f911063f0832747cd5e277b52f91da26ee00b380))
* shorter version display ([416efb5](https://github.com/MikeJennes/treehouse/commit/416efb57bc0d462a265b38de312586d4117a374e))
* update repository URLs ([f2350c4](https://github.com/MikeJennes/treehouse/commit/f2350c46847f68588d893c89db149d022f1cb765))
* update vendor hash handling in workflow ([1e3234d](https://github.com/MikeJennes/treehouse/commit/1e3234d0422d3a7552b5d89cfd5ca7154c543ddf))
* **update:** refuse self-update and silence the notice in the Nix store ([#180](https://github.com/MikeJennes/treehouse/issues/180)) ([9a68c93](https://github.com/MikeJennes/treehouse/commit/9a68c93186fa6c0f1b10349939b8da6105a41369))
* **updater:** replace a running Windows exe without a fixed .old backup ([#121](https://github.com/MikeJennes/treehouse/issues/121)) ([e75f606](https://github.com/MikeJennes/treehouse/commit/e75f6060999a5a5942dd2934a525003ecf0d6f95))
* use remote URL for pool hash for local repos ([ee5ce7c](https://github.com/MikeJennes/treehouse/commit/ee5ce7c8b50fea61655029352bdc487689933b9e))
* **vcs:** check recovered HEAD containment with a single rev-list walk ([#164](https://github.com/MikeJennes/treehouse/issues/164)) ([1107db4](https://github.com/MikeJennes/treehouse/commit/1107db40b1b12ec703a60657822194e5de3c2fb3))
* **vcs:** move HEAD through a git transaction on reftable repositories ([#175](https://github.com/MikeJennes/treehouse/issues/175)) ([f4ea002](https://github.com/MikeJennes/treehouse/commit/f4ea0028290d17e44f6d351e55954d7afe368f90)), closes [#174](https://github.com/MikeJennes/treehouse/issues/174)
* **vcs:** pin submodule.recurse=false in git runners ([#177](https://github.com/MikeJennes/treehouse/issues/177)) ([300ea4c](https://github.com/MikeJennes/treehouse/commit/300ea4c862be51ca66b649e29fb7b9c7931acaf7))
* **vcs:** recover stale HEAD.lock left by interrupted worktree reset ([#178](https://github.com/MikeJennes/treehouse/issues/178)) ([eedfddf](https://github.com/MikeJennes/treehouse/commit/eedfddf35896dbdd7c262bf599099ee6fada4e6b))
* windows test failure ([7ab0903](https://github.com/MikeJennes/treehouse/commit/7ab0903adae85567f154f7334d4ecbb7df8a5f73))

## [3.1.8](https://github.com/kunchenguid/treehouse/compare/v3.1.7...v3.1.8) (2026-10-30)


### Bug Fixes

* **pool:** guard against invalid worktree registrations ([#200](https://github.com/kunchenguid/treehouse/issues/200)) ([bf61797](https://github.com/kunchenguid/treehouse/commit/bf61797bb80a0b1169dbb736e43111181a7ef472))
* **vcs:** recover stale HEAD.lock left by interrupted worktree reset ([#178](https://github.com/kunchenguid/treehouse/issues/178)) ([986b4b7](https://github.com/kunchenguid/treehouse/commit/986b4b735fd9c20b02dc9ab48311a79344247943))

## [3.1.7](https://github.com/kunchenguid/treehouse/compare/v3.1.6...v3.1.7) (2026-10-26)


### Bug Fixes

* **installer:** resolve latest release without GitHub API ([#197](https://github.com/kunchenguid/treehouse/issues/197)) ([7372295](https://github.com/kunchenguid/treehouse/commit/73722955948dd402e0245b65dd9e5418b7970112))
* **pool:** stop get from deregistering live slots it cannot see ([#198](https://github.com/kunchenguid/treehouse/issues/198)) ([4acb9e4](https://github.com/kunchenguid/treehouse/commit/4acb9e4bc1d78d9aeb69358cd5ff7d1b375a3a1f)), closes [#194](https://github.com/kunchenguid/treehouse/issues/194)

## [3.1.6](https://github.com/kunchenguid/treehouse/compare/v3.1.5...v3.1.6) (2026-10-24)


### Bug Fixes

* **vcs:** move HEAD through a git transaction on reftable repositories ([#175](https://github.com/kunchenguid/treehouse/issues/175)) ([f389758](https://github.com/kunchenguid/treehouse/commit/f389758894dc2480801f3151ac272e8a3b7920e1)), closes [#174](https://github.com/kunchenguid/treehouse/issues/174)

## [3.1.5](https://github.com/kunchenguid/treehouse/compare/v3.1.4...v3.1.5) (2026-10-20)


### Bug Fixes

* **pool:** reclaim empty leftover slot directories on get ([#186](https://github.com/kunchenguid/treehouse/issues/186)) ([03c12c2](https://github.com/kunchenguid/treehouse/commit/03c12c2847f2fa347e98e0a2e382fbde40a60da0))

## [3.1.4](https://github.com/kunchenguid/treehouse/compare/v3.1.3...v3.1.4) (2026-10-15)


### Bug Fixes

* **nix:** drop x86_64-darwin and update flake.lock ([#182](https://github.com/kunchenguid/treehouse/issues/182)) ([2a93409](https://github.com/kunchenguid/treehouse/commit/2a934095cc791845f4b689ce9a5379df6d20df39))
* **update:** refuse self-update and silence the notice in the Nix store ([#180](https://github.com/kunchenguid/treehouse/issues/180)) ([93a18da](https://github.com/kunchenguid/treehouse/commit/93a18dabcf5ad46bf243492912865d65ef0977dd))

## [3.1.3](https://github.com/kunchenguid/treehouse/compare/v3.1.2...v3.1.3) (2026-10-12)


### Bug Fixes

* **vcs:** pin submodule.recurse=false in git runners ([#177](https://github.com/kunchenguid/treehouse/issues/177)) ([d40678e](https://github.com/kunchenguid/treehouse/commit/d40678e3b88ac638c4c05ccdfd96082c1aa1648a))

## [3.1.2](https://github.com/kunchenguid/treehouse/compare/v3.1.1...v3.1.2) (2026-10-02)


### Bug Fixes

* add /v3 major version suffix to module path ([#167](https://github.com/kunchenguid/treehouse/issues/167)) ([2b481be](https://github.com/kunchenguid/treehouse/commit/2b481beda1bac61669b6435ac8cae2f58be5f36e))

## [3.1.1](https://github.com/kunchenguid/treehouse/compare/v3.1.0...v3.1.1) (2026-09-30)


### Bug Fixes

* **vcs:** check recovered HEAD containment with a single rev-list walk ([#164](https://github.com/kunchenguid/treehouse/issues/164)) ([cb7fb26](https://github.com/kunchenguid/treehouse/commit/cb7fb264d138da9e6f0234d7e19aa42239413268))

## [3.1.0](https://github.com/kunchenguid/treehouse/compare/v3.0.1...v3.1.0) (2026-09-26)


### Features

* **pool:** automatically free safe recovered slots ([#159](https://github.com/kunchenguid/treehouse/issues/159)) ([d1f9167](https://github.com/kunchenguid/treehouse/commit/d1f91675d956e8619d45b102c209fe3e612c007a))

## [3.0.1](https://github.com/kunchenguid/treehouse/compare/v3.0.0...v3.0.1) (2026-09-26)


### Bug Fixes

* **pool:** adopt pre-3.0 state instead of quarantining it as recovered ([#156](https://github.com/kunchenguid/treehouse/issues/156)) ([706ae59](https://github.com/kunchenguid/treehouse/commit/706ae5932b13a355db5698486042f0b897eea247))

## [3.0.0](https://github.com/kunchenguid/treehouse/compare/v2.3.0...v3.0.0) (2026-09-25)


### ⚠ BREAKING CHANGES

* **cmd:** `treehouse return` now exits 3, not 0, when it leaves a dirty worktree in place, and `treehouse get` does the same when its subshell exits leaving one dirty. Callers that read exit 0 as "the slot was released" were reading the bug this fixes; scripts under `set -e`, or using `treehouse return "$p" && next-step`, will now stop or branch differently at a dirty abort. Pass --force to clean and return, or treat exit 3 as "not returned".

### Features

* add Nix package manager install support ([#113](https://github.com/kunchenguid/treehouse/issues/113)) ([4307a30](https://github.com/kunchenguid/treehouse/commit/4307a30f6d18457200dbd15954a56d75749454b8))
* add opt-in branch creation to treehouse get ([#150](https://github.com/kunchenguid/treehouse/issues/150)) ([e4f59d1](https://github.com/kunchenguid/treehouse/commit/e4f59d10b872eb8d191ef16ccfb073b505a262e2))
* add per-acquisition file seeding manifests ([#131](https://github.com/kunchenguid/treehouse/issues/131)) ([67c9f2f](https://github.com/kunchenguid/treehouse/commit/67c9f2fd5e662321b3481255ffa633540d5d793e))
* **cmd:** report checked-out branches in status ([#134](https://github.com/kunchenguid/treehouse/issues/134)) ([ee8652b](https://github.com/kunchenguid/treehouse/commit/ee8652b8464ae1d673053a627e7dad75ac2f3406))
* **cmd:** return a worktree by name and add return --all ([#143](https://github.com/kunchenguid/treehouse/issues/143)) ([99f4db2](https://github.com/kunchenguid/treehouse/commit/99f4db2bbeececc1e6f136a88f79002e5a707174))
* **fileclone:** add opt-in APFS sharing for fresh Git worktrees ([#153](https://github.com/kunchenguid/treehouse/issues/153)) ([438e9c1](https://github.com/kunchenguid/treehouse/commit/438e9c17d29632dd2c17765225c11de1086d6aad))
* **pool:** add lease command to durably lease an existing worktree ([#128](https://github.com/kunchenguid/treehouse/issues/128)) ([b227e59](https://github.com/kunchenguid/treehouse/commit/b227e59cf73fd15d69f00b580da0f5bee6b38fce))
* **pool:** make where a new pool worktree is placed configurable ([#140](https://github.com/kunchenguid/treehouse/issues/140)) ([6d33753](https://github.com/kunchenguid/treehouse/commit/6d33753e94ac3ddf08d7953f3e200ba9bb8b00d5))
* **pool:** opt-in unique worktree directory names for get ([#126](https://github.com/kunchenguid/treehouse/issues/126)) ([cee9ea1](https://github.com/kunchenguid/treehouse/commit/cee9ea11337afea0e5e1431317b81200d4e8bd18))
* **pool:** seed ignored files from .worktreeinclude ([#129](https://github.com/kunchenguid/treehouse/issues/129)) ([0e87c62](https://github.com/kunchenguid/treehouse/commit/0e87c62b0494fd08bc5df230797cfb44a10dd814))
* **pool:** support configurable base branch for get ([#119](https://github.com/kunchenguid/treehouse/issues/119)) ([c98e9de](https://github.com/kunchenguid/treehouse/commit/c98e9de0a8ad85d9551ccce85ecd96c8b9a8dff5))


### Bug Fixes

* **cmd:** exit non-zero when a dirty worktree is not returned ([#138](https://github.com/kunchenguid/treehouse/issues/138)) ([e57daab](https://github.com/kunchenguid/treehouse/commit/e57daab3e0c038750d251c779d1c3e294156fa7f))
* **cmd:** paste-safe dirty non-TTY return --force hints ([#122](https://github.com/kunchenguid/treehouse/issues/122)) ([59762c9](https://github.com/kunchenguid/treehouse/commit/59762c9dd545cca29517e6b7333ec5a23e67ee85))
* **config:** warn when repository hooks are ignored ([#141](https://github.com/kunchenguid/treehouse/issues/141)) ([8e3ceff](https://github.com/kunchenguid/treehouse/commit/8e3ceffb090d335ea459fa5bd53754ac3a87b6b4))
* pin nix-build to flake-locked nixpkgs and extract package.nix ([#135](https://github.com/kunchenguid/treehouse/issues/135)) ([30723fc](https://github.com/kunchenguid/treehouse/commit/30723fc0baa2ce05969c96dd245a163333945596))
* **pool:** let prune and destroy reclaim worktrees from other clones in a shared pool ([#146](https://github.com/kunchenguid/treehouse/issues/146)) ([94c092f](https://github.com/kunchenguid/treehouse/commit/94c092f511259c21dffb7466feb9048e29913176))
* **pool:** report only the processes return would terminate in status ([#139](https://github.com/kunchenguid/treehouse/issues/139)) ([af57b33](https://github.com/kunchenguid/treehouse/commit/af57b33ff8a80b3b1b476b3f060677a3271201a5))
* **pool:** reuse a pooled worktree only for the clone that owns it ([#145](https://github.com/kunchenguid/treehouse/issues/145)) ([1185dc6](https://github.com/kunchenguid/treehouse/commit/1185dc6cc50e1b66ef5c74b8ac677a6251258abc))
* **shell:** start supported user shells as interactive login sessions ([#120](https://github.com/kunchenguid/treehouse/issues/120)) ([db06078](https://github.com/kunchenguid/treehouse/commit/db06078c6f5569e539b8cdb7703f38fdefe06382))
* **updater:** replace a running Windows exe without a fixed .old backup ([#121](https://github.com/kunchenguid/treehouse/issues/121)) ([bdbd0f8](https://github.com/kunchenguid/treehouse/commit/bdbd0f89164ba87cda5d48b53dfb3e04836dc6f7))

## [2.3.0](https://github.com/kunchenguid/treehouse/compare/v2.2.1...v2.3.0) (2026-08-21)


### Features

* **vcs:** add opt-in Jujutsu (jj) workspace backend behind a VCS seam ([#100](https://github.com/kunchenguid/treehouse/issues/100)) ([a2e554c](https://github.com/kunchenguid/treehouse/commit/a2e554c15e0c8de0e8cbc0e45549acc59f6b97f9))
* **vcs:** slot-flavor dispatch, flavor-aware acquire, and markerless fail-closed hardening ([#110](https://github.com/kunchenguid/treehouse/issues/110)) ([c88b53e](https://github.com/kunchenguid/treehouse/commit/c88b53ef6149054435fd375806117dfcd8371a0d))


### Bug Fixes

* **ci:** make update-vendor-hash fork-aware for checkout and push ([#105](https://github.com/kunchenguid/treehouse/issues/105)) ([6c40205](https://github.com/kunchenguid/treehouse/commit/6c40205c69855998ed2fac19d3c75751b504243a))
* **get:** skip reclaiming a pool slot that holds unlanded work ([#104](https://github.com/kunchenguid/treehouse/issues/104)) ([04d8725](https://github.com/kunchenguid/treehouse/commit/04d87252f918dc3942318817b74413bf55f5b3eb))
* **process:** wait for SIGKILLed processes to be reaped before return runs git ([#102](https://github.com/kunchenguid/treehouse/issues/102)) ([664adf8](https://github.com/kunchenguid/treehouse/commit/664adf81e4a427080449aa8e4b76b53cc54f8a24))

## [2.2.1](https://github.com/kunchenguid/treehouse/compare/v2.2.0...v2.2.1) (2026-08-21)


### Bug Fixes

* **return:** refuse to reset a worktree that still has live writers ([#103](https://github.com/kunchenguid/treehouse/issues/103)) ([978da87](https://github.com/kunchenguid/treehouse/commit/978da8750da4f6faebbef90ccdb23aaac6211118))

## [2.2.0](https://github.com/kunchenguid/treehouse/compare/v2.1.1...v2.2.0) (2026-08-19)


### Features

* add --root flag and TREEHOUSE_ROOT env for the worktree root ([#93](https://github.com/kunchenguid/treehouse/issues/93)) ([5e3d282](https://github.com/kunchenguid/treehouse/commit/5e3d282592dfef5e60a5027797aa917f08c6cbf0))
* add no-fetch worktree acquisition ([164d903](https://github.com/kunchenguid/treehouse/commit/164d9036569a406d664f988f064c6a58eea1a645))


### Bug Fixes

* **cmd:** resolve main repo root for pool commands run inside a worktree ([#51](https://github.com/kunchenguid/treehouse/issues/51)) ([3fcd637](https://github.com/kunchenguid/treehouse/commit/3fcd63771a6368fa357a9a4079a9b6e242202dcb))
* detect squash-merged worktrees ([#88](https://github.com/kunchenguid/treehouse/issues/88)) ([a651776](https://github.com/kunchenguid/treehouse/commit/a651776a47a2911d260c55472ccdfc5f6a3aeaf8))
* ignore in-project pool via .git/info/exclude ([fdb3f99](https://github.com/kunchenguid/treehouse/commit/fdb3f99ba1c7c6d24db7efbcbb569a61f6535489))
* **pool:** prune stale worktree registrations before adding in get ([844acc4](https://github.com/kunchenguid/treehouse/commit/844acc4d1d7d8078f1110295689d94853a921dd7)), closes [#31](https://github.com/kunchenguid/treehouse/issues/31)

## [2.1.1](https://github.com/kunchenguid/treehouse/compare/v2.1.0...v2.1.1) (2026-07-31)


### Bug Fixes

* **ci:** suppress pull_request runs on release-please PRs ([#77](https://github.com/kunchenguid/treehouse/issues/77)) ([da7eda2](https://github.com/kunchenguid/treehouse/commit/da7eda26e5f26e0a1bf87a0d67e7553d72952cdf))

## [2.1.0](https://github.com/kunchenguid/treehouse/compare/v2.0.1...v2.1.0) (2026-07-20)


### Features

* **pool:** add stable lease identities ([#68](https://github.com/kunchenguid/treehouse/issues/68)) ([e914cca](https://github.com/kunchenguid/treehouse/commit/e914cca93693be4c47e0a4df1bf7439afd5e820a))

## [2.0.1](https://github.com/kunchenguid/treehouse/compare/v2.0.0...v2.0.1) (2026-07-14)


### Bug Fixes

* **pool:** make state persistence atomic and recoverable ([#55](https://github.com/kunchenguid/treehouse/issues/55)) ([c76015d](https://github.com/kunchenguid/treehouse/commit/c76015d914e8ae7068c024c68c58860e10e8ee52))

## [2.0.0](https://github.com/kunchenguid/treehouse/compare/v1.8.0...v2.0.0) (2026-06-24)


### ⚠ BREAKING CHANGES

* **cmd:** the `treehouse destroy --force` flag is removed. Replace it with the specific --include-unlanded / --include-in-use / --include-leased flag(s) for the risk you intend to override, plus --yes, and pass an explicit pool path to --all.

### Features

* **cmd:** make destroy safe by default ([#37](https://github.com/kunchenguid/treehouse/issues/37)) ([0190382](https://github.com/kunchenguid/treehouse/commit/0190382c6f3b95025667b5b01e688e779bf3c516))

## [1.8.0](https://github.com/kunchenguid/treehouse/compare/v1.7.0...v1.8.0) (2026-06-22)


### Features

* **pool:** add durable worktree leases ([#35](https://github.com/kunchenguid/treehouse/issues/35)) ([97d6708](https://github.com/kunchenguid/treehouse/commit/97d67089ea55cba166c3f4d5332e9a7a09206057))

## [1.7.0](https://github.com/kunchenguid/treehouse/compare/v1.6.0...v1.7.0) (2026-06-20)


### Features

* **pool:** classify orphaned worktrees during prune ([#28](https://github.com/kunchenguid/treehouse/issues/28)) ([836044f](https://github.com/kunchenguid/treehouse/commit/836044f85e992d2fd65969dca387704998c144b6))

## [1.6.0](https://github.com/kunchenguid/treehouse/compare/v1.5.0...v1.6.0) (2026-06-20)


### Features

* **cmd:** add global prune mode ([#26](https://github.com/kunchenguid/treehouse/issues/26)) ([6de3a91](https://github.com/kunchenguid/treehouse/commit/6de3a9150453cc5cf5fb4e95627788551adae66c))

## [1.5.0](https://github.com/kunchenguid/treehouse/compare/v1.4.0...v1.5.0) (2026-06-19)


### Features

* **prune:** add safe stale worktree pruning ([#24](https://github.com/kunchenguid/treehouse/issues/24)) ([3395c20](https://github.com/kunchenguid/treehouse/commit/3395c20e41dbb563e3437c4a0a5e031ce042ca2a))

## [1.4.0](https://github.com/kunchenguid/treehouse/compare/v1.3.2...v1.4.0) (2026-05-15)


### Features

* **pool:** add user lifecycle hooks ([#22](https://github.com/kunchenguid/treehouse/issues/22)) ([9c70d0b](https://github.com/kunchenguid/treehouse/commit/9c70d0b73c6ca1c1783828f3e9d215612993a3b4))

## [1.3.2](https://github.com/kunchenguid/treehouse/compare/v1.3.1...v1.3.2) (2026-05-02)


### Bug Fixes

* **cmd:** detach worktrees before pool reuse ([#19](https://github.com/kunchenguid/treehouse/issues/19)) ([0d849a3](https://github.com/kunchenguid/treehouse/commit/0d849a3b82a8647f507b1e2f186dc041c930fe35))

## [1.3.1](https://github.com/kunchenguid/treehouse/compare/v1.3.0...v1.3.1) (2026-04-16)


### Bug Fixes

* **process:** safely clean up lingering worktree processes ([#17](https://github.com/kunchenguid/treehouse/issues/17)) ([c1e443d](https://github.com/kunchenguid/treehouse/commit/c1e443de639d3bf5a867e71f218153c4816c78ef))

## [1.3.0](https://github.com/kunchenguid/treehouse/compare/v1.2.1...v1.3.0) (2026-04-04)


### Features

* **nix:** add flake.nix and flake.lock ([#15](https://github.com/kunchenguid/treehouse/issues/15)) ([500d2f9](https://github.com/kunchenguid/treehouse/commit/500d2f9e26429d02e8378142556af8ad9be8cbd0))


### Bug Fixes

* update vendor hash handling in workflow ([fe692a5](https://github.com/kunchenguid/treehouse/commit/fe692a5fdce020a003581abece3d7eacf88dfb03))

## [1.2.1](https://github.com/kunchenguid/treehouse/compare/v1.2.0...v1.2.1) (2026-03-21)


### Bug Fixes

* use remote URL for pool hash for local repos ([7b13a4d](https://github.com/kunchenguid/treehouse/commit/7b13a4dd52dbef7270cd1535575e1a0610d8d296))

## [1.2.0](https://github.com/kunchenguid/treehouse/compare/v1.1.5...v1.2.0) (2026-03-17)


### Features

* **config:** add configurable root for pool directory ([#12](https://github.com/kunchenguid/treehouse/issues/12)) ([0bc1378](https://github.com/kunchenguid/treehouse/commit/0bc1378b758ac93bb4ca430a942e87a5c3b8f020))

## [1.1.5](https://github.com/kunchenguid/treehouse/compare/v1.1.4...v1.1.5) (2026-03-16)


### Bug Fixes

* update repository URLs ([b9d1fda](https://github.com/kunchenguid/treehouse/commit/b9d1fda8f919411002e8d5119e35693e7a97fbbe))

## [1.1.4](https://github.com/kunchenguid/treehouse/compare/v1.1.3...v1.1.4) (2026-03-15)


### Bug Fixes

* app update permission error ([0559e99](https://github.com/kunchenguid/treehouse/commit/0559e99680c8d1f0a99f969c9fdf5407e4027aa3))

## [1.1.3](https://github.com/kunchenguid/treehouse/compare/v1.1.2...v1.1.3) (2026-03-15)


### Bug Fixes

* recheck app update when cached version is stale ([21d93e2](https://github.com/kunchenguid/treehouse/commit/21d93e2e36eb3948623e21a6e92c520bae476da9))

## [1.1.2](https://github.com/kunchenguid/treehouse/compare/v1.1.1...v1.1.2) (2026-03-15)


### Bug Fixes

* shorter version display ([9c51b35](https://github.com/kunchenguid/treehouse/commit/9c51b35fdb34cc1230d14c6695cd32f04345cf9b))

## [1.1.1](https://github.com/kunchenguid/treehouse/compare/v1.1.0...v1.1.1) (2026-03-15)


### Bug Fixes

* install under ~/.local/bin when in PATH ([08bb5b6](https://github.com/kunchenguid/treehouse/commit/08bb5b6ec2fa91d2f9e426164cd3313d90812918))

## [1.1.0](https://github.com/kunchenguid/treehouse/compare/v1.0.2...v1.1.0) (2026-03-15)


### Features

* **status:** show current worktree status ([75b24a0](https://github.com/kunchenguid/treehouse/commit/75b24a0b8a0fe2ea4ed88e8a28288c529403e951))
* use latest default branch for worktree ([df3ee7b](https://github.com/kunchenguid/treehouse/commit/df3ee7b364aab64e1d7099422815ebeb43dc6c58))

## [1.0.2](https://github.com/kunchenguid/treehouse/compare/v1.0.1...v1.0.2) (2026-03-15)


### Bug Fixes

* **cli:** expose version flag and set rootCmd.Version ([ac84c4a](https://github.com/kunchenguid/treehouse/commit/ac84c4a38c72b75a9fe633e138b50aaf66d20e26))
* windows test failure ([4e24e5f](https://github.com/kunchenguid/treehouse/commit/4e24e5ff502e502f657bb417ea74a44012a28eb8))

## [1.0.1](https://github.com/kunchenguid/treehouse/compare/v1.0.0...v1.0.1) (2026-03-14)


### Bug Fixes

* CI failures ([d744564](https://github.com/kunchenguid/treehouse/commit/d744564529cad1975c78a29b2b8ed4d61d529977))

## 1.0.0 (2026-03-14)


### Features

* initial project setup ([bfc295d](https://github.com/kunchenguid/treehouse/commit/bfc295dd52e0452b5a69ea2642864449380d54b5))

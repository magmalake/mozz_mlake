# mozz_mlake

**This is not a new fuzzing library. It is a packaged build of
[mozz](https://github.com/ehsanmok/mozz) by
[Ehsan M. Kermani](https://github.com/ehsanmok), redistributed so that
[magmalake](https://github.com/magmalake) repositories can depend on it.**

All of the code here — the mutation engine, the `Arbitrary` trait, shrinking,
the corpus handling — is upstream's work.

**If you are looking for the project, go upstream:
<https://github.com/ehsanmok/mozz>.** Star it there, file issues there, send
pull requests there.

## Why this exists

mozz is not published to any conda channel, so `pixi` cannot resolve it. That
blocks two things: `flare_mlake`'s fuzz environment, and using mozz for fuzzing
in magmalake's own repositories.

## What differs from upstream

- **The build backend pin.** Upstream pins
  `pixi-build-rattler-build ==0.3.13`, which requires a
  `pixi-build-api-version` that is no longer published, so no current pixi can
  solve it — upstream works around this by pinning CI to pixi 0.70.2. The
  magmalake repos are all on pixi 0.78.0, so this tracks `0.4.*` instead.
- **The package is named `mozz_mlake`**; the module is still imported as
  `mozz`, so no source changes are needed by consumers and switching to an
  official package later is a one-line dependency change.

Nothing else. Upstream's README is preserved verbatim as
[README.upstream.md](README.upstream.md).

## This repository should not outlive its usefulness

The moment mozz is published to a channel `pixi` can resolve, magmalake should
depend on that and this repository should be archived.

## License

MIT, © 2026 Ehsan M. Kermani. See [LICENSE](LICENSE), unchanged from upstream.

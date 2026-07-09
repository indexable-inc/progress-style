> [!NOTE]
> [`indexable-inc/progress-style`](https://github.com/indexable-inc/progress-style) is a read-only mirror, generated from [`packages/progress-style`](https://github.com/indexable-inc/index/tree/024f8681bc41a14aa5095850a079126e2afb337f/packages/progress-style) in [`indexable-inc/index`](https://github.com/indexable-inc/index) at commit `024f8681bc41`. The monorepo is the source of truth: please open issues and pull requests [there](https://github.com/indexable-inc/index). This mirror is regenerated automatically; anything pushed directly here will be overwritten.

# progress-style

The shared [`indicatif`](https://docs.rs/indicatif) progress-bar and spinner
styling for ix command-line tools: one owner for the glyphs, colors, and
templates, so `search`, `dag-runner`, and future commands render the same
shape instead of each hand-rolling a template.

The bar fills one-eighth of a cell at a time with block glyphs over a visible
`░` track (no segmented `=>-` arrow), fronted by a braille spinner:

```text
⠹ indexing 42/128 ███████████▎░░░░░░░░░░░░░░░░░░░ 00:00:07
```

## Quickstart

Pick a style, then set the per-run label and status on the bar:

```rust
use indicatif::ProgressBar;

let bar = ProgressBar::new(128).with_style(progress_style::bar("cyan"));
bar.set_prefix("indexing");
for item in work {
    process(item);
    bar.inc(1);
}
bar.finish();
```

`bar(accent)` is a determinate bar whose fill color marks the phase;
`spinner()` is the matching indeterminate spinner for work with no known
total (label via `set_prefix`, status line via `set_message`).

## Pointers

- [doc/progress-style/overview.md](https://github.com/indexable-inc/index/blob/main/doc/progress-style/overview.md)
  — from-source documentation.

## Install

`progress-style` is not on crates.io; add it as a git dependency:

```toml
[dependencies]
progress-style = { git = "https://github.com/indexable-inc/progress-style" }
```

Changes: [CHANGELOG.md](CHANGELOG.md), derived from the [monorepo history](https://github.com/indexable-inc/index/commits/main/packages/progress-style) of the package.

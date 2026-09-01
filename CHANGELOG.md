# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Changed

- Discover artifacts by scanning `*.metadata.json` sidecars instead of `*.md` files, so artifacts are no longer limited to the `.md` extension.

## [0.1.1] - 2026-09-01

### Changed

- Use "artifact" terminology consistently in docs and CLI help text.

## [0.1.0] - 2026-09-01

### Added

- `agyfind` CLI to list and inspect Antigravity CLI brain files, with `summary`, `ls`, and `show` subcommands.

# Changelog

All notable changes are documented here.
Format follows keepachangelog.com, versions are semver-ish.

## [0.3.6] - 2026-08-13

### Fixed
- off-by-one in the summary counter
- config values were ignored when flags were present

### Changed
- faster directory walking, fewer syscalls

## [0.2.0] - 2026-05-22

### Added
- 4xx fails fast; 429 and 5xx retry with jittered backoff

## [0.1.0] - 2026-04-23

### Added
- 4xx fails fast; 429 and 5xx retry with jittered backoff

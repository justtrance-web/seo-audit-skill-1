# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [3.0.1] - 2026-05-06

### Fixed

- Republished `dist/index.js` so the programmatic entry point
  (`import { createAuditor } from '@seomator/seo-audit'`) works on npm. The
  source was correct, but the `3.0.0` tarball was missing the library build
  artifact, causing programmatic consumers to receive an undefined export.

### Added

- Integration test suite for the programmatic API (`src/auditor.test.ts`).
  Covers `createAuditor` / `Auditor` exports, default-vs-filtered category
  selection, the `AuditResult` shape returned by `audit()`, lifecycle callback
  ordering (`onCategoryStart` → `onRuleComplete*` → `onCategoryComplete`), and
  the single-fetch invariant. Imports through `./index.js` to mirror the npm
  consumer entry point and catch packaging regressions like the one reported
  against the published `3.0.0` artifact.

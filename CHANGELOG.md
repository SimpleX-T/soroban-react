# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.1.0] - 2026-03-15

### Added

- `SorobanProvider` for configuring Soroban network and wallet context.
- `useWallet` hook for connecting, disconnecting, and reading wallet state.
- `useNetwork` hook for reading active network configuration.
- `useContractRead` hook for reactive Soroban contract reads.
- `useContractWrite` hook for invoking Soroban contract methods.
- `useTransaction` hook for tracking transaction lifecycle state.
- `@soroban-react/freighter` adapter for Freighter wallet support.

[unreleased]: https://github.com/SimpleX-T/soroban-react/compare/v0.1.0...HEAD
[0.1.0]: https://github.com/SimpleX-T/soroban-react/releases/tag/v0.1.0

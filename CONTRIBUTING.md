# Contributing to LWS

Thanks for your interest in contributing to the Local Wallet Standard! This guide will help you get started.

## Development Setup

### Prerequisites

- [Rust](https://rustup.rs/) (stable toolchain)
- [Node.js](https://nodejs.org/) >= 20 (for Node bindings)
- [Python](https://python.org/) >= 3.9 + [Maturin](https://www.maturin.rs/) (for Python bindings)

### Building from Source

```bash
# Clone the repo
git clone https://github.com/dawnlabsai/lws.git
cd lws

# Build the Rust workspace
cd lws && cargo build --workspace --release

# Build Node bindings
cd bindings/node && npm install && npx napi build --platform --release

# Build Python bindings
cd bindings/python && maturin develop --release
```

### Running Tests

```bash
# Rust tests
cd lws && cargo test --workspace

# Node tests
cd bindings/node && npm test
```

### Code Formatting

```bash
cd lws && cargo fmt --all      # Format Rust code
cd lws && cargo clippy --workspace -- -D warnings  # Lint
```

## Making Changes

1. **Fork** the repo and create a branch from `main`.
2. **Make your changes.** Keep commits focused and use [conventional commit](https://www.conventionalcommits.org/) messages (e.g., `feat:`, `fix:`, `chore:`).
3. **Test.** Ensure `cargo test --workspace` passes and `cargo clippy` is clean.
4. **Open a PR** against `main` with a clear description of what changed and why.

## Pull Request Guidelines

- Keep PRs small and focused — one logical change per PR.
- Update documentation if your change affects the public API or CLI.
- Add tests for new functionality.
- Ensure CI passes before requesting review.

## Project Structure

```
lws/
├── lws/crates/
│   ├── lws-core/      # Types, CAIP parsing, errors
│   ├── lws-signer/    # HD derivation, signing, address generation
│   ├── lws-lib/       # FFI interface for language bindings
│   └── lws-cli/       # CLI tool
├── bindings/
│   ├── node/          # Node.js NAPI bindings
│   └── python/        # Python (PyO3/Maturin) bindings
├── docs/              # Specification documents
└── website/           # Static site (localwalletstandard.org)
```

## Reporting Bugs

Open a [GitHub Issue](https://github.com/dawnlabsai/lws/issues) with:
- Steps to reproduce
- Expected vs actual behavior
- OS, Rust version, and LWS version (`lws --version`)

## Questions?

Open a [discussion](https://github.com/dawnlabsai/lws/discussions) or an issue — we're happy to help.

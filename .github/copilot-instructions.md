# Copilot Instructions for HTTPie CLI

## Project Overview
- **HTTPie CLI** is a human-friendly command-line HTTP client for testing, debugging, and interacting with APIs and HTTP servers.
- The codebase is organized for extensibility, testability, and cross-platform support (Linux, macOS, Windows, FreeBSD).
- Major commands: `http`, `https` (see `httpie/__main__.py`).

## Architecture & Key Components
- **Core logic**: `httpie/` (request building, response handling, config, sessions, plugins)
- **CLI parsing**: `httpie/cli/` (argument parsing, CLI options, user input handling)
- **Plugins**: `httpie/plugins/` (authentication, transport, output, etc.)
- **Legacy support**: `httpie/legacy/`
- **Tests**: `tests/` (pytest-based, see `tests/README.md`)
- **Docs**: `docs/` (user/developer documentation)
- **Build/packaging**: `Makefile`, `setup.py`, `snapcraft.yaml`, `docs/packaging/`

## Developer Workflows
- **Setup**: Use `make` tasks (see `Makefile` for available commands). Typical setup:
  ```sh
  make
  make venv
  source venv/bin/activate.fish  # or .bash, .zsh, etc.
  make install
  ```
- **Testing**: Run all tests with `make test` or `pytest` from the project root. See `CONTRIBUTING.md` for details.
- **Debugging**: Use the `--debug` flag with CLI commands to get verbose output for bug reports.
- **Docs**: Edit in `docs/`, preview at https://httpie.org/docs.

## Project-Specific Conventions
- **All new features/bugfixes require tests** (see `CONTRIBUTING.md`).
- **Plugins**: Use the plugin system for new auth, transport, or output features (see `httpie/plugins/`).
- **Config/session files**: Managed in `httpie/config.py` and `httpie/sessions.py`.
- **Command-line parsing**: Centralized in `httpie/cli/argparser.py` and related files.
- **Cross-platform shell completions**: See `extras/httpie-completion.*`.
- **Profiling/benchmarks**: See `extras/profiling/`.

## Integration & External Dependencies
- **PyPI package**: `httpie` (see `setup.py`)
- **CI**: GitHub Actions (`.github/workflows/`)
- **Packaging**: Snap, Homebrew, Chocolatey, etc. (see `docs/packaging/`)

## Examples
- Add a new CLI option: update `httpie/cli/argparser.py`, add tests in `tests/test_cli.py`.
- Add a new plugin: create in `httpie/plugins/`, register in `httpie/plugins/__init__.py`, test in `tests/`.

## References
- [README.md](../README.md) — project intro, features, and links
- [CONTRIBUTING.md](../CONTRIBUTING.md) — dev setup, PR/test requirements
- [tests/README.md](../tests/README.md) — test suite overview
- [docs/README.md](../docs/README.md) — documentation structure

---
For any unclear or missing conventions, consult the above files or ask for clarification in your PR.

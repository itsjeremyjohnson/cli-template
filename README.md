# placeholder-cli

<!-- Replace with your CLI description -->

A CLI tool for [SERVICE_NAME] built with Go.

## Installation

### Homebrew (macOS/Linux)

```bash
brew tap builtbyrobben/tap
brew install placeholder-cli
```

### Download Binary

Download the latest release from [GitHub Releases](https://github.com/builtbyrobben/placeholder-cli/releases).

### Build from Source

```bash
git clone https://github.com/builtbyrobben/placeholder-cli.git
cd placeholder-cli
make build
```

## Authentication

### Set API Key

```bash
# Interactive (secure, recommended)
placeholder-cli auth set-key --stdin

# From environment variable
echo $API_KEY | placeholder-cli auth set-key --stdin

# From argument (discouraged - exposes in shell history)
placeholder-cli auth set-key YOUR_API_KEY
```

### Check Status

```bash
placeholder-cli auth status
```

### Remove Credentials

```bash
placeholder-cli auth remove
```

### Environment Variables

- `PLACEHOLDER_CLI_API_KEY` - Override stored credentials
- `PLACEHOLDER_CLI_KEYRING_BACKEND` - Force keyring backend (auto/keychain/file)
- `PLACEHOLDER_CLI_KEYRING_PASS` - Password for file backend (headless systems)

## Usage

<!-- Add your CLI usage examples here -->

```bash
placeholder-cli --help
```

## Development

### Prerequisites

- Go 1.22+ for the module and build contract; the CI test suite runs on Go 1.25
- Go 1.25+ for `make tools`, `make fmt`, `make lint`, and `make ci`
- Make

### Commands

```bash
make build        # Build binary
make test         # Run tests
make lint         # Run linter
make ci           # Run full CI suite
make tools        # Install dev tools
```

### CI and template adaptation

Linux runs formatting, linting, and tests with Go 1.25, which the pinned lint tools require. macOS and Windows keep Go 1.22 build and credential smoke coverage; the module's Go 1.22 requirement is unchanged. CI runs on every pull request and on pushes to `main` or this template's current default branch, `feat/initial-template`.

The macOS runner checks native keyring behavior only with an empty store. The write/read/remove smoke uses the supported encrypted file backend with public dummy fixtures and a one-minute timeout. It does not verify native macOS reads of stored credentials. Production keychain trust settings are unchanged.

When adapting the template, keep `cmd/placeholder`, `placeholder-cli`, and the `PLACEHOLDER_CLI_*` environment names in sync in the code, Makefile, and workflow. Keep the explicit backend selection and status assertions so a missing fixture or environment override cannot pass as a successful storage check.

## License

MIT

## Contributing

Contributions are welcome! Please read our contributing guidelines before submitting PRs.

<p align="center">
  <img src="packages/fether-electron/build/icons/512.png" alt="Parity Fether" width="160">
</p>

# Parity Fether - a decentralised, light client-based wallet

## [» Download the latest release «](https://github.com/parityfether/fether/releases)

---

## About Parity Fether

Parity Fether is a lightweight, decentralised desktop wallet designed for managing Ether (ETH) and ERC-20 tokens.

The wallet uses a light-client architecture to interact with the Ethereum blockchain without requiring users to run a full node. It provides a simple desktop interface for managing accounts, checking balances, and sending and receiving transactions.

Parity Fether can launch its embedded Ethereum light client or connect to a separately running compatible client, offering flexibility in how users access the network.

For questions, bug reports, or feature requests, use the [GitHub Issues](https://github.com/parityfether/fether/issues) page.

Parity Fether is distributed under the BSD 3-Clause License; see [LICENSE](LICENSE).

---

## Install and start Parity Fether using binaries

Check the [Releases](https://github.com/parityfether/fether/releases) page for published versions and downloadable assets. Available formats depend on the release.

### Mac

1. Download a `.dmg` file from [Releases](https://github.com/parityfether/fether/releases), when available.
2. Open the file and install Parity Fether.
3. Launch Parity Fether from Applications.

### Windows

1. Download a `.exe` installer from [Releases](https://github.com/parityfether/fether/releases), when available.
2. Run the installer.
3. Launch Fether from the Start menu.

### Linux

#### Using the AppImage (any compatible distribution)

1. Download an `.AppImage` from [Releases](https://github.com/parityfether/fether/releases), when available.
2. Make it executable and launch it:

```bash
chmod +x ./fether-*.AppImage
./fether-*.AppImage
```

#### Using the binary archive

1. Download a `.tar.xz` archive, when available.
2. Extract it and run the executable from the extracted directory:

```bash
tar xf fether-*.tar.xz
```

#### Debian installer (Ubuntu, Linux Mint and compatible distributions)

1. Download a `.deb` package, when available.
2. Install it using your package manager or graphical package installer.
3. Launch Fether from your applications menu.

---

## Security warning

### Don't run Fether as root

Avoid running Fether as root or with elevated privileges. Wallet software should be run with only the permissions it requires.

### Beware of suspicious AppImage `.home` symlinks

An AppImage can use a matching `.home` file or directory as its home directory. A malicious symlink named like `fether-x.y.z-x86_64.AppImage.home` could redirect application data to an unexpected location. Check unfamiliar files and symlinks before launching an AppImage.

Use trusted release assets and take appropriate precautions when handling wallet credentials and funds.

---

## Build from sources

### Install dependencies

You will need Git, Node.js, Yarn and the native build tools required by your operating system. This codebase uses an older JavaScript toolchain; choose Node.js and Yarn versions compatible with its dependencies rather than assuming the latest versions will work.

#### Mac

Install the Xcode Command Line Tools:

```bash
xcode-select --install
```

Install Node.js, Yarn and Git using your preferred package managers.

#### Linux

Install Git, Node.js, Yarn and your distribution's native build dependencies. Depending on your distribution, additional libraries may be required for Electron packaging.

#### Windows

Install Git, Node.js, Yarn and the native build tools needed by the project's dependencies. Use PowerShell or a compatible shell for the commands below.

### Clone this repo

```bash
git clone https://github.com/parityfether/fether.git
cd fether
yarn install
```

The `postinstall` script runs `yarn fetch-parity` to obtain the Parity Ethereum client used by the application.

### Build and run

#### Build this repo and run

```bash
yarn electron
```

The `electron` script automatically invokes the project build before launching the Electron application.

#### Build binaries

```bash
yarn package
```

#### Run with live reload for development

```bash
yarn start
```

#### Run tests

```bash
yarn test
```

---

## Build binaries for production

### General notes

The repository uses Yarn and Lerna to build its packages. Production packaging is handled by the Electron package scripts. Platform-specific builds may require the corresponding operating system and signing configuration.

Build the packages:

```bash
yarn build
```

Package the application:

```bash
yarn package
```

The desktop package output is generated under `packages/fether-electron/dist/` when packaging succeeds.

### Mac

To run the platform-specific release build on macOS:

```bash
yarn build
cd packages/fether-electron
yarn release --mac
```

### Linux

To run the platform-specific release build on Linux:

```bash
yarn build
cd packages/fether-electron
yarn release --linux
```

### Windows

To run the platform-specific release build on Windows:

```bash
yarn build
cd packages/fether-electron
yarn release --win
```

Release commands may require additional configuration or credentials when publishing artifacts. For local builds, prefer `yarn package` unless a platform-specific release task is needed.

---

## Releases

Source versions and any published installation packages can be found on the [GitHub Releases](https://github.com/parityfether/fether/releases) page.

## License

Parity Fether is licensed under the [BSD 3-Clause License](LICENSE).

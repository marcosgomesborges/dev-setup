# macOS Development Setup

A macOS development environment setup guide and installation scripts.

![Release-macOS-doc][release-macos-shield] [![License][license-shield]](LICENSE.md) [![Twitter][twitter-shield]](https://twitter.com/mgomesborges)

## Command Line Tools (mandatory)

![Command Line Tools](./assets/terminal.png?raw=true)

The Command Line Tools Package is a small self-contained package available for download separately from Xcode and that allows you to do command line development in macOS.

### Install Command Line Tools

1. Paste that in the terminal prompt:

    ```bash
    xcode-select --install
    ```

2. A software update popup window will appear. Click `Install`, then agree to the Terms of Service when requested.

    ![Command Line Tools](./assets/Xcode-command-line-tools.png)

3. The Command Line Tools is installed at:

    ```bash
    /Library/Developer/CommandLineTools/
    ```

## Xcode (optional)

![Xcode](./assets/Xcode.png)

[Xcode](https://developer.apple.com/xcode/) is Apple's integrated development environment (IDE) for Swift, Objective-C, C, and C++. It also supports Java, AppleScript, Python, Ruby, and ResEdit (Rez).

### Install Xcode

> :red_circle: WARNING: Xcode takes over 13 GB of disk space. Its installation is not mandatory.

Download and install Xcode from the [App Store](https://apps.apple.com/us/app/xcode/id497799835?mt=12) or from [Apple's website](https://developer.apple.com/xcode/)

## Contributing

All contributions are welcome! There are many ways in which you can participate in the project, for example:

* [Submit bugs and feature requests](https://github.com/mgomesborges/mac-dev-setup/issues)
* Review the documentation and make pull requests for anything from typos to new content

If you are interested in fixing issues and contributing directly to the code base, please read our [Contribution Guide](CONTRIBUTING.md).

## Feedback

* [Request a new feature](CONTRIBUTING.md)
* [File an issue](https://github.com/mgomesborges/mac-dev-setup/issues)
* Ask a question on [Twitter](https://twitter.com/mgomesborges)

## Author

* [Marcos Gomes-Borges](https://github.com/mgomesborges)

## License

The source code is licensed under the [MIT license](LICENSE.md).

The content of this project itself is licensed under the [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0).

[twitter-shield]: https://img.shields.io/twitter/follow/mgomesborges?label=Follow&style=social
[release-macos-shield]: https://img.shields.io/badge/Doc-18--Jan--2020-blue
[license-shield]: https://img.shields.io/github/license/mgomesborges/mac-dev-setup.svg

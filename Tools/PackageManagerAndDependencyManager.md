# Package Manager vs Dependency Manager

The key difference is **dependency manager** only manages the dependency but **package manager** also host and distribute the software.

### JavaScript
- [npm](https://www.npmjs.com): package manager (distribution included, register at https://register.npmjs.org)
- [Yarn](https://yarnpkg.com): dependency manager (no distribution; pulls packages from npmjs.com register at https://registry.npmjs.org)

### .NET
- [NuGet](https://www.nuget.org): package manager (distribution included, package source at https://api.nuget.org/v3/index.json)

### iOS
- [CocoaPods](https://cocoapods.org): dependency manager (no distribution; pulls packages from `source` of package's `podspec`, commonly from GitHub)
- [Carthage](): dependency manager (no distribution)
- [Swift Package Manager](https://github.com/apple/swift-package-manager): dependency manager (no distribution; pulls package from GitHub. [Documentation](https://github.com/apple/swift-package-manager/blob/master/Documentation/Usage.md).)

### Android
- [jcenter](https://bintray.com/bintray/jcenter): package manager (distribution included, source at https://jcenter.bintray.com)
- [Maven Central](): package manager (distribution included)

### Ruby
- [RubyGems](https://rubygems.org): package manager (distribution included)

### MacOS
- [Homebrew](https://brew.sh): package manager (distribution included at http://formulae.brew.sh)

### Windows
- [Chocolatey](https://chocolatey.org): package manager (distribution included)

### Linux
- [apt-get](https://manpages.debian.org/stretch/apt/apt-get.8.en.html): package manager (distribution included)

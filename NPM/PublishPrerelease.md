# How to Publish Pre-release packages on NPM

[NPM dist-tag documentation](https://docs.npmjs.com/cli/dist-tag#purpose):
> By default, the latest tag is used by npm to identify the current version of a package, and npm install <pkg> (without any @<version> or @<tag> specifier) installs the latest tag. Typically, projects only use the latest tag for stable release versions, and use other tags for unstable versions such as prereleases.

### Steps to Publish:
- Update package.json, set version to a prerelease version, e.g. `prerelease`, `2.0.0-rc.1`, etc.
- Run `npm publish --tag prerelease` to publish the package under the prerelease tag

### Steps to Install:
- Run `npm install package@prerelease` to install prerelease package

### Caveat:
- Tags that can be interpreted as valid semver ranges will be rejected. For example, v1.4 cannot be used as a tag, because it is interpreted by semver as >=1.4.0 <1.5.0. 
- The simplest way to avoid semver problems with tags is to use tags that do not begin with a number or the letter `v`.

---
Reference:
- [npm-dist-tag documentation](https://docs.npmjs.com/cli/dist-tag)
- [Prereleases and Npm by Mike Bostock](https://medium.com/@mbostock/prereleases-and-npm-e778fc5e2420)

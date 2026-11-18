# Changelog

All notable changes to avocado-ext-docker are documented in this file.
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.2.0]

### Added
- CA bundle generation: a docker.service drop-in points the engine at a bundle
  generated at start, so public-registry pulls verify certificates. The
  ca-certificates package is now a declared dependency.

### Known limitations
- On Docker 28 or newer with the iptables backend, containers on bridge
  networks (the default bridge and user-defined ones) need the kernel to
  provide the raw netfilter table, because the engine adds a raw PREROUTING
  rule for each container endpoint. On a target whose kernel lacks it, such
  containers fail to start; host networking avoids the rule.

## [0.1.0]

### Added
- Initial release: Avocado Docker container engine.
- CI via the shared `avocado-linux/actions` reusable workflows: PR build check
  (`test.yml`) and tag-driven package + publish to the Avocado feed (`release.yml`).

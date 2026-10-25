# Changelog

All notable changes to GCVMessagePassingRules.jl are documented here. The format is based on
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and the project adheres to
[Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.0.1] - 2026-10-25

### Changed

- The compat entry for StatsFuns admits 2.

## [1.0.0] - 2026-10-16

The first release: the GCV node, the Gaussian controlled variance `y ~ N(x, exp(κz + ω))`, under
`GCVApproximation`, with the density `ExponentialLinearQuadratic` of its messages and the rules
that let the normal nodes take them, developed in the
[ReactiveMP](https://github.com/ReactiveBayes/ReactiveMP.jl) repository, whose history this
repository keeps.

[Unreleased]: https://github.com/ReactiveBayes/GCVMessagePassingRules.jl/compare/v1.0.1...HEAD
[1.0.1]: https://github.com/ReactiveBayes/GCVMessagePassingRules.jl/compare/v1.0.0...v1.0.1
[1.0.0]: https://github.com/ReactiveBayes/GCVMessagePassingRules.jl/releases/tag/v1.0.0

# GCVMessagePassingRules

[![CI](https://github.com/ReactiveBayes/GCVMessagePassingRules.jl/actions/workflows/CI.yml/badge.svg?branch=main)](https://github.com/ReactiveBayes/GCVMessagePassingRules.jl/actions/workflows/CI.yml)
[![Docs: stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://reactivebayes.github.io/GCVMessagePassingRules.jl/stable/)
[![Docs: dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://reactivebayes.github.io/GCVMessagePassingRules.jl/dev/)
[![Coverage](https://codecov.io/gh/ReactiveBayes/GCVMessagePassingRules.jl/graph/badge.svg)](https://codecov.io/gh/ReactiveBayes/GCVMessagePassingRules.jl)
[![Code style: Runic](https://img.shields.io/badge/code_style-%E1%9A%B1%E1%9A%A2%E1%9A%BE%E1%9B%81%E1%9A%B2-black)](https://github.com/fredrikekre/Runic.jl)

The Gaussian controlled variance node, `GCV`, for reactive message passing:
`y ~ N(x, exp(κz + ω))`, a normal whose log-variance is linear in other variables, the building
block of hierarchical Gaussian filters. The package holds the node, its algorithm
`GCVApproximation`, the density `ExponentialLinearQuadratic` of its messages towards `z`, `κ` and
`ω`, and the rules that let `NormalMeanVariance` and `NormalMeanPrecision` take such a message on
their `out`. The rules are variational, under `q(y, x) q(z) q(κ) q(ω)` or the mean field.

```julia
using MessagePassingRulesBase, GCVMessagePassingRules, ExponentialFamily, BayesBase

result = @call_message_update_rule(
    node = GCV, target = :y,
    m = (x = NormalMeanVariance(1.0, 2.0),),
    q = (z = PointMass(0.0), κ = PointMass(1.0), ω = PointMass(0.0)),
)
getresult(result)   # NormalMeanVariance(1.0, 3.0): the noise variance exp(1 ⋅ 0 + 0) = 1 added
```

```julia
import Pkg; Pkg.add("GCVMessagePassingRules")
```

- Documentation: <https://reactivebayes.github.io/GCVMessagePassingRules.jl/stable/>.
  `make docs` builds it locally, into `docs/build`.
- Tests: `make test` runs the suite as CI does, ending with the rule-coverage gate: every rule
  must be selected by some test. `make test test_args="name:rules"` selects items by tag, by
  name or by file; `make help` lists the other targets.
- Julia 1.10 or later. MIT licence.

@def title = "JuliaSymbolics — Symbolic programming in Julia"
@def hasmath = false
@def hascode = true
<!-- Note: by default hasmath == true and hascode == false. You can change this in
the config file by setting hasmath = false for instance and just setting it to true
where appropriate -->

# JuliaSymbolics - Home

[JuliaSymbolics](https://github.com/JuliaSymbolics/) is the Julia organization dedicated to
building a fully-featured and high performance Computer Algebra System (CAS) for the Julia
programming language. It is currently home to a layered architecture of packages:

- Layer 3: [**Symbolics.jl**](https://github.com/JuliaSymbolics/Symbolics.jl) -- A fast symbolic system designed for everyday symbolic computing needs. It features:
    - Symbolic arithmetic with type information and multiple dispatch
    - Symbolic polynomials and trigonometric functions
    - Expression simplification
    - Differentiation
    - Symbolic linear algebra (factorizations, inversion, determinants, eigencomputations, etc.)
    - Discrete math (representations of summations, products, binomial coefficients, etc.)
    - Logical and Boolean expressions
    - Symbolic equation solving and conversion to arbitrary precision
    - Support for non-standard algebras (non-commutative symbols and customizable rulesets)
    - Special functions (list provided by [SpecialFunctions.jl](https://github.com/JuliaMath/SpecialFunctions.jl))
    - Automatic conversion of Julia code to symbolic code
    - Generation of (high performance and parallel) functions from symbolic expressions
    - Fast automated sparsity detection and generation of sparse Jacobian and Hessians

- Layer 2: [**SymbolicUtils.jl**](https://github.com/JuliaSymbolics/SymbolicUtils.jl) -- The low-level representation and expression rewriting system:
    - Stores common expressions in a fast canonical form that is simplified by default
    - Rule-based simplification for further simplification
    - Polynomial-normalization (i.e. use polynomial algebra to expand expressions)

- Layer 1: [**Metatheory.jl**](https://github.com/JuliaSymbolics/Metatheory.jl) -- General purpose algebraic metaprogramming and symbolic computation library.
    - A powerful expression rewriting system and first-class pattern matching engine, based on the pattern matcher in the [SICM book](https://mitpress.mit.edu/9780262028967/structure-and-interpretation-of-classical-mechanics/).
    - An eDSL (domain specific language) to define different kinds of symbolic rewrite rules.
    - A flexible library of rewriter combinators.
    - E-graph rewriting (equality saturation) system and pattern matcher, inspired from the [egg library](https://egraphs-good.github.io/)
    - Backtracking and non-deterministic term rewriting using e-graphs.
    - Features available as generic as possible: rewrite on Julia native `Expr`, Symbolics.jl expressions or any expression satisfying [TermInterface.jl](https://github.com/JuliaSymbolics/TermInterface.jl).

- Layer 0: [**TermInterface.jl**](https://github.com/JuliaSymbolics/TermInterface.jl) -- Shared generic interface for symbolic expressions.
    - Definition of general functions for fast primitive manipulation of symbolic expressions.
    - Define methods for your expression types for the functions in this interface to use [Metatheory.jl](https://github.com/JuliaSymbolics/Metatheory.jl) features on any expression type.


## Extension Ecosystem

Due to its deep connection to the expansive Julia package ecosystem, many organizations utilize the building
blocks offered by JuliaSymbolics as the underpinning of their symbolic packages to build and extend the ecosystem.

- [**ModelingToolkit.jl**](https://github.com/SciML/ModelingToolkit.jl) -- Symbolic representations of common numerical systems
    - Ordinary differential equations
    - Stochastic differential equations
    - Partial differential equations
    - Nonlinear systems
    - Optimization problems
    - Optimal Control
    - Causal and acausal modeling (Simulink/Modelica)
    - Automated model transformation, simplification, and composition

- [**Catalyst.jl**](https://github.com/SciML/Catalyst.jl) -- Symbolic representations of chemical reactions
    - Symbolically build and represent large systems of chemical reactions
    - Generate code for ODEs, SDEs, continuous-time Markov Chains, and more
    - Simulate the models using the SciML ecosystem with O(1) Gillespie methods

- [**DataDrivenDiffEq.jl**](https://github.com/SciML/DataDrivenDiffEq.jl): Automatic identification of equations from data
    - Automated construction of ODEs and DAEs from data
    - Representations of Koopman operators and Dynamic Mode Decomposition (DMD)

- [**SymbolicRegression.jl**](https://github.com/MilesCranmer/SymbolicRegression.jl): Distributed High-Performance symbolic regression in Julia
    - Parallelized generic algorithms for finding equations from data
    - Pareto frontier based scoring

- [**ReversePropagation.jl**](https://github.com/dpsanders/ReversePropagation.jl): Source-to-source reverse mode automatic differentiation
    - Automated tracing of code and construction of backpropagation equations
    - Composes with symbolic transformation and simplification functionality

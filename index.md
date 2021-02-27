@def title = "JuliaSymbolics — Symbolic programming in Julia"
@def hasmath = false
@def hascode = true
<!-- Note: by default hasmath == true and hascode == false. You can change this in
the config file by setting hasmath = false for instance and just setting it to true
where appropriate -->

# JuliaSymbolics - Home

[JuliaSymbolics](https://github.com/JuliaSymbolics/) is the Julia organization dedicated to
building a fully-featured and high performance Computer Algebra System (CAS) for the Julia
programming language. It is currently home to two main packages:

- [**Symbolics.jl**](https://github.com/JuliaSymbolics/Symbolics.jl) -- A fast symbolic system designed for everyday symbolic computing needs. It features:
    - Symbolic arithmetic with type information and multiple dispatch
    - Symbolic polynomials and trigonometric functions
    - Pattern matching, simplification and substitution
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


- [**SymbolicUtils.jl**](https://github.com/JuliaSymbolics/SymbolicUtils.jl) -- The low-level representation and expression rewriting system:
    - Stores common expressions in a fast canonical form that is simplified by default
    - Rule-based simplification for further simplification
    - Polynomial-normalization (i.e. use polynomial algebra to expand expressions)
    - Tools for composing code.

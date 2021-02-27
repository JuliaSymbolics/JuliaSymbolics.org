@def title = "JuliaSymbolics — Symbolic programming in Julia"
@def hasmath = false
@def hascode = true
<!-- Note: by default hasmath == true and hascode == false. You can change this in
the config file by setting hasmath = false for instance and just setting it to true
where appropriate -->

~~~
<h1>JuliaSymbolics &mdash; home</h1>
~~~

~~~
<p style="font-size: 1.25em; line-height: 1.67em; text-align: center; margin: 1em 0; color: #111;">
<a href="https://github.com/JuliaSymbolics/">JuliaSymbolics</a> is an organization for Julia packages related to symbolic programming.~~~

It is currently home to two main packages:

- [**Symbolics.jl**](https://github.com/JuliaSymbolics/Symbolics.jl) -- A fast symbolic system designed for everyday symbolic computing needs. It features:
    - Variables and expressions that carry type information
    - Symbolic differentiation
    - Fast jacobian and hessian sparsity computations
    - Generate code from symbolic expressions
    - Solving linear symbolic systems (more systems planned for the future)


- [**SymbolicUtils.jl**](https://github.com/JuliaSymbolics/SymbolicUtils.jl) -- The low-level representation and expression rewriting system:
    - Stores common expressions in a fast canonical form that is simplified by default
    - Rule-based simplification for further simplification
    - Polynomial-normalization (i.e. use polynomial algebra to expand expressions)
    - Tools for composing code.

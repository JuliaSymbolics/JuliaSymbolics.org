@def title = "JuliaSymbolics — Roadmap"
@def hasmath = false
@def hascode = true
<!-- Note: by default hasmath == true and hascode == false. You can change this in
the config file by setting hasmath = false for instance and just setting it to true
where appropriate -->

# JuliaSymbolics Roadmap: A Modern Computer Algebra System for a Modern Language

We need new Computer Algebra Systems (CAS) for this new era of computing.
We need a CAS that dispatches in the multiple ways we think. We need a
CAS that scales exponentially like our problems. We need a CAS that
integrates with our package ecosystem, letting people extend parts and
contribute back to the core library all in one language. We need a
modern CAS in a modern language.

Symbolics.jl is the answer. Symbolics.jl is a pure Julia CAS which
uses the Julia core library to its fullest. It is built from the
ground up with performance in mind. We use specialized structures
for automatic simplification to match the performance of the most
fully optimized C++ libraries. It exploits parallelism at every level;
our symbolic simplification takes advantage of Julia's task-based
multithreading to transform symbolic equations into parallelized
Julia code.

This reconstruction of the idea of CAS in Julia's type system is
entirely extensible. New term types enable fast symbolic arithmetic
on standard and non-standard algebras; add-on libraries like
ModelingToolkit build a bridge from symbolics to numerics.
Symbolics.jl and its ecosystem will be the common foundation on which
the next generation of Domain-Specific Languages (DSLs) will be constructed,
automatically updated and accelerated through with the growth of this system.

## The Features of Symbolics.jl

Symbolics.jl at its launch in 2021 is already expansive. It includes:

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

and much more. A lot of these features are for free given its deep
integration with multiple dispatch and Julia's type system.

## Connection to the Package Ecosystem

### The Connection to the ModelingToolkit.jl

Here in the Julia world, we like differential equations, maybe a little
too much.

Symbolics.jl grew out of ModelingToolkit.jl, an equation-based modeling
system for the Julia programming language. Its vision is that the best
system for modeling requires having the ability to symbolically specify
models and build a library of transformations for generating more stable
and performant code. While software in a similar space like Simulink
and Modelica are disconnected from traditional programming languages
and symbolic algebra systems, ModelingToolkit.jl weaves them together,
allowing all aspects of the Julia programming language and symbolic
computing to contribute to the richness of its design.

The ModelingToolkit.jl project has been almost too much of a success
in that respect, reaching a feature-base that included an entire
CAS as a submodule within itself. It was time for that CAS to be set
free. Symbolics.jl is that CAS, now set in its own organization,
JuliaSymbolics, with its ability to transform new domains.

ModelingToolkit.jl will continue to provide the symbolic representations
of common numeric systems and the SciML organization, such as causal
and acausal modeling (Simulink/Modelica) in the domains of:

- Ordinary differential equations
- Stochastic differential equations
- Partial differential equations
- Nonlinear systems
- Optimization problems
- Optimal Control

It will continue to power the connection the next generation of
symbolic-numeric computation, blurring the boundaries by mixing
analytical solutions with optimized and parallelized generated code.
All symbolic functionality related to those domains will continue to
thrive in that package, leaving Symbolics.jl the room to focus on
the core of symbolic algebras: polynomials, Grobner bases, and more.

### The Connection to SymbolicUtils.jl

Symbolics.jl is an opinionated CAS. It types its variables so that
generic Julia functions which require `Real` numbers can automatically
be converted into symbolic expressions. It uses the Leibniz rules for
defining derivatives. It does symbolic algebra as "the normal person
would expect".

However, there are some use cases in computational algebra which
require non-standard rulesets. How would you define symbolic Octonian
numbers or define differentiation on non-smooth manifolds that do
not satisfy the Leibniz rule? For these questions, mathematicians have
traditionally been on their own having to develop new tools from
scratch. However, the JuliaSymbolics has refactored its core so that new
algebras can easily be implemented and created, and automatically
get the optimized high performance of Symbolics.jl. This is SymbolicUtils.jl.

SymbolicUtils.jl is a fast and parallel rule-based rewrite system.
By specifying a list of rules, such as trigonometric identities,
you can specify new mathematical domains and create the symbolic
arithmetic that you need. Symbolics.jl is built on this foundation,
adding the common simplification rules for real numbers, derivative
definitions and rules for Newton differentiation, and more. However,
if you're so inclined, SymbolicUtils.jl is open for you to define
BraKet algebras and more.

## Goals for Symbolics.jl

Symbolics.jl will be a never ending project as we wish to provide
a high performance implementation of every symbolic algorithm that
can and does exist. But, there are specific goals we have in mind.

### High-Performance Symbolic Arithmetic

Anywhere that we are beat in performance is a bug. Please file an issue
immediately. This library should use every core, and it should use
every core efficiently, allowing the exponential cost of symbolic
arithmetic to tackled by the exponential gains in computational power
and efficiency.

### Pervasiveness Throughout the Julia DSLs

We want to provide a symbolic foundation which all DSLs can rely on.
We do not believe that a pharmacometrics library should define how
to symbolically calculate a Hessian, and then the mathematical programming
library JuMP, etc. We believe that by pooling together on Symbolics.jl,
we can accelerate the growth of DSLs throughout the language, offering
a way to collaborate towards a single battletested implementation.

### Bridge the Gap from Computer Scientists to Scientists and Mathematicans

While "code" is what package developers like to see, math is what
practioners are trained on. We are committed to bridging that gap,
making it easy to see the LaTeX-ification of the symbolic variables,
creating informative displays in notebooks. Symbolics.jl should look
and feel like doing math.

### Feature Completeness

We want Symbolics.jl to be the place where you check the documentation
immediately for symbolic methods, knowing that if such a method exists
then it's implemented there. Symbolics.jl should not just cover the
domain but also be an archive of its research and science, making it
easy to explore algorithms and compare between them.

## Next Steps for Symbolics.jl

We have not met all of our goals yet. While much of this roadmap has
been accomplished, there is much in our way forward. Some major goals
on our sights are:

- Symbolic integration using [RUBI](https://rulebasedintegration.org/)
- Expansive algorithm selection for Grobner Basis
- Feature parity with SymPy ([being tracked here](https://github.com/JuliaSymbolics/Symbolics.jl/issues/59))
- Integration with distributed and GPU computation
- High performance symbolic root finding
- Integrating modern techniques like [deep learning to accelerate and improve symbolic rule application](https://arxiv.org/pdf/1912.01412.pdf)
- Tools for [transforming generated equations to have minimal floating point error](https://herbie.uwplse.org/)
- A full reproducible benchmarking suite

## How You Can Join The Process

If you want to be a part of JuliaSymbolics, that's great, you're in!
Here are some things you can start doing:

- Star our libraries like
  [Symbolics.jl](https://github.com/JuliaSymbolics/Symbolics.jl) and
  our extensions like [ModelingToolkit.jl](https://github.com/SciML/ModelingToolkit.jl). Such
  recognition drives our growth to sustain the project.
- Join our chatroom to discuss with us. Our main chatroom is
  `#symbolic programming` on the [Julia Zulip](https://julialang.zulipchat.com/register/)
- If you're a student, find a summer project that interests you and
  apply for funding through Google Summer of Code or other processes
  (contact us if you are interested)
- Start contributing! We recommend opening up an issue to discuss
  first, and we can help you get started.
- Help update our websites, tutorials, benchmarks, and documentation
- Help answer questions on Stack Overflow, the Julia Discourse, and
  other sites!
- Hold workshops to train others on our tools.

There are many ways to get involved, so if you'd like some help
figuring out how, please get in touch with us.

# StereotypesIR

# Stereotypes
Checkout the [documentation](DOCUMENTATION.md)

## Description
TODO

## Load the module
The `StereotypesIR` module can be loaded as:

```julia
# If Julia opens in other path, change it to local
(dirname(@__FILE__) == pwd()) || cd(dirname(@__FILE__))

# If Julia is in your current path, add it
any(LOAD_PATH .== pwd()) || push!(LOAD_PATH, pwd())

# Load module
using StereotypesIR

```
## Structure
The module `StereotypesIR` is organized as:

```
src
├── StereotypesIR.jl
└── module
    ├── methods
    │   ├── evolution.jl
    │   ├── get_functions.jl
    │   └── simulation.jl
    └── structs.jl
```

The files contain:
- `Stereotypes.jl`:

    Module definition.
    Call structs and methods,
    export relevant functions,
    and precompiles.

- `structs.jl`:

    Definition of `Game`, `Population`, and `Tracker` structs.

- `evolution.jl`:

    Main functions for evolutionary dynamics. They modify
    the mutable struct `Population`.

- `get_functions.jl`:

    Functions for accessing and calculating values from a `Population` instance.

- `simulation.jl`:

    Functions for making simulations. Initializers, folder
    preparation for results, and sweeping parameters.

### Run a simulation

Define the Game parameters:
```julia
# Population size
N = 50

# Payoff parameters
b = 3.0           # benefit
c = 1.0           # cost

# Selection strength
w = 1.0

# Mutation rates
u_s  = 10/N    # strategy
u_p  = 0.02    # performance
u_a  = 0.02    # assignment
a    = 0.3     # access cost

# Game parameters
game = [b, c, w, u_s, u_p, u_a, a]
```

Define the simulation parameters:
```julia
# Number of generations
generations = 1_000

# Number of realizations per parameter
repetitions = 10
```
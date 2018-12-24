# Quantex

[Quantex](https://hex.pm/packages/quantex) is a quantum computer system environment and libraries in Elixir. Here is an example:

```elixir
iex> Q.q0  # |0> qubit = ( 1, 0 )
%Array{array: [1, 0], shape: {2, nil}}

iex> Q.q1  # |1> qubit = ( 0, 1 )
%Array{array: [0, 1], shape: {2, nil}}

iex> Q.q0 |> Q.x  # X|0> = |1> = ( 1, 0 ) ... X Gate (Bit inversion gate)
%Array{array: [0, 1], shape: {2, nil}}

iex> Q.q1 |> Q.x  # X|1> = |0> = ( 0, 1 )
%Array{array: [1, 0], shape: {2, nil}}

iex> Q.q0 |> Q.z  # Z|0> = |0> = ( 1, 0 )... Z Gate (Phase inversion gate)
%Array{array: [1, 0], shape: {2, nil}}

iex> Q.q1 |> Q.z  # Z|1> = -|1> = ( 0, -1 )
%Array{array: [0, -1], shape: {2, nil}}

iex> Q.q0 |> Q.h  # H|0> = 1 / sqrt( 2 ) |0> + 1 / sqrt( 2 ) |1> = ( 0.7, 0.7 ) ... H Gate (Hadamard gate)
%Array{array: [0.7071067811865475, 0.7071067811865475], shape: {2, nil}}

iex> Q.q1 |> Q.h  # H|1> = 1 / sqrt( 2 ) |0> - 1 / sqrt( 2 ) |1> = ( 0.7, -0.7 )
%Array{array: [0.7071067811865475, -0.7071067811865475], shape: {2, nil}}

iex> Q.cnot( Q.q0, Q.q0 )  # CNOT|00> = |00> = ( 1, 0, 0, 0 ) ... CNOT gate(Controlled NOT gate)
%Array{array: [1, 0, 0, 0], shape: {4, nil}}

iex> Q.cnot( Q.q0, Q.q1 )  # CNOT|01> = |01> = ( 0, 1, 0, 0 )
%Array{array: [0, 1, 0, 0], shape: {4, nil}}

iex> Q.cnot( Q.q1, Q.q0 )  # CNOT|10> = |11> = ( 0, 0, 0, 1 )
%Array{array: [0, 0, 0, 1], shape: {4, nil}}

iex> Q.cnot( Q.q1, Q.q1 )  # CNOT|11> = |10> = ( 0, 0, 1, 0 )
%Array{array: [0, 0, 1, 0], shape: {4, nil}}

iex> Q.cnot( Q.q1, Q.q0 ) |> Q.z  # Cz(|11>) = -|11> = ( 0, 0, 0, -1 )
%Array{array: [0, 0, 0, -1], shape: {4, nil}}

iex> Q.epr( Q.q0(), Q.q0 )  # EPR|00> = 1 / sqrt( 2 ) |00> + 1 / sqrt( 2 ) |11> = ( 0.7, 0, 0, 0.7 ) ... EPR pair
%Array{array: [0.7071067811865475, 0, 0, 0.7071067811865475], shape: {4, nil}}
```

See the [online documentation](https://hexdocs.pm/quantex).

## Installation

Add to your ```mix.exs``` file:

```elixir
def deps do
  [
    { :quantex, "~> 0.1.0" }
  ]
end
```

## License
This project is licensed under the terms of the Apache 2.0 license, see LICENSE.

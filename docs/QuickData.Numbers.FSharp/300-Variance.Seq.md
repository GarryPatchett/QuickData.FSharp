# QuickData.Numbers.FSharp

# Variance.Seq

This module lets you generate sequences of Variance.

- The [Variance.Seq Module](#the-varianceseq-module)
    - [Construction Functions](#construction-functions) with [code examples](#construction-code-examples)
    - [Deconstruction Functions](#deconstruction-functions) with [code examples](#deconstruction-code-examples)
    - [Generation Functions](#generation-functions)  with [code examples](#generation-code-examples)
    - [Variation Functions](#variation-functions)  with [code examples](#variation-code-examples)
- [Exception-free Processing](#exception-free-processing)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

> **Notes:** 
>
> 1. See the the documentation [here](../QuickData.Core.FSharp/040-Variance.md "The Variance Type") for more information about the Variance type.
>
> 2. See the the documentation [here](../QuickData.Core.FSharp/010-Normal.md "The Normal Type") for more information about the Normal type.

## The Variance.Seq Module

The `Variance.Seq` **module** defines functions for working with sequences of Variance.

### Construction Functions

The functions are:

Returns a new sequence whose elements are...

- `fromFloats` : ...the results of making a Variance from a float in the original sequence;
- `fromNormals` : ...the results of converting each Normal in the input sequence to a Variance (direct conversion);
- `fromNormalsSpread` : ...the results of converting each Normal in the input sequence to a Variance (across the Variance range).

#### Construction Code Examples

```fsharp 
let variances = 
    seq { -0.8 ; 0.2 ; 0.6 } 
    |> Variance.Seq.fromfloats
    // -> seq { V-0.8 ; V0.2 ; V0.6 }
```

### Deconstruction Functions

The functions are:

Returns a new sequence...

- `expand` : ...of floats where each Variance in the input sequence has been expanded according to the specified range;
- `toFloats` : ...whose elements are the results of obtaining the inner value of a Variance in the original sequence;
- `toNormals` : ...whose elements are the results of converting each Variance in the input sequence to a Normal (direct conversion);
- `toNormalsSpread` : ...whose elements are the results of converting each Variance in the input sequence to a Normal (across the Variance range).

#### Deconstruction Code Examples

```fsharp 
let variances = 
    seq { -0.8 ; 0.2 ; 0.6 } 
    |> Variance.Seq.fromfloats
    // -> seq { V-0.8 ; V0.2 ; V0.6 }

let normals = 
    variances 
    |> Variance.Seq.toNormals
    // -> seq { N0.0 ; N0.2 ; N0.6 }

let normalsSpread = 
    variances 
    |> Variance.Seq.toNormalsSpread
    // -> seq { N0.1 ; N0.6 ; N0.8 }

let values = 
    variances 
    |> Variance.Seq.expand (ExpansionRange.fromFloats -100.0 100.0) 
    // -> seq { -80.0 ; 20.0 ; 60.0 }
```

### Generation Functions

The functions are:

Builds a new sequence...

- `random` : ...whose elements are the results of making a Variance from a randomly-generated
                value between -1.0 and +1.0 (inclusive);
- `semiRandom` : ...whose elements are the results of making a Variance from a semi-randomly-generated
                    value between -1.0 and +1.0 (inclusive);
- `natural` : ...each element of which is a Variance. The values together resemble natural noise.

#### Generation Code Examples

```fsharp 
let rng = System.Random.Shared // Any random number generator.

let random = 
    Variance.Seq.random rng 
    // -> e.g. seq { V-0.8405302358 ; V0.02112688358 ; V-0.47318973 ; V0.5841965045; etc. }

let semiRandom = 
    Variance.Seq.semiRandom rng 
    // -> e.g. seq { V0.9910997474 ; V0.278991106 ; V-0.9980267284 ; V-0.8945446398 ; etc. }

let noise = 
    Variance.Seq.natural rng NaturalVarianceDegree.Medium 100
    // -> e.g. seq { V-0.08614438349 ; V-0.007068484245 ; V-0.004268473915 ; etc. }
```

### Variation Functions

The functions are:

Returns a new sequence whose elements are the results of...

- `add` : ...adding each offset to the corresponding element in the source input sequence;
- `scaleAll` : ...scaling each element in the input sequence by the given magnitude;
- `scale` : ...scaling each element in the
            source sequence by the corresponding magnitude in the magnitudes sequence;
- `invert` : ...inverting each element in the input sequence.

#### Variation Code Examples

```fsharp 
let rng = System.Random.Shared // Any random number generator.

let originals = 
    Variance.Seq.natural rng NaturalVarianceDegree.Medium 100
    // -> e.g. seq { V0.01814711793 ; V0.05899230515 ; V-0.007994736698 ; V-0.009257126441; etc. }

let scaledByHalf = 
    originals |> Variance.Seq.scaleAll Normal.oneHalf 
    // -> e.g. seq { V0.009073558967 ; V0.02949615257 ; V-0.003997368349 ; V-0.00462856322 ; etc. }

let reversed = originals |> Seq.rev // Note: Just Seq, not Normal.Seq

let inverted = 
    originals |> Variance.Seq.invert 
    // -> e.g. seq { V-0.01814711793 ; V-0.05899230515 ; V0.007994736698 ; V0.009257126441; etc. }
```

## Exception-free Processing

Exception-free processing versions - FailSafe, Option, and Result - of some functions are available.
See the [overview documentation](000-Overview.md "Package overview") for more information about these.

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
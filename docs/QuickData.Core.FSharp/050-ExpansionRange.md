# QuickData.Core.FSharp

# ExpansionRange

This type allows for the conversion of a Variance to a float.

- The [ExpansionRange Type](#the-expansionrange-type)
- The [ExpansionRange Module](#the-expansionrange-module)
    - [Construction Functions](#construction-functions)
    - [Deconstruction Functions](#deconstruction-functions)
    - [Variation Functions](#variation-functions)
    - [Processing Functions](#processing-functions)
    - [Code Examples](#code-examples)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The ExpansionRange Type

The `ExpansionRange` **type** defines a discriminated union which is a range to be used to create a float from a Variance. 

The cases are:

| Case Name                     | Created With                                                  |
| ----------------------------- | ------------------------------------------------------------- |
| **AsymmetricalExpansion**     | Two unequal values (the usual way to do it)                   |
| **SymmetricalExpansion**      | Two equal values (not usually recommended)                    |
| **NoExpansion**               | Two zero values (not much use at all in most circumstances)   |

## The ExpansionRange Module 

The `ExpansionRange` **module** provides functions for working with a ExpansionRange.

### Construction Functions 

The construction functions provided are:

Creates an ExpansionRange from...

- `fromFloats` : ...two (preferably different) provided float values;
- `fromSingleFloat` : ...a single float value.

### Deconstruction Functions 

The deconstruction functions provided are:

Returns an Option containing...

- `negativeMagnitude` : ...the negative magnitude...
- `positiveMagnitude` : ...the positive magnitude...

...(if there is one).

### Variation Functions

Expansion ranges, once constructed, cannot be modified. If you need to use a different range then just create a new expansion range.

### Processing Functions 

The processing functions provided are:

- `expand` : Returns a float which is calculated from a Variance and the provided range.

The expand process works by taking the value of a Variance and multiplying it by one of the magnitudes in the ExpansionRange.

For example, with an ExpansionRange of -100.0 to +300.0 (AsymmetricalExpansion), expanding
a Variance of +0.5 would return a value of +150.0 (+300.0 * +0.5), whereas expanding
a Variance of -0.5 with the same range would return a value of -50.0 (-0.5 * abs(-100.0)).

If only one unique magnitude was provided when the range was created (SymmetricalExpansion) then
the same magnitude is used for both positive and negative scaling. If the only magnitude that was
provided when the range was created was 0.0 (NoExpansion) then the actual value of the Variance
is always returned. (You can think of the NoExpansion range as an equivalent to the id function - value out = value in.)

#### Code Examples

```fsharp 
let symmetricalRange = ExpansionRange.fromSingleFloat 40 

let c = 
    Variance.fromFloat 0.5 
    |> ExpansionRange.expand symmetricalRange // -> float 20.0
let d = 
    Variance.fromFloat -0.5 
    |> ExpansionRange.expand symmetricalRange // -> float -20.0

let asymmetricalRange = ExpansionRange.fromFloats -50.0 100.0

let e = 
    Variance.fromFloat 0.5 
    |> ExpansionRange.expand asymmetricalRange // -> float 50.0
let f = 
    Variance.fromFloat -0.5 
    |> ExpansionRange.expand asymmetricalRange // -> float -25.0

let noExpansion = ExpansionRange.fromFloats 0.0 0.0 

let g = 
    Variance.fromFloat 0.5 
    |> ExpansionRange.expand noExpansion // -> float 0.5 
let h = 
    Variance.fromFloat -0.5 
    |> ExpansionRange.expand noExpansion // -> float -0.5
```

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
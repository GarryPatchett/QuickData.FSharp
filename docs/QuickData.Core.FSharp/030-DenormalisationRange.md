# QuickData.Core.FSharp

# DenormalisationRange

This type allows for the conversion of a Normal to a float.

- The [DenormalisationRange Type](#the-denormalisationrange-type)
- The [DenormalisationRange Module](#the-denormalisationrange-module)
    - [Construction Functions](#construction-functions)
    - [Deconstruction Functions](#deconstruction-functions)
    - [Variation Functions](#variation-functions)
    - [Processing Functions](#processing-functions)
    - [Code Examples](#code-examples)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The DenormalisationRange Type

The `DenormalisationRange` **type** defines a discriminated union which is a range to be used to create a float from a Normal. 

The cases are:

| Case Name                     | Created With                                                  |
| ----------------------------- | ------------------------------------------------------------- |
| **LowAndHighValues**          | Two unequal values (the usual way to do it)                   |
| **SingleValue**               | Two equal values (not usually recommended)                    |
| **NoDenormalisation**         | Two zero values (not much use at all in most circumstances)   |

## The DenormalisationRange Module 

The `DenormalisationRange` **module** provides functions for working with a DenormalisationRange.

### Construction Functions 

The construction functions provided are:

Creates a DenormalisationRange from...

- `fromFloats` : ...the two (preferably different) provided float values;
- `fromNormalisationRange` : ...a normalisation range.

### Deconstruction Functions 

The deconstruction functions provided are:

Returns an Option containing...

- `lowValue` : ...the lowest (float) value of the range...
- `highValue` : ...the highest (float) value of the range...

... (or None for NoDenormalisation).

### Variation Functions

Denormalisation ranges, once constructed, cannot be modified. If you need to use a different range then just create a new denormalisation range.

### Processing Functions 

The processing functions provided are:

- `denormalise` : Returns a float which is calculated from a Normal and the provided range.

The denormalise process works by taking the value of the Normal and mapping it from the
Normal range (0.0 to +1.0) to the provided denormalisation range.

For example, with a DenormalisationRange of -100.0 to +100.0 (LowAndHighValues), denormalising a
Normal of +0.75 would return a value of +50.0 (plus fifty), whereas denormalising a
Normal of +0.25 with the same range would return a value of -50.0 (minus fifty).

If both values used to create the range were the same then a SingleValue range will be created and 
a single value will always be returned by denormalisation, because there's no 'range' to be mapped to.

However, if both values used to create the range were zero then a NoDenormalisation range will be created and
the result of denormalisation will always be the original value.

#### Code Examples

```fsharp 
let zeroToHundredRange = DenormalisationRange.fromFloats 0.0 100.0 

let a = 
    Normal.oneQuarter 
    |> DenormalisationRange.denormalise zeroToHundredRange // -> float 25.0
let b = 
    Normal.twoFifths 
    |> DenormalisationRange.denormalise zeroToHundredRange // -> float 40.0

let spanZeroRange = DenormalisationRange.fromFloats -200.0 100.0 

let x = 
    Normal.twoThirds 
    |> DenormalisationRange.denormalise spanZeroRange // -> float 0.0 
let y = 
    Normal.oneFifth 
    |> DenormalisationRange.denormalise spanZeroRange // -> float -140.0

let noDenormalisation = DenormalisationRange.fromFloats 0.0 0.0 

let z = 
    Normal.oneHalf 
    |> DenormalisationRange.denormalise noDenormalisation // -> float 0.0 
```

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
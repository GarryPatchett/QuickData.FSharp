# QuickData.Core.FSharp

# NormalisationRange

This type allows for the conversion of a float to a Normal.

- The [NormalisationRange Type](#the-normalisationrange-type)
- The [NormalisationRange Module](#the-normalisationrange-module)
    - [Construction Functions](#construction-functions)
    - [Deconstruction Functions](#deconstruction-functions)
    - [Variation Functions](#variation-functions)
    - [Processing Functions](#processing-functions)
    - [Code Examples](#code-examples)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The NormalisationRange Type

The `NormalisationRange` **type** defines a discriminated union which is a range to be used to create a Normal from a float. 

The cases are:

| Case Name                     | Created With                                          |
| ----------------------------- | ----------------------------------------------------- |
| **BetweenLowAndHigh**         | Two unequal values (the usual way to do it)           |
| **ToMinimumOnly**             | Two equal values (not usually recommended)            |

## The NormalisationRange Module 

The `NormalisationRange` **module** provides functions for working with a NormalisationRange.

### Construction Functions 

The construction functions provided are:

Creates a NormalisationRange from...

- `fromFloats` : ...the two (preferably different) provided float values;
- `fromCollection` : ..the minimum/maximum float values in the provided collection.

### Deconstruction Functions 

The deconstruction functions provided are:

Returns an Option containing...

- `lowValue` : ...the lowest (float) value of the range... 
- `highValue` : ...the highest (float) value of the range...

...(or None for ToMinimumOnly).

### Variation Functions

Normalisation ranges, once constructed, cannot be modified. If you need to use a different range then just create a new normalisation range.

### Processing Functions 

The processing functions provided are:

- `normalise` : Returns a Normal which is calculated from a float and the provided range.

The normalise process works by taking the value of the float and mapping it, via the provided normalisation range,
to the Normal range (0.0 to +1.0).

For example, with a NormalisationRange of 0.0 to +200.0 (BetweenLowAndHigh), normalising a float
of +150.0 would return a Normal of 0.75.

If both values used to create the range were the same then a ToMinimumOnly range will be created and normalisation
will always return Normal.minimum, because there's no 'range' to be mapped to.

When creating a normalisation range from a collection, if the collection contains fewer than two elements,
or all of the values are equal, then a ToMinimumOnly range will be created and normalisation will always
return Normal.minimum, because there's no 'range' to be mapped to.

#### Code Examples

```fsharp 
let basicRange = 
    NormalisationRange.fromFloats 0.0 200.0 
    // -> BetweenLowAndHigh (0.0, 200.0)

let normal = NormalisationRange.normalise basicRange 100.0 // Normal 0.5 

let fromSequence = 
    seq { 10.0; 20.0; 5.0; 30.0; 45.0; 15.0 } 
    |> NormalisationRange.fromCollection 
    // -> BetweenLowAndHigh (5.0, 45.0)

let lowValue = fromSequence |> NormalisationRange.lowValue // -> 5.0 
```

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
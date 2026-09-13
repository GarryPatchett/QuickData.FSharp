# QuickData.Core.FSharp

# Variance

This type is a value which is clamped to the range of -1.0 to +1.0 (inclusive).

- The [Variance Module](#the-variance-module)
    - [Operators](#operators)
    - [Construction Functions](#construction-functions)
    - [Deconstruction Functions](#deconstruction-functions)
    - [Variation Functions](#variation-functions)
    - [Ready-made Values](#ready-made-values)
    - [Code Examples](#code-examples)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The Variance Module 

The `Variance` **module** provides operators and functions for working with a Variance.

> **Note:** When a Variance is printed via structured formatting - e.g. `printf "%A"` - the value will
be prefixed with a 'V', e.g. `V0.5`. You would not usually print a Variance but this might be useful to know.

### Operators

The operators provided are:

- `*` : Multiplies one Variance by another Variance, or by a Normal, returning a new Variance.

The methods provided are:

- `Value` : Returns the value of a Variance as a float (equivalent to the `toFloat` function).

### Construction Functions 

The construction functions provided are:

- `fromFloat` : The only way you can manually create a Variance;
- `fromNormal` : Creates a new Variance directly from the value of a Normal;
- `fromNormalSpread` : Creates a new Variance from the value of a Normal (value is recalculated).

### Deconstruction Functions 

The deconstruction functions provided are:

- `toFloat` : Returns the value of a Variance as a float (equivalent to the `Value` method);
- `toNormal` : Creates a new Normal directly from the value of a Variance;
- `toNormalSpread` : Creates a new Normal from the value of a Variance (value is recalculated).

### Variation Functions 

The variation functions provided are:

- `invert` : Creates a new Variance which is an inversion of the original.

Inverting a Variance takes the value of the original, gets the negative of that value (producing
a positive if the original value was negative), and then creates a new Variance from that new value.

### Ready-made Values

The `Variance` **module** also provides various ready-made values which make it easy to specify some often-used Variances.

These values are:

- `minimum` = -1.0 ; the lowest possible value;
- `zero` = 0.0;
- `maximum` = +1.0 ; the highest possible value.

#### Code Examples

```fsharp 
let okayPositive = Variance.fromFloat 0.7 // -> Variance 0.7 

let okayNegative = Variance.fromFloat -0.3 // -> Variance -0.3 

let invertedVariance = 
    Variance.fromFloat 0.4 
    |> Variance.invert // -> Variance -0.4 

let ofNormal = 
    Normal.fromFloat 0.2 
    |> Variance.fromNormal // -> Variance 0.2 

let ofNormalSpread = 
    Normal.fromFloat 0.2 
    |> Variance.fromNormalSpread // -> Variance -0.6
```

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
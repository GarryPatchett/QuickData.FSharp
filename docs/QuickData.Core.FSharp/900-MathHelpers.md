# QuickData.Core.FSharp

# MathHelpers

This module provides various math-based functions which might be useful.

- The [MathHelpers Module](#the-mathhelpers-module)
    - [Active Patterns](#active-patterns)
    - [Code Examples](#code-examples)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The MathHelpers Module 

The `MathHelpers` **module** provides functions for working with numbers.

These functions are:

- `lowThenHigh` : Returns a tuple where the two values provided are returned with the lowest value first;
- `clamp` : Clamps a value to be inside the range provided;
- `round` : Returns the value rounded to the provided number of decimal places;
- `toRadians` : Calculates the radians value for a provided degrees value.

> **Note:** These functions require that the MathHelpers module name be prefixed to the
function name (just so they don't interfere with other functions with the same name).

### Active Patterns 

The following active patterns are also available:

- `|IntIsMultipleOfTwo|IntIsNotMultipleOfTwo|` : Is an integer a multiple of two?
- `|IntIsMultipleOfFour|IntIsNotMultipleOfFour|` : Is an integer a multiple of four?
- `|FloatIsMultipleOfTwo|FloatIsNotMultipleOfTwo|` : Is a float a multiple of two?
- `|SingleIsMultipleOfTwo|SingleIsNotMultipleOfTwo|` : Is a single a multiple of two?

> **Note:** These active patterns require that the MathHelpers module name be prefixed to the
pattern name (just so they don't interfere with other patterns with the same name).

None of these functions/patterns do anything 'fancy' but they can be convenient to use on occasion.

### Code Examples

```fsharp 
let clamped = 45.0 |> MathHelpers.clamp 0.0 30.0 // -> 30.0

let lowFirst = MathHelpers.lowThenHigh 20.0 -40.0 // -> (-40.0, 20.0)

let rounded = 5.6753 |> MathHelpers.round 2 // -> 5.68 

let intMultiple = 
    match 8 with 
    | MathHelpers.IntIsMultipleOfFour -> "Multiple of Four"
    | MathHelpers.IntIsMultipleOfTwo -> "Multiple of Two"
    | MathHelpers.IntIsNotMultipleOfTwo -> "Not Multiple of Two (or Four)"
    // -> "Multiple of Four"
```

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
# QuickData.Core.FSharp

# RandomHelpers

This module provides various random number functions which might be useful.

- The [RandomHelpers Module](#the-randomhelpers-module)
    - [Code Examples](#code-examples)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The RandomHelpers Module 

The `RandomHelpers` **module** provides functions for working with random numbers.

These functions are:

- `nextSingleInRange` : Returns a single within the range provided;
- `nextFloatInRange` : Returns a float within the range provided.

> **Note:** These functions will never return the actual high value of the range provided,
            but that won't usually be a problem.

### Code Examples

```fsharp 
let rng = System.Random 1389 // Randomly-chosen seed.

let nextSingle = RandomHelpers.nextSingleInRange 10.0f 20.0f 

let randomSingles = 
    [ 1..5 ] 
    |> List.map (fun _ -> rng |> nextSingle) 
    // e.g. [ 13.75004673f; 13.75785255f; 16.62341499f; 10.30391788f; 13.19725704f ]

let nextFloat = RandomHelpers.nextFloatInRange 20 30 

let randomFloats = 
    [ 1..5 ] 
    |> List.map (fun _ -> rng |> nextFloat) 
    // e.g. [ 24.02938277; 22.56780016; 22.81813383; 28.20046628; 24.68979083 ]
```

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
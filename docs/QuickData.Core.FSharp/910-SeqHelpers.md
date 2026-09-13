# QuickData.Core.FSharp

# SeqHelpers

This module provides various sequence-based functions which might be useful.

- The [SeqHelpers Module](#the-seqhelpers-module)
    - [Code Examples](#code-examples)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The SeqHelpers Module 

The `SeqHelpers` **module** provides functions for working with sequences.

These functions are:

Returns a sequence where...

- `repeated` : ...the provided element is repeated endlessly;
- `cycle` : ...the provided sequence is repeated endlessly;
- `tombola` : ...the provided sequence is shuffled endlessly via a random number generator.

> **Tip:** These functions work with any type of element, not just those provided by this package.

### Code Examples

```fsharp 
// Remember to take the number of elements which you need, 
//  otherwise you will get an infinite sequence.

let repeated = 
    "XYZ" 
    |> SeqHelpers.repeated 
    |> Seq.take 4 
    |> Seq.toList // -> ["XYZ"; "XYZ"; "XYZ"; "XYZ"]

let cycled = 
    seq { 1 ; 2 ; 3 } 
    |> SeqHelpers.cycle 
    |> Seq.take 8 
    |> Seq.toList // -> [1; 2; 3; 1; 2; 3; 1; 2]

let rng = System.Random.Shared 

let tombolad = 
    seq { 'a' ; 'b' ; 'c' } 
    |> SeqHelpers.tombola rng 
    |> Seq.take 8 
    |> Seq.toList // -> e.g. ['c'; 'b'; 'a'; 'a'; 'b'; 'c'; 'a'; 'c']
```

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
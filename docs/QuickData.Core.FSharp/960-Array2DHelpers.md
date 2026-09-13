# QuickData.Core.FSharp

# Array2DHelpers

This module provides various two-dimensional array functions which might be useful.

- The [Array2DHelpers Module](#the-array2dhelpers-module)
    - [Code Examples](#code-examples)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The Array2DHelpers Module 

The `Array2DHelpers` **module** provides functions for working with two-dimensional arrays.

These functions are:

- `columnValues` : Returns the column values from a 2D array;
- `rowValues` : Returns the row values from a 2D array;
- `toArray` : Returns a 1D array from a 2D array.

> **Note:** The `columnValues` and `rowValues` functions will raise an `IndexOutOfRangeException`
            exception if the relevant column/row does not exist.

### Code Examples

```fsharp 
let original = 
    Array2D.init 3 2 (fun col row -> ((col + 3) * 2) * ((row + 1) * 10))
    // -> [[60; 120]
    //     [80; 160]
    //     [100; 200]]

let columnValues = 
    original 
    |> Array2DHelpers.columnValues 0 
    // -> [| 60; 80; 100 |]

let rowValues = 
    original 
    |> Array2DHelpers.rowValues 0 
    // -> [| 60; 120 |]

let oneDimension = 
    original 
    |> Array2DHelpers.toArray 
    // -> [| 60; 120; 80; 160; 100; 200 |]
```

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
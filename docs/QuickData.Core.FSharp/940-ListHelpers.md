# QuickData.Core.FSharp

# ListHelpers

This module provides various list-based functions which might be useful.

- The [ListHelpers Module](#the-listhelpers-module)
    - [Code Examples](#code-examples)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The ListHelpers Module 

The `ListHelpers` **module** provides functions for working with lists.

These functions are:

- `intersperse` : Returns a new list where the same new element is inserted between the existing elements of a list.

### Code Examples

```fsharp 
let interspersed = 
    [ "one" ; "two" ; "three" ] 
    |> ListHelpers.intersperse "****"
    // -> [ "one" ; "****" ; "two" ; "****" ; "three" ] 
```

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
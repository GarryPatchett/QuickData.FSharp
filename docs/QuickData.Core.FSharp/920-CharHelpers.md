# QuickData.Core.FSharp

# CharHelpers

This module provides various character-based functions which might be useful.

- The [CharHelpers Module](#the-charhelpers-module)
    - [Code Examples](#code-examples)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The CharHelpers Module 

The `CharHelpers` **module** provides functions for working with characters.

These functions are:

- `replaceSpaceWith` : Returns the replacement char if the original char is a space, otherwise return the original char;
- `arrayAsString` : Returns a string containing the characters from the source array of characters;
- `seqAsString` : Returns a string containing the characters from the source sequence of characters;
- `removeControlCharactersFromSeq` : Returns a sequence of char which contains no control characters;
- `removeControlCharactersFromArray` : Returns an array of char which contains no control characters.

None of these functions do anything 'fancy' but they can be convenient to use on occasion.

### Code Examples

```fsharp 
let asItWas = 'x' |> CharHelpers.replaceSpaceWith 'z' // -> 'x' 

let notSpace = ' ' |> CharHelpers.replaceSpaceWith 'a' // -> 'a' 

let stringFromArray = 
    [| 't' ; 'e' ; 'x' ; 't' |] 
    |> CharHelpers.arrayAsString 
    // -> "text"

let stringFromSequence = 
    seq { 't' ; 'e' ; 'x' ; 't' } 
    |> CharHelpers.seqAsString 
    // -> "text"

let withNoControlCharacters = 
    seq { '\a' ; 'x' ; '\r' ; 'y' } 
    |> CharHelpers.removeControlCharactersFromSeq 
    // -> seq { 'x' ; 'y' }
```

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
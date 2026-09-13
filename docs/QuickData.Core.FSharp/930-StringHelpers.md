# QuickData.Core.FSharp

# StringHelpers

This module provides various string-based functions which might be useful.

- The [StringHelpers Module](#the-stringhelpers-module)
    - [Active Patterns](#active-patterns)
    - [Code Examples](#code-examples)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The StringHelpers Module 

The `StringHelpers` **module** provides functions for working with strings.

These functions are:

- `removeControlCharacters` : Returns a string which contains no control characters;
- `removeSpaces` : Returns a string which contains no spaces;
- `removeAllButNumerals` : Returns a string which contains only numerals;
- `removeAllButLettersAndNumerals` : Returns a string which contains only letters and numerals;
- `rev` : Returns a string which contains the characters in the original string reversed;
- `capitalise` : Returns a string which contains the characters in the original string with the
                    first character converted to upper-case (if it's a letter);
- `joinedWith` : Returns a string which contains the strings in the original sequence joined
                    with the joiner string between each source string (some convenience functions are also available);
- `joinedVia` : Returns a string which contains the strings in the source sequence
                    with a joiner string between each element;
- `split` : Returns an array of string which contains the parts of the original string
                split at the characters supplied.

> **Note:** These functions require that the StringHelpers module name be prefixed to the
function name (just so they don't interfere with other functions with the same name).

### Active Patterns 

The following active patterns are also available:

- `|StringIsEmpty|StringIsNotEmpty|` : Is the string empty or only contains spaces?
- `|StringContainsControlCharacters|StringDoesNotContainControlCharacters|` : Does the string contain control characters?
- `|StringOnlyContainsNumbers|StringContainsMoreThanJustNumbers|` : Does the string only contain numbers?
- `|StringOnlyContainsLetters|StringContainsMoreThanJustLetters|` : Does the string only contain letters (either upper- or lower-case)?
- `|StringStartsWithSpace|StringDoesNotStartWithSpace|` : Does the string start with a space?
- `|StringEndsWithSpace|StringDoesNotEndWithSpace|` : Does the string end with a space?
- `|StringIsLongerThan|_|` : Is the string longer than the specified length?
- `|StringIsShorterThan|_|` : Is the string shorter than specified length?

None of these functions/patterns do anything 'fancy' but they can be convenient to use on occasion.

### Code Examples

```fsharp 
let withNoControlCharacters = 
    "\aNo\n Mess\r" 
    |> StringHelpers.removeControlCharacters // -> "No Mess"

let reversed = "abcd" |> StringHelpers.rev // -> "dcba"

let joined = 
    seq { "same" ; "join" ; "between" ; "strings" }
    |> StringHelpers.joinedWith "-" 
    // -> "same-join-between-strings"

let joinedVia = 
    seq { "different" ; "joiners" ; "between" ; "strings" }
    |> StringHelpers.joinedVia (seq { "-" ; "/" ; "=" })
    // -> "different-joiners/between=strings"

open QuickData.FSharp.StringHelpers 

// Active patterns can be used alone, for example:
let isEmpty = // -> "is empty"
    match "" with 
    | StringIsEmpty -> "is empty"
    | StringIsNotEmpty -> "not empty"

let tooLong = // -> "too long at 14 characters"
    match "my long string" with 
    | StringIsLongerThan 6 length -> "too long at " + length.ToString() + " characters"
    | _ -> "okay length"

//...or they can be used together for basic validation:
let results = 
    [ "" 
      "return\r"
      " starts with space" 
      "ends with space " 
      "too many characters" 
      "short" 
      "   "
      "this is okay"
      "\n\a\r"
      String.Empty ]
    |> List.map (fun str -> 
        match str with 
        | StringIsEmpty -> "string is empty"
        | StringContainsControlCharacters -> "contains control characters"
        | StringStartsWithSpace -> "starts with space"
        | StringEndsWithSpace -> "ends with space"
        | StringIsLongerThan 12 length -> "too long at " + length.ToString() + " characters"
        | StringIsShorterThan 6 length -> "too short at " + length.ToString() + " characters"
        | _ -> str)
    // -> ["string is empty"; "contains control characters"; "starts with space";
    //     "ends with space"; "too long at 19 characters";
    //     "too short at 5 characters"; "string is empty"; "this is okay";
    //     "contains control characters"; "string is empty"]
```

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
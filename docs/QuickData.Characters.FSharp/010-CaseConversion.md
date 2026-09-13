# QuickData.Characters.FSharp

# CaseConversion

Defines various ways in which the case of a letter can be changed.

- The [CaseConversion Type](#the-caseconversion-type)
- The [CaseConversion Module](#the-caseconversion-module) with [code examples](#single-character-code-examples)
- [Discriminated Union Identity Values](#discriminated-union-identity-values)
- [Exception-free Processing](#exception-free-processing)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The CaseConversion Type

The `CaseConversion` **type** defines a discriminated union used to specify how letters will have their case converted.

The cases are:

| Case Name                     | Conversion                                                                                                                    |
| ----------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| **NoCaseConversion** **1*     | No case conversion will be performed - letter out = letter in                                                                 |
| **RandomlyInvertCase**        | The case of the letter may be changed, or not, according to the output from a random number generator                         |
| **RandomlyToUpperCase**       | A lower-case letter can be converted, according to the output from a random number generator, to an upper-case letter         |
| **RandomlyToLowerCase**       | An upper-case letter can be converted, according to the output from a random number generator, to a lower-case letter         |
| **AlwaysInvertCase**          | The letter will always have its case changed to the opposite case                                                             |
| **AlwaysToUpperCase**         | The letter will always be converted to upper-case                                                                             |
| **AlwaysToLowerCase**         | The letter will always be converted to lower-case                                                                             |
| **FirstOnlyToUpperCase** **2* | The first letter will be converted to upper-case while the remaining letters will remain as they are                          |
| **TitleCase** **2*            | The first letter will be converted to upper-case and the remaining letters will be converted to lower-case                    |

- **1* : The default case.
- **2* : Some of these case conversions only make sense when used with sequences of more than one character. 
When used with a single character, these conversions will return the original character.

To specify a case conversion simply supply its name, such as `CaseConversion.AlwaysInvertCase`.

The difference between the input and output of some of these cases can sometimes be subtle so it is recommended
that you experiment to see which is best for your particular requirements with the data you are processing.

## The CaseConversion Module

The `CaseConversion` **module** defines various functions which work with characters for the purposes of case conversion.

These functions are:

- `convert` : Returns a character which has been passed through the case conversion process;
- `Seq.convert` : Returns a sequence of characters, each of which has been passed through the case conversion process.

#### Single Character Code Examples

```fsharp 
let rng = System.Random 1234 // Randomly-chosen seed.

let same = 
    'a' |> CaseConversion.convert rng CaseConversion.NoCaseConversion 
    // -> 'a'

let upper = 
    'a' |> CaseConversion.convert rng CaseConversion.AlwaysToUpperCase 
    // -> 'A'

let lower = 
    'Z' |> CaseConversion.convert rng CaseConversion.AlwaysToLowerCase 
    // -> 'z'

let depends = 
    'x' |> CaseConversion.convert rng CaseConversion.RandomlyInvertCase 
    // -> Maybe 'x' or 'X'
```

#### Character Sequence Code Examples

```fsharp 
let rng = System.Random 345 // Randomly-chosen seed.

let same = 
    seq { 'a' ; 'B' ; 'c' } 
    |> CaseConversion.Seq.convert rng CaseConversion.NoCaseConversion 
    // -> seq { 'a' ; 'B' ; 'c' }

let allUpper = 
    seq { 'a' ; 'B' ; 'c' } 
    |> CaseConversion.Seq.convert rng CaseConversion.AlwaysToUpperCase 
    // -> seq { 'A' ; 'B' ; 'C' }

let mixed = 
    seq { 'a' ; 'B' ; 'C' ; 'd' } 
    |> CaseConversion.Seq.convert rng CaseConversion.RandomlyInvertCase 
    // -> e.g. seq { 'A' ; 'B' ; 'c' ; 'D' }

let title = 
    seq { 'a' ; 'B' ; 'C' ; 'd' } 
    |> CaseConversion.Seq.convert rng CaseConversion.TitleCase 
    // -> seq { 'A' ; 'b' ; 'c' ; 'd' }
```

## Discriminated Union Identity Values

Functions are available for converting to and from POCO types and DU cases.
See the [overview documentation](000-Overview.md "Package overview") for more information about these.

## Exception-free Processing

Exception-free processing versions - FailSafe, Option, and Result - of some functions are available.
See the [overview documentation](000-Overview.md "Package overview") for more information about these.

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
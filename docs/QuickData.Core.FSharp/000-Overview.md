# QuickData.Core.FSharp 

## Contents

- [Overview](#overview)
- [Types And Modules](#types-and-modules)
- [Helpers](#helpers)
- [Discriminated Union Identity Values](#discriminated-union-identity-values)
- [Exception-free Processing](#exception-free-processing)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)
- [Dependencies](#dependencies)
- [Usage](#usage)

## Overview

This QuickData.Core.FSharp package contains the `QuickData.FSharp` **namespace** for F# developers
which provides some types and their related functions, and also some helper functions.

> **IMPORTANT:** There's not a lot that you can do with this package by itself and it is recommended that you install
one or more of the other QuickData.FSharp packages instead which will install this package. However, to get the best from the
other `QuickData.FSharp` packages you should understand the types and modules implemented here as they are used
extensively in those other packages.

For more information about the types, modules, and functions provided, links are provided below.

> **Note:** You can use IntelliSense in your code editor to get more information about each type and function.

## Types And Modules

The types provided, with associated modules, are (in alphabetical order):

| Type/Module                                                                                   | Defines/Specifies                                                     |
| --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| **[DenormalisationRange](030-DenormalisationRange.md "The DenormalisationRange module")**     | A range used to convert Normals to floats                             |
| **[Digit](060-Digit.md "The Digit module")** **1*                                             | Integer values (DU cases) between zero and nine (inclusive)           |
| **[ExpansionRange](050-ExpansionRange.md "The ExpansionRange module")**                       | A range used to convert Variances to floats                           |
| **[Normal](010-Normal.md "The Normal module")**                                               | Values between 0.0 and +1.0 (inclusive)                               |
| **[NormalisationRange](020-NormalisationRange.md "The NormalisationRange module")**           | A range used to convert floats to Normals                             |
| **[Variance](040-Variance.md "The Variance module")**                                         | Values between -1.0 and +1.0 (inclusive)                              |

- **1* : Used primarily by the `QuickData.Digits.FSharp` package.

## Helpers

Some modules exist which provide some helper functions which might be useful, and these are (in alphabetical order):

| Module                                                                    | Useful When Using     |
| ------------------------------------------------------------------------- | --------------------- |
| **[Array2DHelpers](960-Array2DHelpers.md "The Array2DHelpers module")**   | 2D Arrays             |
| **[CharHelpers](920-CharHelpers.md "The CharHelpers module")**            | Characters            |
| **[ListHelpers](940-ListHelpers.md "The ListHelpers module")**            | Lists                 |
| **[MathHelpers](900-MathHelpers.md "The MathHelpers module")**            | Numbers               |
| **[RandomHelpers](950-RandomHelpers.md "The RandomHelpers module")**      | Random Numbers        |
| **[SeqHelpers](910-SeqHelpers.md "The SeqHelpers module")**               | Sequences             |
| **[StringHelpers](930-StringHelpers.md "The StringHelpers module")**      | Strings               |

## Discriminated Union Identity Values

In all of the QuickData.FSharp packages, where a discriminated union exists to specify a parameter for a function,
there often will be two functions related to that discriminated union which return an integer identity value from the union
case - `toInt` - or return a union case from an integer identity value - `fromInt`.

These can be useful if you need to store a value in a data structure which does not cater for 
discriminated unions, e.g. in a file, in JSON, etc.

The `toInt` function will always return a valid identity value.

> **Notes:** 
>
> 1. Where a `fromInt` function exists there often will be [exception-free versions](#exception-free-processing) available.
>
> 2. All valid identity values are in the range 100 to 999 (inclusive). Any value which has fewer,
or more, than three digits can be immediately identified as being invalid, but not all three-digit values are valid.
> 3. While identity values are unique within a discriminated union, some identity values may be shared by cases
in different discriminated unions but no functional equality or relationship between the two should be inferred.
Identity values will not change unless specifically mentioned in the release notes.

The `defaultCase` value (where available) contains the default case for the discriminated union.

The `allCases` value (where available) contains a list of all of the cases for the discriminated union.

## Exception-free Processing

In all of the QuickData.FSharp packages, some functions will raise an exception if the internal processing fails
for some reason or if the input was not as expected.

Many of this type of function will also have alternative exception-free versions which do not
raise an exception.

These alternative functions are:
- `<module-name>.FailSafe.<function-name>`
    : Returns a default value, instead of raising an exception;
- `<module-name>.Option.<function-name>`
    : Returns `None` instead of raising an exception, otherwise `Some value`;
- `<module-name>.Result.<function-name>`
    : Returns `Error <error-type>` instead of raising an exception, otherwise `Ok value`.

In general, but not always (as documented elsewhere), if there is no exception-free version of a function then
it can be assumed that the function will not raise an exception.

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.

## Dependencies 

This package has no dependencies other than `FSharp.Core` which you will be using anyway.

> **Note:** This package will normally be automatically installed if you install any other QuickData.FSharp package, so you normally don't need to manually install this package yourself.

## Usage

The types and functions in this package have been designed to be used only with F#.

However, they may also be usable with C# but this has not been tested, so use them with C# at your own risk.
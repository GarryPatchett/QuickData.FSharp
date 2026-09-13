# QuickData.FSharp Release Notes

> **Notes:**
> 
> 1. Changes to the project documentation can be made
as necessary at any time, but they will not normally be noted in these release
notes unless those changes are particularly significant.
>
> 2. Any changes to the Intellisense documentation will be made
as necessary with new releases, but they will not normally be noted in these release
notes unless those changes are significant.
>
> 3. If any package is updated then all of the packages will be updated to the new version number,
whether thay have changed or not. This, hopefully, helps to avoid confusion by having the same version
number across all of the packages in the project at any one time.

## Overview

- [0.3.1](#031--) - New functionalities added and documentation moved.
- [0.3.0](#030--) - New packages. Also added new types and other functions to existing packages.
- [0.2.1](#021--) - Documentation changes.
- [0.2.0](#020--) - Added new types, functions, new GitHub repo, and some active patterns.
- [0.1.0](#010--) - Initial release.

## 0.3.1 - 

### Core Package

- Moved the documentation from the package itself to the project website in GitHub.
- New `RandomHelpers` **module**:
    - Provides functionalities to generate random singles/floats within a range.
- New `Array2DHelpers` **module**:
    - Provides functionalities for use with two-dimensional arrays.
- Changed `MathHelpers` **module**:
    - `toRadians` function is now more accurate (now uses a float rather than a single);
    - Added some basic active patterns to determine whether values are multiples of another value.

### Digits Package

- Moved the documentation from the package itself to the project website in GitHub.
- Changed various spelling functions to correctly spell 'forty' rather than 'fourty' (sorry about that).

### Numbers Package

- Moved the documentation from the package itself to the project website in GitHub.
- Changed `Normal.Seq` **module**:
    - Added new `linearBounceSingleHigh` function;
    - Added new `linearBounceShort` function.

    There are now three different ways to produce a linear bounce, each producing different results depending on the circumstances.

### Characters Package

- Moved the documentation from the package itself to the project website in GitHub.

### Words Package

- Moved the documentation from the package itself to the project website in GitHub.

## 0.3.0 - 

### Core Package

- New `Digit` **type** and **module**:
    - Provides functionality to create and manipulate digits (integers zero to nine, inclusive).
- New `NormalisationRange` **type** and **module**: 
    - Enables conversion of floats to normals via a range.
- Changed `DenormalisationRange` **type** and **module**: 
    - Now allows for no denormalisation (range provided was 0.0 to 0.0);
    - `lowValue` and `highValue` functions now return options.
- Changed `CharHelpers` **module**:
    - Added new `removeControlCharactersFromArray` function to remove control characters from an array of chars.
- Changed `StringHelpers` **module**:
    - Added new `capitalise` function to capitalise a string;
    - Added new `joinedWith` function (and convenience functions) to join strings with into single string;
    - Added new `joinedVia` function to join strings with other strings into a single string;
    - Added new `removeSpaces` function to remove spaces from a string;
    - Added new `removeAllButNumerals` function to remove all characters from a string which are not numerals;
    - Added new `removeAllButLettersAndNumerals` function to remove all characters from a string which are not letters or numerals;
    - Added new `split` function to split a string at the provided characters.
- New `ListHelpers` **module**:
    - `intersperse` function which inserts an element between the elements of a list.

### Digits Package

- Initial release of this package.

### Numbers Package

- Changed `Normal.Seq` **module**:
    - Added new `fromFloatsSpread` function to create a new sequence of normals from a sequence of floats via a `NormalisationRange` (provided by QuickData.Core.FSharp).

### Characters Package

- Initial release of this package.

### Words Package

- Initial release of this package.

## 0.2.1 - 

- Documentation changes required for NuGet.

## 0.2.0 - 

### Core Package

- Added new Error type for use with identity value functions in QuickData.Numbers.FSharp (and future expansion).
- Added new `CharHelpers.removeControlCharactersFromSeq` function.
- Added new `StringHelpers` **module** with various functions and active patterns for basic string validation and manipulation.
- The `CharHelpers` and `SeqHelpers` modules no longer require their name to be used as a prefix;
- Created the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp)* GitHub repository for reporting issues, asking questions, and making suggestions.

### Numbers Package

- **Important:** `NormalEquation` now defines a discriminated union with a case for each equation instead of defining the functions themselves.
    The case names are simply the old function names which have been capitalised.
    Apologies for the change but I thought it was best to change it early in development rather than cause more problems later;
- Added `Normal.Seq.gradient` function (and variants) with related types;
- Various improvements to the README documentation;
- Added `toInt` and `fromInt` functions (and variants) for some discriminated union types to allow for easier storage/retrieval of values via identity values;
- Added `defaultCase` and `allCases` values for some discriminated union types to make the functionalities easier to use in interactive environments;
- Created the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp)* GitHub repository for reporting issues, asking questions, and making suggestions.

## 0.1.0 - 

- Initial release.
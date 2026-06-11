## QuickData.Core.FSharp Release Notes

> **Note:** Any changes to the README or Intellisense documentation will be made
as necessary with new releases, but they will not normally be noted in these release
notes unless those changes are significant.

## Overview

- [0.3.0](#030--) - Added new Digit type, a new range for normalisation of floats, and other functions.
- [0.2.1](#021--) - Documentation changes.
- [0.2.0](#020--) - Added new Error type, some new helper functions, new GitHub repo, and some active patterns.
- [0.1.0](#010--) - Initial release.

### 0.3.0 - 

- New `Digit` **type** and **module**:
    - provides functionality to create and manipulate digits (integers 0 to 9, inclusive).
- New `NormalisationRange` **type** and **module**: 
    - enables conversion of floats to normals via a range.
- Changed `DenormalisationRange` **type** and **module**: 
    - now allows for no denormalisation (range provided was 0.0 to 0.0);
    - `lowValue` and `highValue` functions now return options.
- Changed `CharHelpers` **module**:
    - added new `removeControlCharactersFromArray` function to remove control characters from an array of chars.
- Changed `StringHelpers` **module**:
    - added new `capitalise` function to capitalise a string;
    - added new `joinedWith` function (and convenience functions) to join strings with into single string;
    - added new `joinedVia` function to join strings with other strings into a single string;
    - added new `removeSpaces` function to remove spaces from a string;
    - added new `removeAllButNumerals` function to remove all characters from a string which are not numerals;
    - added new `removeAllButLettersAndNumerals` function to remove all characters from a string which are not letters or numerals;
    - added new `split` function to split a string at the provided characters.
- New `ListHelpers` **module**:
    - `intersperse` function which inserts an element between the elements of a list.

### 0.2.1 - 

- Documentation changes required for NuGet.

### 0.2.0 - 

- Added new Error type for use with identity value functions in QuickData.Numbers.FSharp (and future expansion).
- Added new `CharHelpers.removeControlCharactersFromSeq` function.
- Added new `StringHelpers` **module** with various functions and active patterns for basic string validation and manipulation.
- The `CharHelpers` and `SeqHelpers` modules no longer require their name to be used as a prefix;
- Created the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp)* GitHub repository for reporting issues, asking questions, and making suggestions.

### 0.1.0 - 

- Initial release.

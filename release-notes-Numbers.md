## QuickData.Numbers.FSharp Release Notes

## Overview

- [0.2.0](#020--) - New gradient function and types, NormalEquation changes, better README, new GitHub repo, and addition of identity values for some DUs.
- [0.1.0](#010--) - Initial release.

### 0.2.0 - 

- **Important:** `NormalEquation` now defines a discriminated union with a case for each equation instead of defining the functions themselves.
    The case names are simply the old function names which have been capitalised.
    Apologies for the change but I thought it was best to change it early in development rather than cause more problems later;
- Added `Normal.Seq.gradient` function (and variants) with related types;
- Various improvements to the README documentation;
- Added `toInt` and `fromInt` functions (and variants) for some discriminated union types to allow for easier storage/retrieval of values via identity values;
- Added `defaultCase` and `allCases` values for some discriminated union types to make the functionalities easier to use in interactive environments;
- Created the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp)* GitHub repository for reporting issues, asking questions, and making suggestions.

### 0.1.0 - 

- Initial release.

# QuickData.Digits.FSharp

# DigitZeroPolicy

Defines the policies available for use when generating a new random sequence of Digit.

- The [DigitZeroPolicy Type](#the-digitzeropolicy-type)
- [Discriminated Union Identity Values](#discriminated-union-identity-values)
- [Exception-free Processing](#exception-free-processing)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The DigitZeroPolicy Type

The `DigitZeroPolicy` **type** defines a discriminated union used to specify the policy used when generating a new random sequence of Digit.

The cases are (in alphabetical order):

| Case Name                     | Meaning                                                       |
| ----------------------------- | ------------------------------------------------------------- |
| **AllowAnyDigit** **1*        | Each element of the sequence can be any Digit                 |
| **DoNotAllowZeroValue**       | Do not allow the generated sequence to be all Zeroes          |
| **NoStartingZero**            | Do not allow the first Digit in the sequence to be Zero       |
| **NoZeroesAtAll**             | Do not allow any element of the sequence to be a Zero         |

- **1* : The default case.

To specify a digit zero policy simply supply its name, such as `DigitZeroPolicy.DoNotAllowZeroValue`.

## Discriminated Union Identity Values

Functions are available for converting to and from POCO types and DU cases.
See the [overview documentation](000-Overview.md "Package overview") for more information about these.

## Exception-free Processing

Exception-free processing versions - FailSafe, Option, and Result - of some functions are available.
See the [overview documentation](000-Overview.md "Package overview") for more information about these.

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
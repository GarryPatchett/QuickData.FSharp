# QuickData.Digits.FSharp

# DigitSpellPolicy

Defines the policies available for use when creating words from a sequence of Digit.

- The [DigitSpellPolicy Type](#the-digitspellpolicy-type)
- [Discriminated Union Identity Values](#discriminated-union-identity-values)
- [Exception-free Processing](#exception-free-processing)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The DigitSpellPolicy Type

The `DigitSpellPolicy` **type** defines a discriminated union used to specify the policy for use when creating words from a sequence of Digit.

The cases are:

| Case Name                     | Meaning                                                                                                       |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------- |
| **AsSingleDigitsZero** **1*   | Each digit will be spelt individually, with Zero being spelt as "zero"                                        |
| **AsSingleDigitsOh**          | Each digit will be spelt individually, with Zero being spelt as "oh"                                          |
| **AsDoubleDigitsZero**        | Digits will be paired, from left to right, with Zero being spelt as "zero"                                    |
| **AsDoubleDigitsOh**          | Digits will be paired, from left to right, with Zero being spelt as "oh"                                      |
| **AsTelephoneBasic**          | Spell the digits as they might be written if one were to write a telephone number without numerals **2*       |

- **1* : The default case.
- **2* : This is not a 'perfect' implementation and the result might not be what everyone would want.

To specify a digit spell policy simply supply its name, such as `DigitSpellPolicy.AsSingleDigitsOh`.

See the `Digit.Seq` [documentation](100-Digit.Seq.md "The Digit.Seq module") for examples of usage.

## Discriminated Union Identity Values

Functions are available for converting to and from POCO types and DU cases.
See the [overview documentation](000-Overview.md "Package overview") for more information about these.

## Exception-free Processing

Exception-free processing versions - FailSafe, Option, and Result - of some functions are available.
See the [overview documentation](000-Overview.md "Package overview") for more information about these.

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
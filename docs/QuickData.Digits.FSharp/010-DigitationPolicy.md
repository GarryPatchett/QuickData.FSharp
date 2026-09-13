# QuickData.Digits.FSharp

# DigitationPolicy

Defines the policies by which Normals can be converted to Digits.

- The [DigitationPolicy Type](#the-digitationpolicy-type)
- [Discriminated Union Identity Values](#discriminated-union-identity-values)
- [Exception-free Processing](#exception-free-processing)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

> **Note:** See the the documentation [here](../QuickData.Core.FSharp/010-Normal.md "The Normal Type") for more information about the Normal type.

## The DigitationPolicy Type

The `DigitationPolicy` **type** defines a discriminated union used to specify the policy by which Normals are converted to Digits.

If a Normal value is 'between' two Digits then this policy lets you decide which Digit to use.

The cases are:

| Case Name                     | Map Normal To                                                                                             |
| ----------------------------- | --------------------------------------------------------------------------------------------------------- |
| **UseNearest** **1*           | The nearest Digit **2*                                                                                    |
| **TendDownwards**             | The lower of the two Digits **3*                                                                          |
| **TendUpwards**               | The higher of the two Digits **4*                                                                         |
| **TendOutwards**              | The Digit which is lower when the value is less then 0.5 or higher if greater than or equal to 0.5        |
| **TendInwards**               | The Digit which is greater when the value is less then 0.5 or lower if greater than or equal to 0.5       |

- **1* : The default case.
- **2* : uses Math.Round internally and this will usually be adequate.
- **3* : uses Math.Floor internally.
- **4* : uses Math.Ceiling internally.

To specify a digitation policy simply supply its name, such as `DigitationPolicy.TendUpwards`.

The difference between these cases can sometimes be subtle so it is recommended that you experiment to see which is best
for your particular requirements with the data you are processing.

## Discriminated Union Identity Values

Functions are available for converting to and from POCO types and DU cases.
See the [overview documentation](000-Overview.md "Package overview") for more information about these.

## Exception-free Processing

Exception-free processing versions - FailSafe, Option, and Result - of some functions are available.
See the [overview documentation](000-Overview.md "Package overview") for more information about these.

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
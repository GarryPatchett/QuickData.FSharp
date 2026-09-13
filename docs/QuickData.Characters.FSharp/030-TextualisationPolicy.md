# QuickData.Characters.FSharp

# TextualisationPolicy

Defines cases to be used when textualising a sequence of Normals.

- The [TextualisationPolicy Type](#the-textualisationpolicy-type)
- [Discriminated Union Identity Values](#discriminated-union-identity-values)
- [Exception-free Processing](#exception-free-processing)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

> **Note:** See the the documentation [here](../QuickData.Core.FSharp/010-Normal.md "The Normal Type") for more information about the Normal type.

## The TextualisationPolicy Type

The `TextualisationPolicy` **type** defines a discriminated union used to specify how a sequence of Normals can be textualised.

Textualisation takes a Normal and maps it to a character in a [character set](100-CharacterSet.md "The CharacterSet type").

The cases are:

| Case Name                 | Map Normal To                                                                                                 |
| ------------------------- | ------------------------------------------------------------------------------------------------------------- |
| **UseNearest** **1*       | The nearest character in the set **2*                                                                         |
| **TendDownwards**         | The earlier of the two characters **3*                                                                        |
| **TendUpwards**           | The later of the two characters **4*                                                                          |
| **TendOutwards**          | The character which is earlier when the value is less then 0.5 or later if greater than or equal to 0.5       |
| **TendInwards**           | The character which is later when the value is less then 0.5 or earlier if greater than or equal to 0.5       |

- **1* : The default case.
- **2* : uses Math.Round internally and this will usually be adequate.
- **3* : uses Math.Floor internally.
- **4* : uses Math.Ceiling internally.

To specify a textualisation policy simply supply its name, such as `TextualisationPolicy.TendDownwards`.

The difference between these cases can sometimes be subtle so it is recommended that you experiment to see which is best
for your particular requirements with the data you are processing.

## Discriminated Union Identity Values

Functions are available for converting to and from POCO types and DU characters.
See the [overview documentation](000-Overview.md "Package overview") for more information about these.

## Exception-free Processing

Exception-free processing versions - FailSafe, Option, and Result - of some functions are available.
See the [overview documentation](000-Overview.md "Package overview") for more information about these.

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
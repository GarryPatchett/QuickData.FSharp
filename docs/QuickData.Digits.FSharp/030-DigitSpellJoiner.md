# QuickData.Digits.FSharp

# DigitSpellJoiner

Defines a string which is used to join 'phrases' when text is created with `Digit.Seq.spell`.

- The [DigitSpellJoiner Type](#the-digitspelljoiner-type)
- The [DigitSpellJoiner Module](#the-digitspelljoiner-module)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The DigitSpellJoiner Type

The `DigitSpellJoiner` **type** defines a discriminated union used to specify how spelt 'phrases' are joined.

The cases are:

| Case Name                     | The 'Phrase' Will Have                                                            |
| ----------------------------- | --------------------------------------------------------------------------------- |
| **JoinedWithNothing**         | No joining character(s) between the words, e.g. "doublezero"                      |
| **JoinedWithSpace**           | A single space between the words, e.g. "double zero"                              |
| **JoinedWithComma**           | A single comma between the words, e.g. "double,zero"                              |
| **JoinedWithDash**            | A single dash between the words, e.g. "double-zero"                               |
| **JoinedWithDot**             | A single dot between the words, e.g. "double.zero"                                |
| **JoinedWithSlash**           | A single slash between the words, e.g. "double/zero"                              |
| **JoinedWithBackslash**       | A single backslash between the words, e.g. "double\zero"                          |
| **JoinedWithCommaAndSpace**   | A single comma and then a single space between the words, e.g. "double, zero"     |
| **UserDefinedJoiner** **1*    | A user-defined string between the words                                           |

- **1* : Requires a string modifier; use the function as described below to create one of these cases.

There is no default case.

To specify a non-user-defined digit spell joiner simply supply its name, such as `DigitSpellJoiner.DoNotAllowZeroValue`.

To specify a user-defined digit spell joiner then supply the value it was bound to when you created it.

> **Note:** These joiners are not relevant to the `AsSingle...` digit spell policies but one of them must still be specified.

## The DigitSpellJoiner Module

The `DigitSpellJoiner` **module** provides functions for working with digit spell joiners.

These functions are:

- `fromString` : Creates a new `UserDefinedJoiner` from a string;
- `toString` : Returns the string from any digit spell joiner.

> **Note:** No validation is performed on the string when you create a user defined joiner.
Because of this you might get strange results if the string contains non-keyboard characters.

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
# QuickData.Characters.FSharp

# CharacterSpellPolicy

Defines cases to be used when creating a list of strings ('phrases') from characters.

- The [CharacterSpellPolicy Type](#the-characterspellpolicy-type) with [code examples](#code-examples)
- [Discriminated Union Identity Values](#discriminated-union-identity-values)
- [Exception-free Processing](#exception-free-processing)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The CharacterSpellPolicy Type

The `CharacterSpellPolicy` **type** defines a discriminated union used to specify how characters will be spelt.

The cases are:

| Case Name                     | Charecters Spelt As Words                                         | 'a' ->    | 'x' ->        | '0' ->                |
| ----------------------------- | ----------------------------------------------------------------- | --------- | ------------- | --------------------- |
| **CivilAviation** **1*        | As defined by the International Civil Aviation Organization       | "alfa"    | "xray"        | "zero"                |
| **NatoPronunciation**         | The NATO pronunciation of the characters                          | "al-fah"  | "ecks-ray"    | "zee-ro"              |
| **InternationalMaritime**     | The International Maritime Organization characters                | "al fah"  | "ecks ray"    | "nah-dah-zay-roh"     |
| **PgpTwoSyllables**           | From the PGP biometric word list (two syllables)                  | "fallout" | "indulge"     | "chairlift"           |
| **PgpThreeSyllables**         | From the PGP biometric word list (three syllables)                | "getaway" | "inferno"     | "concurrent"          |
| **ClaphamDwyer**              | From a parody song called "A Surrealist Alphabet" about Cockneys  | "'orses"  | "breakfast"   | ""                    |

- **1* : The default case.

If the character supplied is not defined in the relevant internal table then the character is ingored.

> **Note:** The ClaphamDwyer spelling isn't much use but it's there if you want it for some reason.
(To understand why certain words have been used try to say it like a Cockney might say it, e.g. "a for 'orses" = "(h)ay for (h)orses, "x for breakfast" = "eggs for breakfast", etc.).

To specify a character spell policy simply supply its name, such as `CharacterSpellPolicy.NatoPronunciation`.

**Note:** The only language available is English. There are no plans to support other languages.

### Code Examples

```fsharp 
let rng = System.Random 4567 // Randomly-chosen seed.

let words = 
    CharacterSet.lowerCase 
    |> CharacterSet.append CharacterSet.numeralsAll 
    |> CharacterSet.tombola rng 
    |> Seq.take 12 
    // -> e.g. seq { 'n'; 'v'; '3'; 'e'; '8'; 'p'; 'b'; '5'; 'z'; 'i'; 'y'; '4' }
    |> Char.Seq.spell CharacterSpellPolicy.CivilAviation 
    // -> e.g. seq { "november" ; "victor" ; "three" ; "echo" ; "eight" ; "papa"; 
    //               "bravo" ; "five" ; "zulu" ; "india" ; "yankee" ; "four" } 

let quickData = 
    "QuickData.FSharp" // A string is a sequence of char.
    |> Char.Seq.spell CharacterSpellPolicy.PgpTwoSyllables
    // -> seq { "drunken"; "hockey"; "frighten"; "flatfoot"; "geiger"; "crumpled";
    //          "fallout"; "highchair"; "fallout"; "buzzard"; "cubic"; "dwelling"; 
    //          "freedom"; "fallout"; "guidance"; "goldfish" } 
```

## Discriminated Union Identity Values

Functions are available for converting to and from POCO types and DU characters.
See the [overview documentation](000-Overview.md "Package overview") for more information about these.

## Exception-free Processing

Exception-free processing versions - FailSafe, Option, and Result - of some functions are available.
See the [overview documentation](000-Overview.md "Package overview") for more information about these.

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
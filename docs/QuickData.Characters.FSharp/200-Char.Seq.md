# QuickData.Characters.FSharp

# Char.Seq

Defines ways to process a sequence of characters.

- The [Char.Seq Module](#the-charseq-module) with [code examples](#code-examples)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The Char.Seq Module

The `Char.Seq` **module** provides a single function:

- `spell` : Returns a sequence of string, each element of which may be the spelt version of an input char.

For example, a sequence of 'a', '6', 'c' could produce a sequence of "alfa", "six", "charlie".

If there is no available spelling for an input character in the specified policy then that character will be ignored.

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

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
# QuickData.Characters.FSharp

# CharacterSpellPolicy

Defines a specific sequence of characters.

- The [CharacterSet Type](#the-character-set-type)
- The [CharacterSet Module](#the-character-set-module)
    - [Construction Functions](#construction-functions) with [code examples](#construction-and-deconstruction-code-examples)
        - [Ready-made Character Sets](#ready-made-character-sets)
    - [Deconstruction Functions](#deconstruction-functions) with [code examples](#construction-and-deconstruction-code-examples)
    - [Variation Functions](#variation-functions) with [code examples](#variation-code-examples)
    - [Case Conversion Variation Functions](#case-conversion-variation-functions) with [code examples](#case-conversion-code-examples)
    - [Character Obfuscation Variation Functions](#character-obfuscation-variation-functions) with [code examples](#character-obfuscation-code-examples)
    - [Generation Functions](#generation-functions) with [code examples](#generation-code-examples)
    - [Specials Generation](#specials-generation) with [code examples](#specials-generation-code-examples)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The Character Set Type

The `CharacterSet` **type** defines a sequence of characters with some options for case conversion and character obfuscation.

## The Character Set Module

The `CharacterSet` **module** defines various values and functions which work with character sets.

### Construction Functions

The construction functions available are:

- `fromCharArray` : Returns a character set which contains the characters from the input array of char;
- `fromString` : Returns a character set which contains the characters from the input string.

> **Notes:** 
>
> 1. Control characters, as defined in `Char.IsControl`, will be omitted from any character set upon creation. 
If none of the characters used to create a character set are considered usable then the character set
will contain an empty sequence of characters. (This does not cause errors but no characters will be generated from such a set.)
>
> 2. Character sets are created with no case conversion and no character obfuscation.

#### Ready-made Character Sets

Some character sets are available to use without you needing to create them.

> **Note:** These character sets have no case conversion and no character obfuscation.

A character set containing...

- `lowerCase` : ...the English lower-case letters from 'a' to 'z' (inclusive) in ascending alphabetical order;
- `upperCase` : ...the English upper-case letters from 'A' to 'Z' (inclusive) in ascending alphabetical order;
- `numeralsAll` : ...the Arabic numerals from '0' to '9' (inclusive) in ascending numerical order;
- `numeralsWithoutZero` : ...the Arabic numerals from '1' to '9' (inclusive) in ascending numerical order;
- `easilyDistinguishable` : ...English keyboard characters which are easily distinguishable, especially when written down;
- `lessDistinguishable` : ...English keyboard characters which are not as easily distinguishable as some others, especially when written down;
- `forBasicPassword` : ...the English lower- and upper-case letters, all Arabic numerals, and the easily-distinguishable characters;
- `forTextualisation` : ...the English letters from 'z' to 'a' then from 'A' to 'Z'.

#### Shuffled Character Sets 

It's possible to create some variants of some of the ready-made character sets via these functions:

- `shuffledLowerCase` : The `lowerCase` character set...
- `shuffledUpperCase` : The `upperCase` character set...
- `shuffledNumeralsAll` : The `numeralsAll` character set...
- `shuffledNumeralsWithoutZero` : The `numeralsWithoutZero` character set...
- `shuffledEasilyDistinguishable` : The `easilyDistinguishable` character set...
- `shuffledLessDistinguishable` : The `lessDistinguishable` character set...

...with the characters randomly shuffled.

### Deconstruction Functions

The deconstruction functions available are:

- `toChars` : Returns a new sequence of char which contains the characters that are defined in the character set.

#### Construction And Deconstruction Code Examples

```fsharp 
let abcdFromCharArray = CharacterSet.fromCharArray [|'a' ; 'b' ; 'c' ; 'd' |]

let xyzFromString = CharacterSet.fromString "xyz"

let characters = 
    xyzFromString 
    |> CharacterSet.toChars 
    // -> seq { 'x' ; 'y' ; 'z' }
```

### Variation Functions

The variation functions available are:

Returns a new character set containing...

- `append` : ...the characters from both of the input sets;
- `combine` : ..the original characters from the first set and the
                converted and obfuscated characters from the second set;
- `distinct` : ...the characters of the original set but with no duplicated characters;
- `rev` : ...the characters of the original set in reverse order;
- `shuffled` : ...the characters of the original set shuffled in a random order.

#### Variation Code Examples

```fsharp 
// The CharHelpers.seqAsString function is in the QuickData.FSharp namespace.

let firstCharacterSet = CharacterSet.fromString "123" 

let secondCharacterSet = CharacterSet.fromString "abcd" 

let appendedCharacterSet = CharacterSet.append firstCharacterSet secondCharacterSet 

let appendedCharacterList = 
    appendedCharacterSet 
    |> CharacterSet.toChars 
    |> Seq.toList 
    // -> [ '1' ; '2' ; '3' ; 'a' ; 'b' ; 'c' ; 'd' ]

let repeatedCharacterSet = CharacterSet.fromString "qoweertyuuuuiootp" 

let distinctCharacterSet = repeatedCharacterSet |> CharacterSet.distinct

let distinctString = 
    distinctCharacterSet 
    |> CharacterSet.toChars 
    |> CharHelpers.seqAsString 
    // -> "qowertyuip"

let manyAppendedSets = 
    [ "abcd" ; "123" ; "XY"]
    |> List.map CharacterSet.fromString 
    |> List.reduce CharacterSet.append 
    |> CharacterSet.toChars 
    |> CharHelpers.seqAsString 
    // -> "abcd123XY"
```

### Case Conversion Variation Functions

The case conversion functions available are:

- `changeCaseConversion` : Returns a new character set with the case conversion changed.

The following functions are shortcuts for the `changeCaseConversion` function where the case conversion choice is built-in:

- `noCaseConversion` 
- `randomlyInvertCase` 
- `randomlyToUpperCase` 
- `randomlyToLowerCase` 
- `alwaysInvertCase` 
- `alwaysToUpperCase` 
- `alwaysToLowerCase` 
- `firstOnlyToUpperCase` 
- `titleCase` 

#### Case Conversion Code Examples

```fsharp 
// The CharHelpers.seqAsString function is in the QuickData.FSharp namespace.
// Some functions here are explained later.

let rng = System.Random 345 // Randomly-chosen seed.

let randomlyInvertedCase = 
    CharacterSet.lowerCase
    // -> "abcdefghij" etc.
    |> CharacterSet.changeCaseConversion CaseConversion.RandomlyInvertCase
    // or |> CharacterSet.randomlyInvertCase 
    |> CharacterSet.cycled rng 
    |> Seq.take 10 
    |> CharHelpers.seqAsString 
    // -> e.g. "aBcDeFGhiJ"
```

### Character Obfuscation Variation Functions

The character obfuscation functions available are:

- `changeCharacterObfuscation` : Returns a new character set with the character obfuscation changed.

The following functions are shortcuts for the `changeCharacterObfuscation` function where the character obfuscation choice is built-in:

- `noObfuscation` 
- `munge` 
- `leet` 

#### Character Obfuscation Code Examples

```fsharp 
// The CharHelpers.seqAsString function is in the QuickData.FSharp namespace.
// Some functions here are explained later.

let munged = 
    CharacterSet.lowerCase
    // -> "abcdefghij" etc.
    |> CharacterSet.changeCharacterObfuscation CharacterObfuscation.Munge 
    // or |> CharacterSet.munge 
    |> CharacterSet.cycled rng 
    |> Seq.take 10 
    |> CharHelpers.seqAsString 
    // -> "@8(63#9#1j"
```

### Generation Functions

The generation functions available are:

#### Random

- `random` : Returns a new sequence of char which is generated by choosing characters randomly from the characters in the specified set.

The following functions are the same as with the `random` function but you don't need to specify the ready-made character set as mentioned in the name:

- `randomLowerCase` 
- `randomUpperCase` 
- `randomNumeralsAll` 
- `randomNumeralsWithoutZero` 
- `randomEasilyDistinguishable` 
- `randomLessDistinguishable` 

#### Cycled

- `cycled` : Returns a new sequence of char where the characters in the specified character set are endlessly cycled.

The following functions are the same as with the `cycled` function but you don't need to specify the ready-made character set as mentioned in the name:

- `cycledLowerCase` 
- `cycledUpperCase` 
- `cycledNumeralsAll` 
- `cycledNumeralsWithoutZero` 
- `cycledEasilyDistinguishable` 
- `cycledLessDistinguishable` 

#### Tombola

- `tombola` : Returns a new sequence of char where the characters in the input character set are endlessly shuffled.

The following functions are the same as with the `tombola` function but you don't need to specify the ready-made character set as mentioned in the name:

- `tombolaLowerCase` 
- `tombolaUpperCase` 
- `tombolaNumeralsAll` 
- `tombolaNumeralsWithoutZero` 
- `tombolaEasilyDistinguishable` 
- `tombolaLessDistinguishable` 

#### Generation Code Examples

```fsharp 
// The CharHelpers.seqAsString function is in the QuickData.FSharp namespace.

let rng = System.Random 1491 // Randomly-chosen seed.

let characterSet = CharacterSet.fromString "abcde"

let randomString = 
    characterSet 
    |> CharacterSet.random rng 12
    |> CharHelpers.seqAsString 
    // -> e.g. "dbeebceccadc"

let cycledString = 
    characterSet 
    |> CharacterSet.cycled rng 
    |> Seq.take 12
    |> CharHelpers.seqAsString 
    // -> "abcdeabcdeab"

let tombolaString = 
    characterSet 
    |> CharacterSet.tombola rng 
    |> Seq.take 12
    |> CharHelpers.seqAsString 
    // -> e.g. "dbacedcbeaed"

let fourPasswords = 
    [ for _ in 1..4 -> 
        CharacterSet.forBasicPassword 
        |> CharacterSet.tombola rng 
        |> Seq.take 16 
        |> CharHelpers.seqAsString ]
        // -> e.g.
        // [ "NqOsjRB8=lfn7vHA"
        //   "Ryun5iUw9&YJKLAo" 
        //   "0ju&>y=i7KXva52t"
        //   "gOY@DPwZKXRvM<1j" ]
```

### Specials Generation

Some functions are supplied for the generation of special sequences of characters, and these are:

- `pinGenerator` : Generates numerical PINs of the specified length where the first numeral is never zero;
- `textualise` : Returns a sequence of char which is a textual representation of the input sequence of Normals
                 mapped to the characters in a character set.

> **Note:** An alternative method of generating PINs is available in the `QuickData.Digits.FSharp` package via the `Digit.Seq.randomViaPolicy` function [here](../QuickData.Digits.FSharp/100-Digit.Seq.md "The Digit.Seq Module").

The `textualise` function can be useful if you want to quickly see the 'shape' of numerical data in a compact form,
or if you are working in a text-only environment which doesn't have graphing capabilities.
It can be used with any character set but the `forTextualisation` character set has been created for convenience.

#### Specials Generation Code Examples

```fsharp 
// The CharHelpers.seqAsString function is in the QuickData.FSharp namespace.

let rng = System.Random 681 // Randomly-chosen seed.

let generatePin = CharacterSet.pinGenerator rng 

let sixPins = 
    [ for _ in 1..6 -> 
        generatePin 4 
        |> CharHelpers.seqAsString ]
    // -> e.g. [ "5240" ; "2547" ; "4749" ; "6135" ; "3179" ; "9849" ]

open QuickData.Numbers.FSharp // To get the sine wave sequence of Normal.

let text = 
    Normal.Seq.byEquation NormalEquation.SineWave 40 
    |> CharacterSet.textualise CharacterSet.forTextualisation TextualisationPolicy.UseNearest 
    |> CharHelpers.seqAsString
    // -> "AEILPSUXYZZYXWTQNJGCcgjnqtwxyzzyxuspliea"
```

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
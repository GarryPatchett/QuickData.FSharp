# QuickData.Words.FSharp

# Words

- The [Words Module](#the-words-module) with [Code Examples](#words-code-examples)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The Words Module

The `Words` **module** provides functions for generating English words.

These functions are (in alphabetical order):

### Single Word

- `singleRandomWord` : Returns a single randomly-chosen word, of any length, from the dictionary.

### Sequence Of Words

Builds a sequence of words where the possible word lengths in the range...

- `cycled` : ...are endlessly cycled;
- `random` : ...are chosen at random;
- `tombola` : ...are endlessly shuffled.

### Sentences

Returns a sentence (string) containing the source words...

- `toSentence` : ...in the order in which they are given;
- `toSortedSentence` : ...in ascending aphabetical order.

No validation is performed on the words when creating a sentence with these functions.

A sentence, as generated here, is a string containing strings, each separated by a space, with a full stop (period) at the end.

If the source collection of words is empty then an empty string will be created.

### Words Code Examples

```fsharp 
let rng = System.Random 3921 // Randomly-chosen seed.

let singleWord = Words.singleRandomWord rng // -> e.g. "acquaintance"

let onlyThreeLetters = 
    Words.random rng (WordLengthRange.fromSingleInt 3) 8 
    // -> e.g. seq { "sir"; "off"; "kid"; "cup"; "gal"; "cur"; "web"; "dip" }

let range = WordLengthRange.fromInts 3 8 

let random = 
    Words.random rng range 7 
    // -> e.g. seq { "fuel"; "ready"; "lighted";
    //               "and"; "whined"; "idea"; "poppies" }

let cycled = 
    range
    |> Words.cycled rng 
    |> Seq.take 8 
    // -> e.g. seq { "tie"; "snug"; "nests"; "crafty";
    //               "manager"; "together"; "raw"; "gate" }

let sentence = cycled |> Words.toSentence
    // -> e.g. "Tie snug nests crafty manager together raw gate."

let onlyOddWords = 
    Words.random rng WordLengthRange.onlyOddLengthWords 8 
    // -> seq { "tower"; "loosely"; "undisturbedly"; "tin"; "straightforwardness";
    //          "uncoiling"; "unconstitutionality"; "sympathetically" }
```

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
# QuickData.Sentences.FSharp

# Sentences

- The [Sentences Module](#the-sentences-module) with [Code Examples](#sentences-code-examples)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The Sentences Module

The `Sentences` **module** provides functions for generating 'nonsense' English sentences.

These functions are (in alphabetical order):

### Single Sentence

- `singleRandomSentence` : Returns a single sentence containing a random number of randomly-chosen words from the dictionary.

### Multiple Sentences

Builds a new sequence whose elements are sentences, each with a number of words within the specified sentence length range...

- `cycled` : ...where word lengths and sentence lengths are cycled from the respective ranges;
- `tombola` : ...where word lengths and sentence lengths are shuffled from the respective ranges.

A sentence, as generated here, is a string containing strings, each separated by a space, with a full stop (period) at the end.

#### Sentences Code Examples

```fsharp 
let rng = System.Random 2345 // Randomly-chosen seed.

let wordLengthRange = WordLengthRange.fromInts 3 8 

let sentenceLengthRange = SentenceLengthRange.fromInts 4 7 

let tombolad = 
    Sentences.tombola rng wordLengthRange sentenceLengthRange

let tomboladFirstFive = 
    tombolad
    |> Seq.take 5 
    // -> e.g. seq { "Eyes piteous cub choir summoned suites."; 
    //               "Map pounced included smoky crab untidy ashy."; 
    //               "Trot oat hunch executes."; 
    //               "Sorts return weed panorama starved."; 
    //               "Puffins seemed drop consider carol cub." }

let tomboladNextTwo = 
    tombolad
    |> Seq.take 2 
    // -> e.g. seq { "Meeting manger probably throw."; 
    //               "Costly cure cling alarmed scribble day hid." }

let singleRandomSentence = 
    Sentences.singleRandomSentence rng wordLengthRange
    // -> e.g. "Eel flashed pop woollen gas act."
```

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
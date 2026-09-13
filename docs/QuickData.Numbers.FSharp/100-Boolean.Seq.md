# QuickData.Numbers.FSharp

# Boolean.Seq

This module lets you generate sequences of boolean values.

- The [Boolean.Seq Module](#the-booleanseq-module)
    - [Generation Functions](#generation-functions)
    - [Variation Functions](#variation-functions)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The Boolean.Seq Module

The `Boolean.Seq` **module** defines functions for working with sequences of boolean values.

### Generation Functions

The functions are:

- `random` : True and false values generated via a random number generator;
- `repeatedTrue` : The value true repeated endlessly;
- `repeatedFalse` : The value false repeated endlessly;
- `alternatingTrueFalse` : True, then false, repeated endlessly;
- `alternatingFalseTrue` : False, then true, repeated endlessly;
- `tombola` : True and false shuffled endlessly.

> **Note:** All generated boolean sequences are of infinite length.

### Variation Functions

The functions are:

- `not` : For each element in the sequence, if the input element is true then the output element is false, otherwise the output element is true.

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
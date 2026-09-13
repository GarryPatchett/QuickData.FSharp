# QuickData.Words.FSharp

# Ranges

Since the ranges in this package are quite similar, with only some small differences, they are documented first
in general (to avoid repeated information) and then below for specific details. 

- [Shared Functionality](#shared-functionality)
    - [Construction Functions](#construction-functions)
    - [Deconstruction Functions](#deconstruction-functions)
    - [Variation Functions](#variation-functions)
- The [Word Length Range](#the-word-length-range) with [ready-made ranges](#ready-made-word-length-ranges)
- The [Sentence Length Range](#the-sentence-length-range) with [ready-made ranges](#ready-made-sentence-length-ranges)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## Shared Functionality

### Construction Functions

The ranges are discriminated unions which specify the range in different ways.

The cases are:

| Case Name                 | Modifiers                           | Defines/Specifies                                                 |
| ------------------------- | ----------------------------------- | ----------------------------------------------------------------- |
| **LengthBetween**         | LowValue (int), HighValue (int)     | The lower and upper extents (inclusive) of the range              |
| **OneLengthOnly**         | Value (int)                         | The specific length                                               |

A range can be either:

- **LengthBetween** : This type of range is one where the two values specified were not equal;
- **OneLengthOnly** : This type of range is one which was specified with either just one value or two values which were equal.

Each range will clamp the input values to certain minimum and maximum values (see below).

A number of functions are supplied for the construction of a range, and these are:

- `fromSingleInt` : Create a **OneLengthOnly** range from one value;
- `fromInts` : Create a **LengthBetween** range from two values, or if the values are equal then a **OneLengthOnly** range is created.

### Deconstruction Functions

Some functions are supplied for the deconstruction of a range, and these are:

- `lowValue` : Returns the low value of the range - the lower limit - same as the high value for OneLengthOnly ranges;
- `highValue` : Returns the high value of the range - the higher limit - same as the low value for OneLengthOnly ranges.

### Variation Functions

Ranges, once constructed, cannot be modified. If you need to use different values then just create a new range.
This gets around the confusing possibility where, for example, a new high value is specified which is lower than
the existing low value.

## The Word Length Range

The `WordLengthRange` **type** and **module** specifies a range of values for word lengths.

An extra case is available for this type:

| Case Name                 | Modifiers                           | Defines/Specifies                                                 |
| ------------------------- | ----------------------------------- | ----------------------------------------------------------------- |
| **LengthChoices**         | Values (int seq)                    | The specific lengths that are possible                            |

This case is specified with a collection of lengths via the `fromCollection` function.

> **Note:** If the input collection is empty (or does not contain any valid lengths) then only words
of a minimum length will be chosen.

The values are specified by ints and they are clamped to a range which is defined by the internal
dictionary (curently, at the time of writing, two to twenty inclusive).

Any duplicate values in the input collection are ignored.

> **Note:** Depending on how many words you generate, you might not get a word of every possible length in the range. For example,
if you specify a range of four to fifteen word lengths (a range of twelve possible lengths) and only generate six words
then you will only get six words and words of some possible lengths will not be generated.

An extra deconstruction function is available called `allValues` which returns all of the values used to define the range.

### Ready-made Word Length Ranges

Various ready-made ranges are available, and these are:

Choose...

- `onlyShortWords` : ...only short words;
- `onlyMediumLengthWords` : ...only medium-length words;
- `onlyLongWords` : ...only long words;
- `onlyVeryLongWords` : ...only very long words (not generally recommended);
- `anyWordLength` : ...any word from all of the words;
- `reasonablePasswordWords` : ...words which are of a length which is reasonable to use in a password;
- `onlyOddLengthWords` : ...only words which have an odd number of letters;
- `onlyEvenLengthWords` : ...only words which have an even number of letters.

## The Sentence Length Range

The `SentenceLengthRange` **type** and **module** specifies a range of values for sentence lengths.

The values are specified by ints and they are clamped to a range of three to twenty (inclusive).

### Ready-made Sentence Length Ranges

Various ready-made ranges are available, and these are:

Choose...

- `onlyShortSentences` : ...only short sentences;
- `onlyMediumLengthSentences` : ...only medium-length sentences;
- `onlyLongSentences` : ...only long sentences;
- `onlyVeryLongSentences` : ...only very long sentences;
- `anySentenceLength` : ...sentences of any possible length;
- `reasonablePasswordSentences` : ...sentences which are of a length which is reasonable to use in a password.

## Issues, Questions, and Suggestions

You can visit the *[QuickVectors.FSharp](https://github.com/GarryPatchett/QuickVectors.FSharp "Home page for the QuickVectors project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
# QuickData.Digit.FSharp

# Digit (extension) and Digit.Seq

This module defines ways to create and modify sequences of Digit.

- The [Digit Module](#the-digit-module-extension)
- The [Digit.Seq Module](#the-digitseq-module)
    - [Construction Functions](#construction-functions) with [code examples](#construction-and-deconstruction-code-examples)
    - [Deconstruction Functions](#deconstruction-functions) with [code examples](#construction-and-deconstruction-code-examples)
    - [Generation Functions](#generation-functions) with [code examples](#generation-code-examples)
    - [Variation Functions](#variation-functions) with  [code examples](#variation-code-examples)
    - [Processing Functions](#processing-functions) with [code examples](#processing-code-examples)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

> **Note:** See the the documentation [here](../QuickData.Core.FSharp/010-Normal.md "The Normal Type") for more information about the Normal type.

## The Digit Module (extension)

The `Digit` **module** extension provides functionality to spell a decimal number.

The `Digit.spellDecimal` function creates a string which is the spelt version of the input decimal value.

For example, the value 780206.531M becomes "seven hundred and eighty thousand, two hundred and six point five three one".

> **Notes:**
>
> 1. There are currently no modification prarameters for this function, but these might be added at
a later point - check the release notes if you notice any differences.
>
> 2. The `spellDecimal` function is also available as [exception-free versions](#exception-free-processing).
(An exception has never been raised in testing but all possible decimal values have not been checked.)
>
> 3. The only language available is English. There are no plans to support other languages.

## The Digit.Seq Module

The `Digit.Seq` **module** provides functionality to create and modify sequences of Digit.

### Construction Functions 

The construction functions provided are:

Builds a new sequence whose elements are the results of making a Digit from...

- `fromChars` : ...each char in the original sequence;
- `fromInts` : ...each int in the original sequence;
- `fromInt` : ...the numerals in the provided int (Int32) value;
- `fromInt64` : ...the numerals in the provided Int64 value;
- `fromString` : ...each char in the original string;
- `fromNormals` : ...each Normal in the original sequence.

### Deconstruction Functions 

The deconstruction functions provided are:

#### Many to Many

Builds a new sequence whose elements are the results of making...

- `toChars` : ...a char from each Digit in the original sequence;
- `toInts` : ...an int from each Digit in the original sequence;
- `toNormals` : ...a Normal from each Digit in the original sequence.

#### Many to One 

- `toInt` : Creates a new int (Int32) which is built...
- `toInt64` : Creates a new Int64 which is built...
- `toString` : Creates a new string where each character is converted...

...from the Digits in the input sequence.

#### Construction and Deconstruction Code Examples

```fsharp 
let rng = System.Random 9831 // Randomly-chosen seed.

let randomInt = rng.Next() // -> 1480705143

let fromRandom = 
    randomInt 
    |> Digit.Seq.fromInt 
    // -> seq { One; Four; Eight; Zero; Seven; Zero; Five; One; Four; Three }

let toInts = 
    fromRandom |> Digit.Seq.toInts 
    // -> seq { 1; 4; 8; 0; 7; 0; 5; 1; 4; 3 }

let fromInts = 
    toInts |> Digit.Seq.fromInts 
    // -> seq { One; Four; Eight; Zero; Seven; Zero; Five; One; Four; Three }

let toChars = 
    fromInts |> Digit.Seq.toChars 
    // -> seq { '1'; '4'; '8'; '0'; '7'; '0'; '5'; '1'; '4'; '3' }

let toString = 
    fromInts 
    |> Digit.Seq.toString // -> "1480705143"

let fromString = 
    toString 
    |> Digit.Seq.fromString 
    // -> seq { One; Four; Eight; Zero; Seven; Zero; Five; One; Four; Three }
```

### Generation Functions 

The generation functions provided are:

Builds a new sequence, each element of which is...

- `randomAll` : ...a randomly-chosen Digit;
- `randomNonZero` : ...a randomly-chosen **non-zero** Digit;
- `randomViaPolicy` : ...a Digit randomly-chosen via the specified policy;
- `randomised` : ...a Digit randomly-chosen from the input sequence;
- `randomisedAll` : ...a randomly-chosen Digit (similar result to `randomAll`);
- `randomisedNonZero` : ...a randomly-chosen **non-zero** Digit (similar result to `randomNonZero`);
- `cycled` : ...cycled from the input sequence;
- `cycledAll` : ...cycled from the sequence of all Digits;
- `cycledNonZero` : ...cycled from the sequence of **non-zero** Digits;
- `tombola` : ...shufled from the input sequence;
- `tombolaAll` : ...shuffled from the sequence of all Digits;
- `tombolaNonZero` : ...shuffled from the sequence of **non-zero** Digits;

#### Generation Code Examples

```fsharp 
let rng = System.Random 9831 // Randomly-chosen seed.

let random = 
    Digit.Seq.randomAll rng 9 
    // -> seq { Four; Five; Nine; Seven; Eight; Seven; Five; Two; Four }

let randomViaPolicy = 
    [ for _ in 1..6 -> 
        Digit.Seq.randomViaPolicy rng DigitZeroPolicy.NoStartingZero 5 
        |> Digit.Seq.toString ]
    // -> [ "16904"; "74289"; "17441"; "62095"; "60544"; "85190" ]

let randomised = 
    seq { One ; Three ; Five } 
    |> Digit.Seq.randomised rng 7
    // -> seq { Five; One; Five; Five; One; Three; One }

let cycled = 
    seq { Two ; Four ; Six ; Eight } 
    |> Digit.Seq.cycled 
    |> Seq.take 7
    // -> seq { Two; Four; Six; Eight; Two; Four; Six }
```

### Variation Functions 

The variation functions provided are:

Returns a new sequence where each element...

- `previous` : ...is one less than the coresponding element in the input sequence;
- `next` : ...is one more than the coresponding element in the input sequence;
- `raiseAll` : ...in the input sequence has been raised by the given amount;
- `lowerAll` : ...in the input sequence has been lowered by the given amount;
- `invert` : ....in the input sequence has been inverted.

#### Variation Code Examples

```fsharp 
let original = seq { Zero ; Four ; Seven ; Nine }
let previous = original |> Digit.Seq.previous // -> seq { Nine ; Three ; Six ; Eight } 
let next = original |> Digit.Seq.next // -> seq { One ; Five ; Eight ; Zero } 
let inverted = original |> Digit.Seq.invert // -> seq { Nine ; Five ; Two ; Zero }
let raised = original |> Digit.Seq.raiseAll Two // -> seq { Two ; Six ; Nine ; One }
```

### Processing Functions 

The processing functions provided are:

- `spell` : Builds a new list of string containing the spelt versions of the provided digits as per the specified policy and joiner.

> **Note:** The only language available is English. There are no plans to support other languages.

### Processing Code Examples

```fsharp 
let asSingleOhWithSpace = 
    seq { One; Two; Zero; Four; Five } 
    |> Digit.Seq.spell AsSingleDigitsOh JoinedWithSpace 
    // -> ["one"; "two"; "oh"; "four"; "five"]

let asDoubleZeroWithDash = 
    seq { One; Two; Zero; Four; Five } 
    |> Digit.Seq.spell AsDoubleDigitsZero JoinedWithDash
    // -> ["twelve"; "zero-four"; "five"]

let phoneNumber = 
    "(0800) 56-00-78"
    |> Digit.Seq.fromString 
    // -> seq { Zero; Eight; Zero; Zero; Five; Six; Zero; Zero; Seven; Eight }
    |> Digit.Seq.spell AsTelephoneBasic JoinedWithSpace 
    // -> [ "oh"; "eight hundred"; "fifty six"; "double oh"; "seventy eight" ]
    |> List.map StringHelpers.capitalise 
    // -> [ "Oh"; "Eight hundred"; "Fifty six"; "Double oh"; "Seventy eight" ]
    |> StringHelpers.joinedWithCommaAndSpace 
    // -> "Oh, Eight hundred, Fifty six, Double oh, Seventy eight"
```

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
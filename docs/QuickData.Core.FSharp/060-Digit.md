# QuickData.Core.FSharp

# Digit

This type is a value which represents an integer numeral between zero and nine (inclusive).

- The [Digit Type](#the-digit-type)
- The [Digit Module](#the-digit-module)
    - [Construction Functions](#construction-functions)
    - [Deconstruction Functions](#deconstruction-functions)
    - [Variation Functions](#variation-functions)
    - [Other Functions](#other-functions)
    - [Active Patterns](#active-patterns)
    - [Code Examples](#code-examples)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The Digit Type

The `Digit` **type** is a discriminated union which contains cases, each of which relates
to an integer value between zero and nine (inclusive).

These cases are: Zero, One, Two, Three, Four, Five, Six, Seven, Eight, and Nine (in that order).

## The Digit Module 

The `Digit` **module** provides operators and functions for working with a Digit.

> **Note:** There's not a lot you can do with Digits by themselves and they are much more useful
when used with the functionalities provided in the `QuickData.Digits.FSharp` package.

### Construction Functions 

The construction functions provided are:

Returns a Digit which relates to...

- `fromChar` : ...a numerical character, e.g. '0' returns Zero;
- `fromInt` : ...an integer, e.g. 0 returns Zero.

Both of the above functions will raise an exception if the input is not valid.

### Deconstruction Functions 

The deconstruction functions provided are:

- `toChar` : Returns a char which relates to a Digit, e.g. Zero returns '0';
- `toInt` : Returns an int which relates to a Digit, e.g. Zero returns 0;
- `toString` : Returns a string which is the lower-case 'name' of a Digit, e.g. Zero returns "zero";
- `toNormal` : Returns a Normal which relates to a Digit, e.g. Zero returns Normal.minimum.

### Variation Functions 

The variation functions provided are:

- `previous` : Returns the Digit which is one less than the original;
- `next` : Returns the Digit which is one more than the original;
- `add` : Returns the result of adding two Digits together;
- `subtract` : Returns the result of subtracting one Digit from another Digit;
- `invert` : Returns a new Digit which is the inversion of the original.

Wrap-around is performed with the above functions, so the previous Digit to Zero is Nine, and Three added to Eight is One, etc.

When inverting a Digit, Zero becomes Nine, One becomes Eight, etc.

### Other Functions 

The other functions provided are:

Returns a sequence containing...

- `allDigits` : ...all the possible Digits from Zero to Nine (inclusive);
- `nonZeroDigits` : ...the Digits from One to Nine (inclusive).

### Active Patterns 

The active patterns provided are:

- `|DigitIsZero|DigitIsNotZero|` : Is the Digit a Zero or not?
- `|DigitIsEven|DigitIsOdd|` : Is the Digit even or odd?

#### Code Examples

```fsharp 
let three = '3' |> Digit.fromChar // -> Three

let invalidChar 'x' |> Digit.fromChar // -> Raises an exception

let threeChar = three |> Digit.toChar // -> '3'

let threeValue = three |> Digit.toInt // -> 3

let threeName = three |> Digit.toString // -> "three"

let previous = three |> Digit.previous // -> Two 

let inverted = three |> Digit.invert // -> Six
```

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
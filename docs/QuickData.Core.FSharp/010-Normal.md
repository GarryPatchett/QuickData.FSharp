# QuickData.Core.FSharp

# Normal

This type is a value which is clamped to the range of 0.0 to +1.0 (inclusive).

- The [Normal Module](#the-normal-module)
    - [Operators](#operators)
    - [Construction Functions](#construction-functions)
    - [Deconstruction Functions](#deconstruction-functions)
    - [Variation Functions](#variation-functions)
    - [Ready-made Values](#ready-made-values)
    - [Code Examples](#code-examples)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The Normal Module 

The `Normal` **module** provides operators and functions for working with a Normal.

> **Note:** When a Normal is printed via structured formatting - e.g. `printf "%A"` - the value will be
prefixed with a 'N', e.g. `N0.5`. You would not usually print a Normal but this might be useful to know.

### Operators

The operators provided are:

- `+` : Adds two Normals together (equivalent to the `add` function);
- `-` : Subtracts one Normal from another Normal (equivalent to the `subtract` function);
- `*` : Multiplies one Normal by another Normal (equivalent to the `multiply` function);
- `/` : Divides one Normal by another Normal (equivalent to the `divide` function);

The methods provided are:

- `Value` : Returns the value of a Normal as a float (equivalent to the `toFloat` function).

### Construction Functions 

The construction functions provided are:

- `fromFloat` : The usual way to manually create a Normal;
- `fromBoolean` : Creates a new Normal from a bool.

### Deconstruction Functions 

The deconstruction functions provided are:

- `toFloat` : Returns the value of a Normal as a float (equivalent to the `Value` method);
- `toBoolean` : Creates a bool from a Normal.

### Variation Functions 

The variation functions provided are:

- `add` : Adds two Normals together (equivalent to the `+` operator);
- `subtract` : Subtracts one Normal from another Normal (equivalent to the `-` operator);
- `multiplyBy` : Multiplies one Normal by another Normal (equivalent to the `*` operator);
- `divideBy` : Divides one Normal by another Normal (equivalent to the `/` operator);
- `scale` : Scales one Normal by another Normal (equivalent to the `multiplyBy` function);
- `invert` : Creates a new Normal which is an inversion of the original;
- `flattenDown` : Creates a new Normal which is the lower of the original and a provided level;
- `flattenUp` : Creates a new Normal which is the higher of the original and a provided level.

Inverting a Normal takes the value of the original, subtracts that from +1.0, and then
creates a new Normal from that new value.

### Ready-made Values

The `Normal` **module** also provides various ready-made values which make it easy to specify some often-used Normals.

These values are:

- `minimum` = 0.0 ; the lowest possible value;
- `oneTenth` = 0.1;
- `oneFifth` = 0.2;
- `oneQuarter` = 0.25;
- `twoFifths` = 0.4;
- `oneThird` = 1.0 / 3.0 = 0.33333...;
- `oneHalf` = 0.5;
- `threeFifths` = 0.6;
- `twoThirds` = 1.0 / 3.0 * 2.0 = 0.66666...;
- `threeQuarters` = 0.75;
- `fourFifths` = 0.8;
- `maximum` : 1.0 ; the highest possible value.

#### Code Examples

```fsharp 
let okay = Normal.fromFloat 0.85 // -> Normal 0.85 

let tooLow = Normal.fromFloat -0.5 // -> Normal 0.0 

let tooHigh = Normal.fromFloat 1.2 // -> Normal 1.0 

let value = Normal.oneTenth |> Normal.toFloat // -> float 0.1 

let added = Normal.fromFloat 0.4 + Normal.fromFloat 0.3 // Normal 0.7 

let subtracted = 
    Normal.fromFloat 0.9 
    |> Normal.subtract (Normal.fromFloat 0.5) // Normal 0.4 

let invertedNormal = Normal.fromFloat 0.7 |> Normal.invert // -> Normal 0.3 
```

## Issues, Questions, and Suggestions

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.
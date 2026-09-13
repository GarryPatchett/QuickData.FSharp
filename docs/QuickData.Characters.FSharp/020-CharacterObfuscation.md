# QuickData.Characters.FSharp

# CharacterObfuscation

Defines various ways in which one character can be changed to one (or more) other character(s).

- The [CharacterObfuscation Type](#the-characterobfuscation-type)
- The [CharacterObfuscation Module](#the-characterobfuscation-module) with [code examples](#single-character-code-examples)
- [Discriminated Union Identity Values](#discriminated-union-identity-values)
- [Exception-free Processing](#exception-free-processing)
- [Issues, Questions, and Suggestions](#issues-questions-and-suggestions)

## The CharacterObfuscation Type

The `CharacterObfuscation` **type** defines a discriminated union used to specify how characters can be obfuscated.

The cases are:

| Case Name                 | Obfuscation                                                                                       |
| ------------------------- | ------------------------------------------------------------------------------------------------- |
| **NoObfuscation** **1*    | No obfuscation will be performed - character out = character in                                   |
| **Munge** **2*            | Converts some characters to a different character which looks a bit like the original             |
| **Leet** **3*             | Converts some characters to a sequence of one or more different characters                        |

- **1* : The default case.
- **2* : Single character to single character, e.g. 'B' -> '8'; 's' -> '5', etc.
- **3* : Single character to either single character or multiple characters, e.g. 'E' -> seq { '3' }, or 'K' -> seq{ '|' ; '<' }, etc.

To specify a character obfuscation simply supply its name, such as `CharacterObfuscation.Munge`.

> **Notes:** 
>
> 4. Character obfuscation only affects characters which are defined in internal tables;
all other characters remain unaffected by character obfuscation.
>
> 5. Different people/groups have their own ideas about which characters are correct for munging and leeting, 
but since the aim of these functions is simply to get a sequence of characters,
rather than for communication, that's not considered to be relevant here.
>
> 6. Obfuscating characters for the purposes of making a password may not make that password more secure.
Seek good advice before using this functionality for the creation of passwords.

## The CharacterObfuscation Module

The `CharacterObfuscation` **module** defines various functions which work with characters for the purposes of character obfuscation.

These functions are:

- `obfuscate` : Returns a sequence of char where the original character has (possibly, see above) been obfuscated;
- `Seq.obfuscate` : Returns a sequence of char where the characters in the source sequence have (possibly, see above) been obfuscated.

#### Single Character Code Examples

```fsharp 
let same = 
    's' |> CharacterObfuscation.obfuscate CharacterObfuscation.NoObfuscation 
    // -> 's'

let munge = 
    's' |> CharacterObfuscation.obfuscate CharacterObfuscation.Munge 
    // -> seq { '5' }

let leet = 
    'U' |> CharacterObfuscation.obfuscate CharacterObfuscation.Leet 
    // -> seq { '(' ; '_' ; ')' }
```

#### Character Sequence Code Examples

```fsharp 
let same = 
    seq { 'a' ; 'c' ; 'e' } 
    |> CharacterObfuscation.Seq.obfuscate CharacterObfuscation.NoObfuscation 
    // -> seq { 'a' ; 'c' ; 'e' }

let munge = 
    seq { 'c' ; 'a' ; 't' } 
    |> CharacterObfuscation.Seq.obfuscate CharacterObfuscation.Munge 
    // -> seq { '(' ; '@' ; '+' }

let leet = 
    seq { 'D' ; 'O' ; 'G' } 
    |> CharacterObfuscation.Seq.obfuscate CharacterObfuscation.Leet 
    // -> seq { '|' ; ')' ; '0' ; '9' }
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
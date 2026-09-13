# QuickData.FSharp 

This is the public repository for the QuickData.FSharp packages.

Together these packages allow you to quickly create sequences of various types.

## Contents

- [Overview](#overview)
- [Installation](#installation)
- [Learning](#learning)
- [Questions and Reporting Issues](#questions-and-reporting-issues)
- [Usage](#usage)

## Overview

This QuickData.FSharp project contains five packages:

| Package                        | What It's For | Documentation | Package |
| ------------------------------ | ------------- | ------------- | ------- |
| **QuickData.Core.FSharp**      | Contains shared types and functionalities | [Core docs](docs/QuickData.Core.FSharp/000-Overview.md "Core package documentation") | [Core package](https://www.nuget.org/packages/QuickData.Core.FSharp "Core package") |
| **QuickData.Digits.FSharp**  | Create sequences of Digit | [Digits docs](docs/QuickData.Digits.FSharp/000-Overview.md "Digits package documentation") | [Digits package](https://www.nuget.org/packages/QuickData.Digits.FSharp "Digits package") |
| **QuickData.Numbers.FSharp**  | Create sequences of numbers | [Numbers docs](docs/QuickData.Numbers.FSharp/000-Overview.md "Numbers package documentation") | [Numbers package](https://www.nuget.org/packages/QuickData.Numbers.FSharp "Numbers package") |
| **QuickData.Characters.FSharp**    | Create sequences of characters | [Characters docs](docs/QuickData.Characters.FSharp/000-Overview.md "Characters package documentation") | [Characters package](https://www.nuget.org/packages/QuickData.Characters.FSharp "Characters package") |
| **QuickData.Words.FSharp**    | Create sequences of words/sentences | [Words docs](docs/QuickData.Words.FSharp/000-Overview.md "Words package documentation") | [Words package](https://www.nuget.org/packages/QuickData.Words.FSharp "Words package") |

You are not expected to install the `Core` package manually but should install one or more of the other
packages instead which will install everything that is necessary.

The documentation for the `Core` package [here](docs/QuickData.Core.FSharp/000-Overview.md "Core package documentation") contains very useful general information.

The documentation for the `Digits` package [here](docs/QuickData.Digits.FSharp/000-Overview.md "Digits package documentation") can be referred to when creating sequences of Digit.

The documentation for the `Numbers` package [here](docs/QuickData.Numbers.FSharp/000-Overview.md "Numbers package documentation") can be referred to when creating sequences of numbers.

The documentation for the `Characters` package [here](docs/QuickData.Characters.FSharp/000-Overview.md "Characters package documentation") can be referred to when creating sequences of characters.

The documentation for the `Words` package [here](docs/QuickData.Words.FSharp/000-Overview.md "Words package documentation") can be referred to when creating sequences of words/sentences.

Various types and modules are provided in the packages and the documentation for such can be found in the
documentation for the relevant package.

The documentation files for each package have a numerical prefix and are ordered in such
a way that it would be beneficial to the reader if they read them in ascending order of this numerical prefix,
but you can dip in to whichever part of the documentation you want to read at any time.

> **IMPORTANT:** There is no code in this repository as **the software is NOT open source**. You can install and use the packages pretty
much anywhere you like but **you have NO RIGHT** to modify the code/project, make any claim of ownership/authorship of the code/project,
make derivatives of the code/project, or various other things. (You can use it for free but please be decent about it.)

## Installation

You can use the `QuickData.FSharp` project within a script or within your own code.

(The examples below use the `Numbers` package. You should specify the package which you want to use.
You don't need to specify the `Core` package unless that is the only package you are interested in.)

If you are just looking to explore the project, or use it to produce something quickly, you
can access the project like this in a script:

```fsharp
#r "nuget: QuickData.Numbers.FSharp"
```

Or, to use it in your own code, add the `QuickData.Numbers.FSharp` Nuget package to your F# project, like this:

```console
dotnet add package QuickData.Numbers.FSharp
```

> **REMEMBER:** Intellisense documentation is available for all of the types and functions which you might need to use.
It is recommended that you refer to that documentation often until you are comfortable in knowing what each type does and how it works.

## Learning

It is recommended that you select a package which you are interested in and then try the example code in the documentation
for that package to get an idea of how things work. Once you see how the examples work, try experimenting and see what
happens.

There's nothing particularly complicated in these packages but the shear amount of 'stuff' to learn can
be daunting so learning things bit-by-bit should make for a more comfortable process.

> **Note:** The code examples only cover a small selection of the possibilities of the packages.
There is so much to see and learn that you might need to put some time aside to really get to grips with what's possible.

## Questions and Reporting Issues

You can visit the *[QuickData.FSharp](https://github.com/GarryPatchett/QuickData.FSharp "Home page for the QuickData project")* GitHub repository to report issues, 
ask questions, or make suggestions. You can also read about the changes across different versions in the release notes there.

> **Note:** I don't visit GitHub regularly so it may take some time for you to get a response.

## Usage

The types and functions in these packages have been designed to be used only with F#.

However, they may also be usable with C# but this has not been tested, so use them with C# at your own risk.
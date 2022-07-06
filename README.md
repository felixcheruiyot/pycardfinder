# PyCardFinder

PyCardFinder is a cross-platform tool for searching filesystems for credit card information written in Python.

PyCardFinder is greatly inspired by [CCSRCH](https://github.com/adamcaudill/ccsrch). CCSRCH works well when you have a few directories to check, but you end up getting a lot of false positives when your scope is large.

PyCardFinder solves this problem by trying to analyse the type of files under observation and intelligently filter out the false positives.

## Features

- Card number validation using Luhn algorithim
- Ability to specify a number of files paths and extensions to ignore during scan
- Detailed report i.e including line number in file where an incident has been identified

## Assumptions

The following assumptions are made throughout the program searching for the card numbers:

- Cards can be a minimum of 14 numbers and up to 16 numbers.
- Card numbers must be contiguous. The only characters ignored when processing the files are dashes, carriage returns, new line feeds, and nulls.
- Files are treated as raw binary objects and processed one character at a time.
- Solo and Switch cards are not processed in the prefix search.
- Compressed or encoded files are NOT uncompressed or decoded in this version. These files should be identified separately and the program run on the decompressed or decoded versions.

## How to use

### Installation

    pip install pycardfinder

### Detect cards under specific folder

    pycardfinder --path="/home/user/Downloads"


### Specify folders and extensions to ignore items list during run

    pycardfinder --path="/home/user/Downloads" --ignore_items=.list,test,.pyc

### Run and output results to a file

    pycardfinder --path="/home/user/Downloads" > out.log
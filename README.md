# Mikro Assembler

![Screenshot of Mikro Assembler interface](images/mikro-assembler-start.png)


## Introduction

The Mikro Assembler is a cartridge for the Commodore 64/VIC 20, released by Supersoft in the early 1980s and written by Andrew J Trott. It offers a unique way to write assembly code, using line numbers like writing BASIC code. The cartridge allows users to `LOAD`, `SAVE`, and `VERIFY` their code to disk or tape, and it includes a machine code monitor called `TIM`.


## Downloads

The following items are available for download from this repository:

* [Mikro Assembler Cartridge (modified with correct cartridge ID for emulators)](downloads/cartridges/Mikro%20Assembler%20[vice].crt)
* [Mikro Assembler Cartridge (original cartridge dump)](downloads/cartridges/Mikro%20Assembler.crt)
* [Multi Easy Easyflash Cartridge](downloads/cartridges/Multi-Easy.crt) by [Lord Crass](https://csdb.dk/scener/?id=25177), includes a version of the Mikro Assembler that works on my hardware. ([source](https://csdb.dk/release/?id=117893)).
* [Mikro Assembler Manual](downloads/Mikro%20Assembler%20Manual.pdf)


## Usage

* [List of BASIC Commands](Basic%20Commands.md)
* [List of Pseudo Opcodes](Pseudo-Ops.md)
* [Machine Code Monitor Commands](Machine%20Code%20Monitor%20Commands.md)


## Examples

The following examples demonstrate how to use the Mikro Assembler:

* [Hello World](examples/helloworld.md)
* [Hello World Inline](examples/helloworldinline.md)
* [10 PRINT](examples/10PRINT.md)
* [Border Colour](examples/borcol.md)
* [Key Beep](examples/keybeep.md)
* [Renumber](examples/renumber.md)
* [ASCII Organ](examples/asciiorgan.md)

You can download a disc image with the source code and assembled files for these examples from [examples.d64](examples/examples.d64).


## Summary

This repository provides everything you need to get started with the Mikro Assembler, including downloads of the cartridge, manual, and example code. With the Mikro Assembler, you can write assembly code using a familiar BASIC-style interface and take advantage of its built-in machine code monitor. Try it out for yourself!

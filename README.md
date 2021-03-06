Flamewing's BCD Test ROM
====
This is a test ROM for the Sega Genesis. Its purpose is to exhaustively test every single permutation of input for the 3 packed Binary Coded Decimal (BCD) instructions available in the Motorola 68000 processor and record any deviations from real hardware.

At present, the following emulators pass the test:

* [BlastEm](https://www.retrodev.com/blastem/)

Whereas the following emulators fail the test:

* [Gens rerecording](https://github.com/TASVideos/gens-rerecording)
* [Genesis Plus GX](https://github.com/ekeeke/Genesis-Plus-GX)
* [BizHawk](https://github.com/TASVideos/BizHawk)
* [Kega Fusion](http://www.carpeludum.com/kega-fusion/)
* [Regen](http://aamirm.hacking-cult.org/www/regen.html)
* [Exodus](http://www.exodusemulator.com/)

And probably lots more I didn't bother to test.

Real hardware naturally passes all tests; this has been verified on:

* Model 1 Sega Genesis
* Model 3 VA2 Sega Genesis

For reference, the original BCD data I used to reverse-engineer the operations was obtained from a Model 1. If you have other models to test, please let me know the results.

Considerations
----
For **abcd** and **sbcd** instructions, there are 256 possible values for each input register. They are also sensitive to **X** and **Z** flags. This gives a total of 256*256*4 = 262144 input combinations for each of **abcd** and **sbcd**.

One NTSC frame in the Sega Genesis corresponds to approximately 128000 cycles of the main 68000 CPU. Thus, every single cycle that the inner loop takes corresponds to one more NTSC frame.

For this reason, I just coded the whole thing in pure assembly and use a pre-generated results table.

How to use this
----
To build the ROM you will need a Unix-based OS. You will need [AS](http://john.ccac.rwth-aachen.de:8000/as/), g++ and build tools. Build AS, install somewhere in your path, then type 'make' to build the ROM.

Then load the ROM in your favorite emulator and let me know that it fails the test, so I can add it to the list.

# adlmidi
ADLMIDI is a MIDI player that uses OPL3 emulation.

![http://bisqwit.iki.fi/jutut/kuvat/programming_examples/midiplay.gif](http://bisqwit.iki.fi/jutut/kuvat/programming_examples/midiplay.gif)

## Key features

* OPL3 emulation with four-operator mode support
* FM patches from a number of known PC games, copied from files typical to AIL = Miles Sound System / DMX / HMI = Human Machine Interfaces / Creative IBK.
* Stereo sound
* Reverb filter based on code from SoX, based on code from Freeverb. A copy of either project is not needed.
* Number of simulated soundcards can be specified as 1-100 (maximum channels 1800!)
* xterm-256color support
* WIN32 console support (also tested with HXRT / MS-DOS)
* Pan (binary panning, i.e. left/right side on/off)
* Pitch-bender with adjustable range
* Vibrato that responds to RPN/NRPN parameters
* Sustain (a.k.a. Pedal hold) and Sostenuto enable/disable
* MIDI and RMI file support
* loopStart / loopEnd tag support (Final Fantasy VII)
* 111-th controller based loop start (RPG-Maker)
* Use automatic arpeggio with chords to relieve channel pressure
* Support for multiple concurrent MIDI synthesizers (per-track device/port select FF 09 message), can be used to overcome 16 channel limit
* Support for ScummVM, Doom, IMF, XMI and CMF files
* Support for custom banks of [WOPL format](https://github.com/Wohlstand/OPL3BankEditor/blob/master/Specifications/WOPL-and-OPLI-Specification.txt)
* Partial support for GS and XG standards (having more instruments than in one 128:128 GM set and ability to use multiple channels for percussion purposes, and a support for some GS/XG exclusive controllers)
* CC74 "Brightness" affects a modulator scale (to simulate frequency cut-off on WT synths)
* Portamento support (CC5, CC37, and CC65)
* SysEx support that supports some generic, GS, and XG features
* Full-panning stereo option (works for emulators only)
* This project is developed in C++, but a GW-BASIC version is also provided (MIDIPLAY.BAS). This player was first implemented in GW-BASIC for a Youtube demonstration video! With alterations that take 15 seconds to implement, it can be run in QBasic and QuickBASIC too. Note: The GW-BASIC version does not contain all of the same features that the C++ version does.

## Usage

```
Usage: adlmidi <midifilename> [ <options> ] [ <banknumber> [ <numcards> [ <numfourops>] ] ]
       adlmidi <midifilename> -1   To enter instrument tester
 -p Enables adlib percussion instrument mode (use with CMF files)
 -t Enables tremolo amplification mode
 -v Enables vibrato amplification mode
 -s Enables scaling of modulator volumes
 -frb Enables full-ranged CC74 XG Brightness controller
 -nl Quit without looping
 -nr Disables the reverb effect
 -w [<filename>] Write WAV file rather than playing
 -d [<filename>] Write video file using ffmpeg
 -fp Enables full-panning stereo support
 --emu-nuked  Uses Nuked OPL3 v 1.8 emulator
 --emu-nuked7 Uses Nuked OPL3 v 1.7.4 emulator
 --emu-dosbox Uses DosBox 0.74 OPL3 emulator
    Banks: 0 = AIL (Star Control 3, Albion, Empire 2, etc.)
           1 = Bisqwit (selection of 4op and 2op)
           2 = HMI (Descent, Asterix)
           3 = HMI (Descent:: Int)
           4 = HMI (Descent:: Ham)
           5 = HMI (Descent:: Rick)
           6 = HMI (Descent 2)
           7 = HMI (Normality)
           8 = HMI (Shattered Steel)
           9 = HMI (Theme Park)
          10 = HMI (3d Table Sports, Battle Arena Toshinden)
          11 = HMI (Aces of the Deep)
          12 = HMI (Earthsiege)
          13 = HMI (Anvil of Dawn)
          14 = DMX (Doom 2)
          15 = DMX (Hexen, Heretic)
          16 = DMX (DOOM, MUS Play)
          17 = AIL (Discworld, Grandest Fleet, etc.)
          18 = AIL (Warcraft 2)
          19 = AIL (Syndicate)
          20 = AIL (Guilty, Orion Conspiracy, TNSFC ::4op)
          21 = AIL (Magic Carpet 2)
          22 = AIL (Nemesis)
          23 = AIL (Jagged Alliance)
          24 = AIL (When Two Worlds War :MISS-INS:)
          25 = AIL (Bards Tale Construction :MISS-INS:)
          26 = AIL (Return to Zork)
          27 = AIL (Theme Hospital)
          28 = AIL (National Hockey League PA)
          29 = AIL (Inherit The Earth)
          30 = AIL (Inherit The Earth, file two)
          31 = AIL (Little Big Adventure :: 4op)
          32 = AIL (Wreckin Crew)
          33 = AIL (Death Gate)
          34 = AIL (FIFA International Soccer)
          35 = AIL (Starship Invasion)
          36 = AIL (Super Street Fighter 2 :4op:)
          37 = AIL (Lords of the Realm :MISS-INS:)
          38 = AIL (SimFarm, SimHealth :: 4op)
          39 = AIL (SimFarm, Settlers, Serf City)
          40 = AIL (Caesar 2, :p4op::MISS-INS:)
          41 = AIL (Syndicate Wars)
          42 = AIL (Bubble Bobble Feat. Rainbow Islands, Z)
          43 = AIL (Warcraft)
          44 = AIL (Terra Nova Strike Force Centuri :p4op:)
          45 = AIL (System Shock :p4op:)
          46 = AIL (Advanced Civilization)
          47 = AIL (Battle Chess 4000 :p4op:)
          48 = AIL (Ultimate Soccer Manager :p4op:)
          49 = AIL (Air Bucks, Blue And The Gray, etc)
          50 = AIL (Ultima Underworld 2)
          51 = AIL (Kasparov's Gambit)
          52 = AIL (High Seas Trader :MISS-INS:)
          53 = AIL (Master of Magic, :4op: std percussion)
          54 = AIL (Master of Magic, :4op: orchestral percussion)
          55 = SB (Action Soccer)
          56 = SB (3d Cyberpuck :: melodic only)
          57 = SB (Simon the Sorcerer :: melodic only)
          58 = OP3 (The Fat Man 2op set)
          59 = OP3 (The Fat Man 4op set)
          60 = OP3 (JungleVision 2op set :: melodic only)
          61 = OP3 (Wallace 2op set, Nitemare 3D :: melodic only)
          62 = TMB (Duke Nukem 3D)
          63 = TMB (Shadow Warrior)
          64 = DMX (Raptor)
          65 = OP3 (Modded GMOPL by Wohlstand)
          66 = SB (Jamie O'Connell's bank)
          67 = TMB (Default bank of Apogee Sound System)
          68 = WOPL (4op bank by James Alan Nguyen and Wohlstand)
          69 = TMB (Blood)
          70 = TMB (Lee)
          71 = TMB (Nam)
          72 = WOPL (DMXOPL3 bank by Sneakernets)
          73 = EA (Cartooners)
          74 = WOPL (Apogee IMF 90-ish)
     Use banks 2-5 to play Descent "q" soundtracks.
     Look up the relevant bank number from descent.sng.

     You can pass the file path instead of bank number
     to use a custom bank. (WOPL format is supported)

     <numfourops> can be used to specify the number
     of four-op channels to use. Each four-op channel eats
     the room of two regular channels. Use as many as required.
     The Doom & Hexen sets require one or two, while
     Miles four-op set requires the maximum of numcards*6.

     When playing Creative Music Files (CMF), try the
     -p and -v options if it sounds wrong otherwise.
```

# How to build
To build ADLMIDI you need to use the CMake:

```bash
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=Release ..
make
sudo make install
```

## Copying and contributing

ADLMIDI is distributed under the terms of the General Public License version 3 (GPL3).
The OPL3 emulator within is from DOSBox is licensed under GPL2+.
The FM soundfonts (patches) used in the program are imported from various PC games without permission from their respective authors. The question of copyright, when it comes to sets of 11 numeric bytes, is somewhat vague, especially considering that most of those sets are simply descendants of the patch sets originally published by AdLib Inc. for everyone's free use.
Patches (as in source code modifications) and other related material can be submitted to the primary author by e-mail at:Joel Yliluoma <bisqwit@iki.fi>

The author also wishes to hear if you use adlmidi, and for what you use it and what you think of it.

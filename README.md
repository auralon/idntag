Idntag
======

| **Linux** | **Mac** |
|-----------|---------|
| [![Linux](https://github.com/d99kris/idntag/workflows/Linux/badge.svg)](https://github.com/d99kris/idntag/actions?query=workflow%3ALinux) | [![macOS](https://github.com/d99kris/idntag/workflows/macOS/badge.svg)](https://github.com/d99kris/idntag/actions?query=workflow%3AmacOS) |

Idntag is a command-line tool that identifies artist and song name in 
specified audio files and updates their ID3-tag meta-data with correct data, 
and renames the files on format Artist_Name-Track_Name.

**Warning:** This tool modifies and renames its input files. The quality of song
identification is not perfect and may have some false detections. It is 
therefore recommended to first make a copy of the files to be identified, so
there is a backup in case the results are not good.

Example Usage
=============

    $ idntag tests/song.mp3 
    tests/song.mp3 : OK : tests/Broke_For_Free-Night_Owl.mp3
    $ ls tests/
    Broke_For_Free-Night_Owl.mp3
    $ ffprobe tests/Broke_For_Free-Night_Owl.mp3 2>&1 | grep -e artist -e title
    artist          : Broke For Free
    title           : Night Owl

Supported Platforms
===================
Idntag is developed and tested on Linux and macOS.

Installation
============
Pre-requisites Ubuntu:

    sudo apt install git cmake mp3info python3-pip libtag1-dev libchromaprint-dev ubuntu-restricted-extras ffmpeg

Pre-requisites Debian (incl. Debian-based like Raspbian):

    sudo apt install git cmake mp3info python3-pip libtag1-dev libchromaprint-dev ffmpeg

Pre-requisites Python:

    pip3 install pyacoustid pytaglib

Download the source code:

    git clone https://github.com/d99kris/idntag && cd idntag

Generate Makefile and build:

    mkdir -p build && cd build && cmake .. && make -s

Optionally run tests:

    ctest --output-on-failure

Optionally install in system:

    sudo make install

Usage
=====

General usage syntax:

    idntag [-h] [-k] [-v] [-w "_"] [-s path] [-f path] path [path ...]

Options:

    path                   Path of a file or directory to process
    -h, --help             Show this help message and exit
    -k, --keepname         Keep original filename
    -w, --whitespace_char  Character to replace whitespace with in filename (does not work when --keepname argument is used)
    -s, --success          Move successfully processed files to this directory
    -f, --fail             Move files that failed to process to this directory
    -v, --version          Show program's version number and exit

License
=======
Idntag is distributed under the MIT license. See LICENSE file.

Keywords
========
linux, macos, fingerprint, music, mp3, automatically tag.

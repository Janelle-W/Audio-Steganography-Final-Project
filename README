# StegoProject

# Description
StegoProject is a steganography application that hides and extracts secret messages in **8-bit mono WAV** files.  
It embeds message bits into the least significant bits (LSBs) of the audio data without noticeably affecting sound quality.

# Usage
The executable supports three run modes depending on the command-line arguments.

## 1. No Arguments
When run without arguments, the program displays usage examples and available command-line options.

**Example**
StegoProject.exe

## 2. Hide Mode
Embeds a message file into the specified cover WAV file to create a stego (encoded) WAV file.  
Each pair of successive byte values in the audio data is modified so that the LSBs (least significant bits) of their average represent the message data bits.

**Command**
StegoProject.exe -hide -c [cover file] -m [message file] (-o [stego file]) (-b [bitcount])

**Parameters**
- -c [cover file] — Input WAV file used to hide the message  
- -m [message file] — File containing the message to be hidden  
- -o [stego file] (optional) — Output WAV file (default: stego.wav)  
- -b [bitcount] (optional) — Number of LSBs used for embedding (default: 1)

**Example**
StegoProject.exe -hide -c input.wav -m secret.txt -o hidden.wav -b 2

## 3. Extract Mode
Extracts a hidden message from a stego WAV file by reading the LSBs of the average of each pair of successive audio byte values.

**Command**
StegoProject.exe -extract -s [stego file] (-o [message file]) (-b [bitcount])

**Parameters**
- -s [stego file] — Input stego WAV file containing the hidden message  
- -o [message file] (optional) — Output file for the extracted message (default: message.txt)  
- -b [bitcount] (optional) — Number of LSBs used during hiding (must match embedding setting)

**Example**
StegoProject.exe -extract -s hidden.wav -o recovered.txt -b 2

# How It Works
1. The program reads every pair of successive bytes from the WAV data.  
2. It computes their average.  
3. The LSBs of that average are either replaced (in hide mode) or read (in extract mode) according to the message bits and specified bit count.

This approach keeps the audio perceptually identical while embedding or retrieving hidden data.

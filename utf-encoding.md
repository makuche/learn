# TLDR - Unicode

- Unicode is a standard that aims to represent human language with unique numbers. Each character is encoded using a so called _code point_, e.g. tie latin latter `A` is assigned the number `65`.
- Most webpages (close to 100%) use UTF-8 encoding in 2023.
- There exist about 1.1 million code points, where around 15% are used and another 11% can be used privately, i.e. a font can ship its own symbols.
- Convention for point values: `U+1F4A9`. U+ is a prefix standing for Unicode, 1F4A9 is the code point in hexadecimal.
- UTF-(8|16|32) encodings store code points different in memory. The simplest one is UTF-32 (8 and 16 are not straight-forward), storing code points as 32-bit integers, occupying four bytes: ```U+1F4A9 -> 00 01 F4 A9```
- UTF-8 is a variable length encoding. Each code point is encoded by one to four bytes. In particular it is space-efficient for basic Latin.
- UTF-8 is compatible with ASCII: Code points 0..127 are ASCII, using the exact same bytes. E.g. the letter `A` is `U+0041` or in ASCII just `41`.
- UTF-8 has error detection and recovery bult in: The first bytes prefix is different from bytes 2-4, so its always possible to check if a valid sequence of UTF-8 bytes is available or if something is missing. 
- Important consequence: It's not possible to determine the string length by counting bytes, or work with substrings by jumping into the middle of the string.
- When checking the length of a string, different programming language will give you different answers for some strings like emojis. This is because different languages use different string representations (UTF-8, 16 or 32).
- String comparison or substring search should only be done after normalizing! Unicode offers many ways to write the same character, e.g. like ö
- Grapheme cluster representations are important for semantic related things, while byte views are for memory/copying/encoding/decoding related tasks
- For working with everything Unicode related, use a Unicode library


These notes are a summary of the following source: https://tonsky.me/blog/unicode/
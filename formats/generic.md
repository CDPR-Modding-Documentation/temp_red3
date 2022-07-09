# Generic

## USM File (Scaleform video file)

This is a multiplexed video file which means multiple files have been compressed into one file. There is always an m2v file and some adx files. The m2v file is the video and the adx files are the sound. Adx files can be converted to wav.

[https://github.com/Traderain/Wolven-kit/blob/master/W3Edit.Scaleform/CriUsmStream.cs](https://github.com/Traderain/Wolven-kit/blob/master/W3Edit.Scaleform/CriUsmStream.cs)

## SUBS File

* They can be opened with normal text editors
* First line: Start of the subtitle (miliseconds)
  * After that each line: (start in ms), (end in ms), text

### CSV File

These are normal excel sheet and can be opened with any text editor or microsoft excel.

### XML File

These are normal xml files and can be opened with any text editor.

### W3Speech file

```
          4 bytes for id (String), usually CPSW
          4 bytes for version (Number), usually A2 00 00 00 or A3 00 00 00
          2 bytes for key1 (Number), part of the language key
          variable amount of bytes for wavecr2w pair count
          for each wemcr2w pair:
            4 bytes for language specific id (Number)
            4 bytes for some other id (Number)
            4 bytes for absolute offset (Number), points at (a) down below 
            4 bytes of zeros
            4 bytes of (wem size + 12) (Number) (c)
            4 bytes of zeros
            4 bytes for absolute offset (Number), points at (b) down below
            4 bytes of zeros
            4 bytes of cr2w size (Number) (d)
            4 bytes of zeros
          2 bytes for key2 (Number), part of the language key
          for each wemcr2w pair:
            4 bytes for wem size (Number) (a)
            c - 12 bytes for wem (raw data)
            4 bytes for duration in seconds (Float)
            4 bytes of 04 00 00 00
            d bytes for cr2w (raw data) (b)
```

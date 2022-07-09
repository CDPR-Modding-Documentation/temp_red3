---
description: texture.cache
---

# Texture Cache



```
        // COMPRESSED FILES (each file has a header, the compressed bytes and (optionally) mipmaps
        --------------------------------
        public UInt32 CachedZSizeNoMips; //NOTE not counting appended mipmaps
        public UInt32 CachedSizeNoMips;
        public byte CachedMipsCount; //NOTE count of appended mipmaps
        public byte[CompressedSize] CompressedBytes;

        // (OPTIONAL) MipMaps (appended are any mipmaps, length = rest + (256 * PageCount) as entries: )
        public byte Rest;
        public UInt32 PageCount;
        public UInt16 dim1; //Width or Height
        public UInt16 dim2; //Heightor Width
        public byte[length] CompressedMipmapBytes;

        //INFOTABLE
        --------------------------------

        // MipMapsOffsetTable (4 bytes per entry * total mipmaps count):
        public Uint32 MipmapOffset; //NOTE MipMap offset is relative, counted from the beginning of the compressed file's offset

        // NamesTable (variable bytes per entry):
        public Cr2wString RelativeFilename; //NOTE (string, ended by nullbyte)

        // EntryinfoTable (52 bytes per entry * entries):
        public Int32 Hash;
        public Int32 PathStringIndex;
        public UInt32 PageOffset;
        public UInt32 ZSize;
        public UInt32 Size;
        public UInt32 BaseAlignment;
        public UInt16 BaseWidth;
        public UInt16 BaseHeight;
        public UInt16 TotalMipsCount;
        public UInt16 SliceCount;
        public Int32 MipOffsetIndex;
        public Int32 MipsCount;
        public Int64 TimeStamp;
        public Int16 Type;
        public Int16 IsCube;

        //FOOTER (const 32 bytes)
        --------------------------------
        public UInt64 Crc; //NOTE FNV1a64 over the Infotable (MipsOffsetTable, Namestable and EntryInfoTable)
        public UInt32 UsedPages;
        public UInt32 EntryCount;
        public UInt32 StringTableSize;
        public UInt32 MipEntryCount;
        public byte[4] IDString = { (byte)'H', (byte)'C', (byte)'X', (byte)'T' };
        public UInt32 Version= 6;
```

---
description: shader.cache
---

# Shader Cache

file structure:

```
Data_entry[Footer.dataentry_count] shaders
Table_entry[Footer.tableentry_count] materials?
Footer
```

Number of items: Footer.dataentry\_count

```
Data_entry:
{
   u8 hash
   u1 compression (only present in version > 2)
   u4 size (only present in version > 2)
   u4 zsize : compressed size in version > 2, entrysize in version < 3
   byte[zsize] compressed_data: zlib compressed bytes
}
```

Number of items: Footer.tableentry\_count

```
Table_entry:
{
   u4 top
   u4 header1
   u8 header2
   u8 header3
   vlq_bit6_prefixed_string name
   u4 top2 : same as top1
   u8 lower1
   u8 lower2
   byte[36] unk2
   u4unkarray unk3
   u4stringarray strings1
   u4stringarray strings2
}
```

```
vlq_bit6_prefixed_string:
{
   vlq_bit6 len
   bytes[len] value
}
```

```
vlq_bit6:
{
   1 bit sign
   1 bit continuation
   6 bit value
  ... shift bits by 7 afterwards
}
```

```
u4unkarray:
{
   u4 count
   byte[32][count] list
}
```

```
u4stringarray:
{
   u4 count
   stringlistentry[count] list
}
```

```
stringlistentry:
{
   vlq_bit6_prefixed_string val
   u1 idx
}
```

## Footer

```
Footer:
{
   u4 dataentry_count
   u4 tableentry_count
   u8 unk2
   u8 table_offset
   u8 table_size
   u8 table_offset again?
   u4 magic : RDHS
   u4 version
}
```

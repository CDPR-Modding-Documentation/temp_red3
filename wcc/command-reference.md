# Command Reference

## analyze

> Analyze game and engine data and output cook lists

**Usage:**

* analyze  -out  \[optional params] &#x20;

Avaiable analyzers:

* world - Analyzes (hierarchicly) the world files &#x20;
* r4res - Analyze resources from the R4 game &#x20;
* r4items - Analyze items from the R4 game &#x20;
* r4game - Analyze game resource from the R4 game definition file (but not worlds) &#x20;
* r4common - Analyze game common resources &#x20;
* r4gui - Analyze related to R4 gui &#x20;
* r4startup - Analyze game & engine startup resources &#x20;
* r4dlc - Analyze DLC directory from the R4 game &#x20;

## splitcache

> Split cache file into multiple files

**Usage:**

*   splitcache  -file= -db= -outdir=

    Options:
* &#x20;\- what kind of cache you want to split (physics, texture, etc)
* \-file= - input cache file
* \-db= - path to the cook.db file to use as a reference
* \-outdir= - where to place output caches
* \-strip - remove data from non cooked files
* \-fallback= - use custom fallback chunk name

## reportchunks

> Reports file usage and chunk distribution of a given cook database.

**Usage:**

* reportchunks -db= -out=&#x20;

Options:

* \-showall         - Outputs exhaustive report (default).
* \-showsumary      - Outputs global statistics.
* \-showextensions  - Outputs extension/chunk statistics.
* \-showfilechunks  - Outputs file/chunk statistics (slow!).
* \-showchunkfiles  - Outputs the list of files in each chunk (slow!).

## dumpbundleinfo

> Dumps info for bundled files.

**Usage:**

* dumpbundleinfo -indir= -outpath=
* \-indir=    - Directory with the bundles (recursive).
* \-infile=   - Absolute path to input bundle (multiple can be specified).
* \-outfile=  - Absolute path to output text file.

## dumpscripts

> Dump data from compiled scripts

**Usage:**

* dumpscripts -file= -out=

Exclusive options:

* \-file=    - Input file (compiled script binary)
* \-out=            - Output report file

## export

> Export single assets from the engine

**Usage:** export -depot= -file= -out=

* Params:
  * \-depot=local          - Use local depot (r4data)
  * \-depot=absolutepath   - Use depot at given directory
  * \-file=relativepath    - Local (depot) path for the file to export
  * \-out=absolutepath     - Output absolute path for the exported file
  * \-fbx=fbxversion       - (Optional) Specify output FBX version - 2016, 2013, 2011, 2010, 2009
* Supported resource types and formats:
  * w2mesh (Mesh) exportable into 5 file format(s):
    * fbx: Autodesk fbx 2016
    * fbx: Autodesk fbx 2013
    * fbx: Autodesk fbx 2011
    * fbx: Autodesk fbx 2010
    * fbx: Autodesk fbx 2009
  * xbm (2D Texture) exportable into 5 file format(s):
    * dds: DirectDraw Surface
    * bmp: Windows Bitmap
    * jpg: Joint Photographics Experts Group
    * tga: Truevision Targa
    * png: Portable Network Graphics&#x20;

## gluefiles

> Glues files into optimal files

**NO INFO**

## gluefilesdlc

> Glues files into optimal files

**NO INFO**

## import

> Import assets into the engine

**Usage:**

* import -depot= -file= -out=
* Params:
  * \-depot=local                - Use local depot (r4data)
  * \-depot=absolutepath        - Use depot at given directory
  * \-file=inputfile            - Absolute path to file to import
  * \-out=outputfile            - Relative (depot) path for the output file
  * \-texturegroup=nameofgroup    - (Optional) Name of texture group when importing texture
* Supported texture group names:
  * BillboardAtlas
  * CharacterDiffuse
  * CharacterDiffuseWithAlpha
  * CharacterEmissive
  * CharacterNormal
  * CharacterNormalHQ
  * CharacterNormalmapGloss
  * Default
  * DetailNormalMap
  * DiffuseNoMips
  * Flares
  * FoliageDiffuse
  * Font
  * GUIWithAlpha
  * GUIWithoutAlpha
  * HeadDiffuse
  * HeadDiffuseWithAlpha
  * HeadEmissive
  * HeadNormal
  * HeadNormalHQ
  * MimicDecalsNormal
  * NormalmapGloss
  * NormalsNoMips
  * Particles
  * ParticlesWithoutAlpha
  * PostFxMap
  * QualityColor
  * QualityOneChannel
  * QualityTwoChannels
  * SpecialQuestDiffuse
  * SpecialQuestNormal
  * SystemNoMips
  * TerrainDiffuse
  * TerrainNormal
  * WorldDiffuse
  * WorldDiffuseWithAlpha
  * WorldEmissive
  * WorldNormal
  * WorldNormalHQ
  * WorldSpecular
* Supported resource types and formats:
  * xbm (2D Texture) importable from 5 file format(s):
    * dds: DirectDraw Surface
    * bmp: Windows Bitmap
    * jpg: Joint Photographics Experts Group
    * tga: Truevision Targa
    * png: Portable Network Graphics
  * w2mesh (Mesh) importable from 2 file format(s):
    * re: Red Engine File
    * fbx: Autodesk FBX

## loadtest

> Attempts to load all resources to check for errors.

## validate

> Validate resources

**Usage:**

* validate \[-db= -file= -all] -outdir=
* Exclusive options:
  * \-db=      - Validate files from given cook
  * \-file=   - Validate single file
  * \-all               - Validate all files in depot (not recommended)

## get\_txts

> Save Dialog Lines

**Usage:**

* get\_txts \[-db=] -outdir= \[-lang=]
  * Exclusive options:
* \-db=      - Validate files from given cook

## dumpfile

> Dump file content (objects)

**Usage:**

* dumpfile -file= -dir= -out=
  * Parameters:
  * \-dir=     - dump the whole directory (recursive)
  * \-file=   - depot path to the file
  * \-out=    - absolute path to the output file
  * \-exclude= - exclude given file extensions

## optimizecollisioncache

> Optimize (resort) collision cache

**Usage:**

* optimizecollisioncache -file= -out=

## patch

> Generalized commandlet for creating differential patches for specified type of content.

**Usage:**

* patch  -base=path -current=path|-mod=path \[-name=packagename] -outdir=path
  * Content types:
* "bundles" MODS + PATCH
* "shaders" PATCH ONLY
* "staticshaders" PATCH ONLY
* "furshaders" PATCH ONLY
* "speeches" PATCH ONLY
* "strings" PATCH ONLY
* "physics" PATCH ONLY
* "sounds" PATCH ONLY
* "specialcases" PATCH ONLY
* "textures" MODS + PATCH
  * Required parameters:
* \-base=path     - Path to the base build (GoldMaster)
* \-current=path  - (pro) Path to the current build (latest cook)
* \-mod=path      - Path to the cooked mod directory
* \-path=path     - Output directory where the patched content will be dumped.
*   \-name=name     - Output using custom directory name.

    > Note: you can use -mod OR -current params

## r4characters

> Extracts a list of character templates from cook.db

**Usage:**

* r4characters -db= -out=

## r4charactersdlc

> Extracts a list of character templates from cook.db

**Usage:**

* r4characters -db= -out=

## unbundle

> Unbundle the files

**Usage:**

* unbundle -dir= -outdir=
  * Parameters:
* \-dir=     - directory with the bundles (recursive)
* \-outdir=  - absolute path to output directory
* \-json=   - optional bundles.json dump (for repacking)

## dumpcharset

> Dumps the charset used in a given strings file (\*.w3strings).

**Usage:**

* dumpcharset -instringsfile= -outcharsetfile= \[options]
  * \-instringsfile     - Path to the input strings file.
  * \-outcharsetfile    - Path to the out charset file (if not given, default is used).
  * Options:
* \-outentriesfile=  - Dumps all string entries into filepath. Only in single file mode.
* \-directory=       - Path to base directory for recursive dump. Used with targetlanguage.
* \-language=        - Target language for recursive dump. Used with targetlanguage.

## uncook

> Uncooks resources from a given bundle set.

**Usage:**

* uncook -indir= -outdir= \[options]
  * \-indir    - Path to the bundled directory.
  * \-outdir   - Path to the unbundled directory.
  * Options:
* \-infile=     - Path to bundle file.
* \-skiperrors            - Upon failure, skips to the next file.
* \-targetdir=   - Relative inner path to be extracted.
* \-targetfile= - Relative inner file path to be extracted.
* \-unbundleonly          - Unbundles data without uncooking it.
* \-uncookonly            - Assumes data in unbundledir is unbundled already.
* \-uncookext=<...>       - Comma delineated list of file extensions to uncook. If options missing will uncook all av
* \-imgfmt=       - Image format for XBM files. Choose one of bmp, png, jpg, or tga. Default is tga.
* \-dumpswf               - Dump redswf files out.

## venc

> Create USMs

## WorldSceneDependencyInfoFiles

> Creates the .dep files Creates the .dep files needed for the database creation used by the Database Viewer.

## buildcache

> Build data cache from cooked assets

**Usage:**

* buildcache  -db  -out  \[optional params]
  * Avaiable cache builders:
* physics - Compile collision data for physics
* shaders - Compile shaders for used materials
* textures - Compressed textures
  * Additional options:
* \-modulo=N      - Process every Nth file
* \-offset=X      - Initial offset for processing (use only with -modulo)
* \-db=     - Path to cook.db
* \-out=    - Path to output cache file

## metadatastore

> Generates a metadata.store file for the specified directory

## dependencies

> Build dependency cache file

**Usage:**

* dependencies -out= -report= \[-db=]
  * Arguments:
* out=     - Save dependency cache to file
* report=       - Generate dependency report in given directory
* db=      - Use dependencies in cook.db file instead of full depot

## exportbundles

> Build final bundle lists

**Usage:**

* exportbundles -db=\[cookerdb] -seed=\[seedfiles] -spatial=\[seedfiles] -out=\[outputfile]
  * Params:
* \-db=       - Cooker data base file
* \-seed=    - Initial list of seed files
* \-spatial= - Additional list of seed files that represent spatial configuration (they override the existing bundles)
* \-out=    - Absolute path to the final output file (JSON bundle list)
* \-split=     - Split bundles into chunks using given split file
* \-extrafast           - Use fast compression for bunles (much faster, larged output bundles)

## filever

> Check file versions

**Usage:**

* filever \[-ext=extensionlist] \[-file=file] \[-min=version] \[-verbose] \[-histogram]
  * Optional parameters:
* \-ext - Check only files with give extensions
* \-file - Check only given files
* \-min - Treat any file with version lower than given number as error
* \-verbose - Print all invalid files
* \-histogram - Print version histogram

## cook

> Cook file lists, generate cooked data and bundle files for packing

**Usage:**

* cook&#x20;
  * Platform:
* null    - Dummy cooker output (only cook.db)
* resave - Resave assets (no cooking, PC only)
* pc        - 64-bit PC
* ps4    - PlayStation 4
* xb1    - XBoxOne
  * Options:
* \-platform=    - Select target platform (required)
* \-outdir=      - Sepcify output directory (required)
* \-seed=        - Input seed file (required)
* \-file=        - Manual depot file for cooking
* \-noerrors           - Allow cooking errors
* \-noasserts          - Allow asserts
* \-silent             - No output
* \-ignore=      - Ignore files with given extension
* \-stringids=   - Capture and save all cooked string ID's
* \-stringkeys=  - Capture and save all cooked string key's
* \-excludedir=  - Don't cook resources from one directory
* \-trimdir=     - Cook resources only from one directory
* \-trimedfiles= - List of trimmed files from cook
* \-additionalDB=- Cook.db file to check if it containes trimmed files

## questlayoutdump

> Saves quest layout for use in external QuestDebugger.

**Use:**&#x20;

* wcc questlayoutdump -quest quest\_path -out dump\_path

## pack

> Packs file from given directory into a bundle

**Usage:**

* pack -dir= -outdir= \[-compression=LZ4|LZ4HC|ZLIB]
* \-dir = Input directory to pack
* \-outdir = Output directory with bundles (note: bundles bigger than 4GB are split)
* \-compression = Compression type to use (default: LZ4HC)

## resourceusage

> Export spatial resource usage information from a given world

**Usage:**

* resourceusage -world= -out= \[options]
  * Options:
* \-world=       - Specifies path to the world file (required)
* \-out=        - Sepcifies path to the output file (required)
* \-noerrors          - Allow cooking errors
* \-noasserts         - Allow asserts
* \-silent            - No output

## cooksubs

> Don't ask

**Use:**&#x20;

> wcc cooksubs font\_path subtitles\_path subtitles\_path needs to be ucs-2 little endian because of our engine the output file is utf8...

## cooksounds

> No operation

**Use:**

> wcc cooksounds output\_dir sound\_resource\_dir platforms

## split

> Split the files into content buckets

* Required usage:
  * split -db= \[-seed=]\* -out=
* Arguments:
  * \-db=            - Path to the cook.db file
  * \-seed=   - Path to the a seed file (multiple files supported)
  * \-out=                - Output file name
  * \-fallback=        - Specify custom fallback chunk for unassigned resources

## package

> Packs a world directories into a single dzip for faster loading and deployment on consoles.
>
> Creates streaming installer data for use by the game. Supported cooking platforms: PS4. Use: wcc package (ps4|orbis) app \[ps4 app options]
>
> * ps4 app options:
>   * \-t=   | --tempdir=             -- temp directory. Optional
>   * \-i=   | --indir=               -- absolute path to final deliverable. E.g., z:\Build\_109641Change\_652889\PS4
>   * \-o=   | --outdir=              -- absolute path where to create gp4, pkg and iso
>   * \-l=   | --langdir=             -- absolute path to the language definitions. E.g., z:\dev\PublisherSpecific\R4\InternalDevelopment\PS4\language | --langs=\[language list]>     -- comma separated list of game languages to support. E.g., en,pl | --dftlang=\[language]          -- default game langauge. Must also be listed in the languages option. E.g., en

## splitstrings

> Splits strings and speech files for a given language based on JSON descriptor.

**Usage:**

* splitstrings \[-dlc] -splitfile= -idsfile= -keysfile= -indir= -outdir=&#x20;
  * \-dlc           - Run in the DLC mode (no per-chunk splitting)
  * \-splitfile     - Path to the split file (mapping resources to chunks, not required in DLC mode).
  * \-idsfile       - Path to the ids file (mapping resources to string ID's).
  * \-keysfile      - Path to the keys file \[optional]\(mapping resources to string Key's).
  * \-indir         - Path to the directory where the language files reside.
  * \-outdir        - Path to the directory where the split files will reside.
  * Options:
* \-dostrings       - Split strings only (everything is done by default).
* \-dospeech        - Split speech only (everything is done by default).
* \-language    - Add language  to the splitting plan (default is 'en').
* \-platform    - Add platform  to the splitting plan (default is 'pc').
* \-allincontent0   - Merges all chunks into content0 (debug option).
* \-allinsamefolder - Outputs all files in the same folder (debug option).

## swfdump

> Dump SWF stuff\
> Dumps SWF resources. Use wcc swfdump \[out directory]

## swfimport

> Bulk import resources preserving directory structure\
> Imports resources. Use wcc import \[option1 value1 \[option2 value2 \[...]]]
>
> * Options:
>   * fromAbsPath -- absolute path to scan inside
>   * toDepotPath -- depot path to import to

## resave

> Resaves resources and optionally submits the changes into P4.

**Usage:**

* resave -tmpdir= \[options]
  * \-tmpdir                - Absolute path to temporary folder.
  * Options:
* \-path=        - Base directory path to scan (full depot resave if not specified).
* \-ext=   - Comma-separated list of extensions to scan for (full resave if not specified).
* \-nosourcecontrol       - Disables version control (local resave).
* \-ignorefileversion     - Resave even if files are latest version.
* \-forcestreamingsetup   - Force reset and setup of streaming in world and layers (dangerous!).
* \-cl=           - Add resaved files into the given changelist (when enabled).
* \-submitwhenfinished    - Enables CL submit when finished (disabled by default).
* \-discardunchangeddata  - Discards files for which data has not changed (disabled by default, potentially slow).
* \-customresave          - Resaves only the given list of files.
  * Version control options:
  * \-p4user=username           -- username for Perforce
  * \-p4client=client           -- client (workspace) for Perforce
  * \-p4host=host               -- hostname for Perforce
  * \-p4password=password       -- password for Perforce
  * \-p4port=port               -- port for Perforce

## cookmaterials

> Cooks materials\
> Use:\
> wcc cookmaterials PLATFORM (-static) (-fastfx) (-allmaterials) (-material=\[path]) (-resaveCRC) (-fur\[=paths])\
> here should be the description of all the parameters..\
> ..meanwhile you can go and ask the engine team

## cookocclusion

> Generate occlusion for given worlds

**Use:**

> wcc cookocclusion -world=pathToWorldFileN \[-smallesOccluder=..] \[-smallestHole=..] \[-tileSize=..] \[-xMin=..] \[-xMax=..] \[-yMin=..] \[-yMax=..]

## calculateRuntimeOcclusionMemory

> Calculate required memory for runtime occlusion data for the level **Use:** wcc calculateRuntimeOcclusionMemory \[-density=..] -world=pathToWorldFile

## findDuplicates

> Find duplicate geometry for the level **Use:** wcc findDuplicates -world=pathToWorldFile \[-output=file]
>
> ## pathlib
>
> Generate navigation data for given world **Use:** wcc pathlib rootSearchDir filePattern

## cookstrings

> Cooks strings and speech database, given a list of languages and platforms.

**Usage:**

* cookstrings    -languages= -platforms=&#x20;
  * out\_dir        - Path to the directory where the caches will be stored.
  * source\_dir     - Path to the base directory where speech data resides.
  * db\_string\_view - SQL query.
  * languages      - List of languages to cook.
  * platforms      - List of platforms to cook for.
* Options:
  * \-skipspeech      - Cooks only strings.

## testcollisioncache

> Test asynchrnous collision cache access **Usage:** testcollisioncache -file=

## cookertest

> Test of wcc\
> Simply tests wcc.

## testmem

> Test memory framework, streaming, GC and resource management stability

**Usage:**

* testmem \[params]
  * Params:
* \-world     Path to the w2w file to load
* \-numiter   Number of test iterations
* \-numpoints Number of test points
* \-extents   Extents (around origin) to test

## voconvert

> Convert voiceover files from .wav to .ogg **Use:** wcc voconvert wwise\_bin\_dir voiceivers\_source\_dir platform languages (pc en ...)

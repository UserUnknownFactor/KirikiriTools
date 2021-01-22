# KirikiriTools
Tools for the Kirikiri visual novel engine. [Download page](../../releases)

## KirikiriDescrambler
Some Kirikiri games have their plaintext scripts (.ks/.tjs) scrambled or compressed. Such files can be recognized by the signature `FE FE XX FF FE` at the start, `XX` being `00`, `01` or `02`. KirikiriDescrambler turns them into regular text files which can be placed right back in the game - no rescrambling needed.

Usage: `KirikiriDescrambler .\data`

## KirikiriUnencryptedArchive
A DLL (named "version.dll") that makes games accept unencrypted .xp3 archives. By using this file, it's no longer necessary to identify and replicate the encryption for each game you work on; just create an unencrypted archive with the Xp3Pack tool (included in this repository), throw the version.dll in the game's folder, and you're done.

## TextUTF16y
Some games have their descarambled or plaintext scripts (.ks/.tjs) in Shift_JIS encoding. This causes games to crash on systems with non-Japanese locale. Use this tool to convert scripts to UTF-16LE encoding if game crashes with .tjs or .ks error. Generally it must be used after files are descrambled. 

Usage: `TextUTF16y .\data *.ks`

## Xp3Pack
Creates unencrypted .xp3 archives for use with the KirikiriUnencryptedArchive DLL. Unlike other packing tools, it sets all hashes in the file table to zero; this serves as a marker for the DLL to bypass the game's decryption for those files.

Usage: `Xp3Pack patch`

Where `patch` is a subfolder containing the files you want to include. This will create `patch.xp3` in the game folder. If the game already has its own `patch.xp3`, name your folder `patch2` and run `Xp3Pack patch2` instead. If the game already has a `patch2.xp3`, name your folder `patch3`, and so on.

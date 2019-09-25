fontconfig (AOSC)
=================

Experimental Fontconfig branch with Michal Srb's optimisation work. Merged to the latest FC.

* PDF documentation: https://www.theseus.fi/bitstream/handle/10024/124694/Srb_Michal.pdf?sequence=1
* Upstream issue: https://gitlab.freedesktop.org/fontconfig/fontconfig/issues/103

Rebasing and tagging
--------------------

```bash
git remote add upstream https://gitlab.freedesktop.org/fontconfig/fontconfig
# if doing a minor-version update OR preparing for upstreaming:
git pull --rebase upstream master
# if doing a patch-version update:
git pull upstream VER
```

Do note that the indentation rule is:
* indent with four spaces, but tabstop = 8
* use tabs for indents when possible to reduce filesize; pad the rest with spaces

Picking patches
---------------

If you are preparing to upstream the patch, you may want to squash together some commits. They are identified by headings below to account for changes in hashes in future rebases:

* FcCompareValueList strong/weak:
  * Refactor FcCompareValueList to take value_strong and value_weak
  * Split strong/weak score debug in FcCompareValueList 
* FcFontSetMatchInternal:
  * Optimize FcFontSetMatchInternal
  * Bring back FC_DBG_MATCH2 from pre-optimized ver
  * Correct score selection in FcFontSetMatchInternal
  * (optional) Add debug info to FcFontSetMatchInternal 
* Preprocessing:
  * Introduce framework for preprocessing values.
  * Add FcPreprocessFOO speeding up FcCompareFOO.
* Hot path:
  * Use (un)likely hints to optimize hot paths. 
  * Mark out some hot paths in FcCompareValueList

For a note on what is probably worth merging, see [this upstream comment](https://gitlab.freedesktop.org/fontconfig/fontconfig/issues/103#note_21635).

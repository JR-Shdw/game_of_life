# game_of_life

Conway's game of life as a terminal program in C, rendered through a
character-grid canvas. Written around 2016.

A menu offers three choices: start a new game, replay a saved board, or quit.
A new game asks for a size, seeds the grid with four hardcoded lines, runs up
to 9 generations or until the board stabilises, then writes the result to a
file named `level1`. Replaying reads a file named `level2` and runs 10
generations. Both filenames are hardcoded in `game.c`.

## Board file format

Plain text, as in the `level1` and `level2` files included here:

```
lg1          magic marker
40 20        width height
X -          the alive character, then the dead character
3 3 2 2 ...  cell coordinates
```

## Building

This will not build from a clone. It needs a separate library that is not in
this repository and is no longer obtainable.

`game.c` and `lifegame.c` compile against the `tools` module by
Jacques-Olivier Lapeyre, part of his Cfuns collection. The makefile expects it
already built as object files in a sibling directory `../tools0_50/`, and
links twenty of them:

```
tools.o jstr.o intarray.o array.o stringarray.o mfile.o jfile.o btree.o
dlist.o mempool.o charpix.o hcharpix.o himage.o ds_cell.o graph_core.o
graph_algos.o gll_Maths.o gll_buffer.o ascii_regular_char.o KVdatatrain.o
```

The original README pointed at `www.mulitparadigme.org` for that library.
That was a typo for *multiparadigme*, but it makes no difference now: neither
spelling resolves, so the source is gone from the web and the dependency
cannot be recovered from the address recorded here.

A partial copy of some of those modules, including `tools` itself, survives
in the sibling project `tools_C_harlock` -- though it is also an incomplete
snapshot with its own missing headers, so it is not a drop-in substitute.

## Notes

`makefile` is ISO-8859 encoded with CRLF line endings, the only file in the
repository that is not valid UTF-8. Left as-is rather than reencoded, since
it is part of how the project was originally written.

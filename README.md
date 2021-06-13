# MDBTools built for 32-bit Windows using MSYS2

_Thanks to <https://github.com/lsgunth/mdbtools-win> for getting this started!_

## Compiling Notes

_I had the biggest struggles trying to figure out how to get this to compile, so if anyone has a better process using MSYS2 directly, please let me know._

**This is what finally worked: <https://github.com/mdbtools/mdbtools/issues/107#issuecomment-815174567>**

- Read <https://github.com/mdbtools/mdbtools/blob/dev/README.md>
- Clone <https://github.com/git-for-windows/git-sdk-64>
- Clone <https://github.com/mdbtools/mdbtools> into `git-sdk-64` folder
- Launch MinGW32 (I just ran `mingw32` from the `git-sdk-64` folder)

```sh
cd mdbtools
autoreconf -i -f
./configure
make all
make install    # may not actually be necessary
```

- Test some of the commands inside MinGW32 to make sure they function; `mdb-ver -M` is a reasonable one

## Collecting Relevant Files

_Still in MingW32 for this_

```sh
cd
mkdir /mdbtools-win
cp -p /mdbtools/src/COPYING* /mdbtools-win/
cp -p /mdbtools/src/util/.libs/*.exe /mdbtools-win/
cp -p /mdbtools/src/sql/.libs/*.dll /mdbtools-win/
cp -p /mdbtools/src/libmdb/.libs/*.dll /mdbtools-win/
cp -p /mingw32/bin/libgcc*.dll /mdbtools-win/
cp -p /mingw32/bin/libiconv*.dll /mdbtools-win/
cp -p /mingw32/bin/libreadline*.dll /mdbtools-win/
cp -p /mingw32/bin/libtermcap*.dll /mdbtools-win/
cp -p /mingw32/bin/libwinpthread*.dll /mdbtools-win/
```

Copy to where you want and use for good.

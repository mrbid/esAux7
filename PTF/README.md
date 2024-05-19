- `make` to compile
- place all of your [vertex colored](https://github.com/vertexcolor) [PLY](https://paulbourke.net/dataformats/ply/) files into the `ply` directory.
- run `./doall.sh` and all of the PLY files will be coverted to C header files and placed into the `high` directory.

The directory is named high for "higest quality" the concept is that you could then output medium and low quality directories from decimated versions of the original PLY file meshes.
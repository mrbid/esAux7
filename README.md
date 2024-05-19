## An OpenGL ES 1.1 framework for rendering [Vertex Colors](https://github.com/vertexcolor)

This code will operate on pretty much any device including web browsers using [Emscripten](https://emscripten.org/).

I prefer to use [GLFW](https://www.glfw.org/) to render OpenGL graphics to a window, but [SDL](https://www.libsdl.org/) is not bad too and includes more than just a graphics and input subsystem, such as an audio subsystem too.

The code includes the [PLY](https://paulbourke.net/dataformats/ply/) to C Header File conversion utilities [PTO](PTO) and [PTF](PTF), the simplified render [esAux7.h](esAux7.h), and a concise [Matrix](mat.h) and [Vector](vec.h) library although I highly recommend that you write most vector and matrix operations in-line and not to use external helper functions where reasonable as using canned functions can easily lead to oversights that lead to inefficiencies. Don't rely on canned functions all the time!

⚠️ Be weary of using `esRand()` as it uses the modulo operator and that tends to not function the same across different platforms, for example using this function with Emscripten will lead to overruns by 1, e.g `esRand(3, 6)` will return 3-7 in WASM and 3-6 on Linux and Windows. Stick to using `esRandFloat()` and casting back to integer or `fRand()` in [vec.h](https://github.com/mrbid/esAux7/blob/main/vec.h#L99). The fastest random functions for real-time usage are in [vec.h](vec.h) with `srandf()` _(seed rand)_, `randf()` _(0-1)_, `randfc()` _(-1 to +1)_, `randfn()` _(normal random)_.

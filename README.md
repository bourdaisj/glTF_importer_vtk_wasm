# glTF Importer VTK WebAssembly

## Build

Use the `kitware/vtk-wasm` docker image to compile the project to WASM with emscripten.
```bash
docker run --rm --entrypoint /bin/bash -v $PWD:/work -it kitware/vtk-wasm
mkdir build-emscripten && cd /work/build-emscripten

cmake .. \
  -GNinja \
  -DCMAKE_TOOLCHAIN_FILE=${CMAKE_TOOLCHAIN_FILE} \
  -DVTK_DIR=/VTK-install/Release/lib/cmake/vtk \
  -DCMAKE_BUILD_TYPE=Release

cmake --build .
exit
```

## Run

Once you're out of the container, cd into the `build-emscripten` folder and start a web server.
```bash
cd build-emscripten
python -m http.server 2000
```

Open browser at localhost:2000 and boom!

# WASM playground

## Compiling

### hello1
docker run --rm -v ./hello1/:/src emscripten/emsdk emcc hello.c -o hello.html

### hello2
docker run --rm -v ./hello1/:/src emscripten/emsdk emcc -o hello.html hello.c -O3 --shell-file html_template/shell_minimal.html

### hello3
docker run --rm -v ./hello3/:/src emscripten/emsdk emcc -o hello.html hello.c -O3 --shell-file html_template/shell_minimal.html -s NO_EXIT_RUNTIME=1 -s "EXPORTED_RUNTIME_METHODS=['ccall']"

## Serving

docker run --rm -v /hello1/:/src -p 8000:8000 python -m http.server

http://localhost:8000/hello.html

### More info
https://developer.mozilla.org/en-US/docs/WebAssembly/C_to_wasm

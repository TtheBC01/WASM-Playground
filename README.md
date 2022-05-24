# WASM Playground

Each subdirectory has a small hello-world example showing different aspects of compiling C/C++ into 
WebAssembly. Docker commands should be executed at the top-level directory. After you compile the 
C/C++ code into its artifacts, you must serve the resulting `.html` file from a http server in order 
for your browser to execute the WebAssembly correctly. 

## Compiling

### hello1

```shell
docker run --rm -v ./hello1/:/src emscripten/emsdk emcc hello.c -o hello.html
```

### hello2

```shell
docker run --rm -v ./hello1/:/src emscripten/emsdk emcc -o hello.html hello.c -O3 --shell-file html_template/shell_minimal.html
```

### hello3

```shell
docker run --rm -v ./hello3/:/src emscripten/emsdk emcc -o hello.html hello.c -O3 --shell-file html_template/shell_minimal.html -s NO_EXIT_RUNTIME=1 -s "EXPORTED_RUNTIME_METHODS=['ccall']"
```

## Serving

Run a simple python http server:

```shell
docker run --rm -v /hello1/:/src -p 8000:8000 python -m http.server
```

View the compiled page on your local network: 

http://localhost:8000/hello.html

## More info
https://developer.mozilla.org/en-US/docs/WebAssembly/C_to_wasm

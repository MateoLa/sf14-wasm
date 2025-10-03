<div align="center">

[<img src=https://stockfishchess.org/images/logo/icon_128x128.png></img>](https://stockfishchess.org)

<h3>Stockfish</h3>

<p>A free and strong UCI chess engine.</p>
<p>Analyzes chess positions and computes optimal moves.</p>
</div>

#### Description of the universal chess interface - UCI protocol

It is a command line protocol.

You will need to write to stdin ([UCI commands](https://backscattering.de/chess/uci/)) and listen to stdout.

Compiling stockfish generates a binary file `make build ARCH=x86-64-avx2 > build.log 2>&1`

#### WebAssembly 

Wasm is a binary instruction format for a stack-based virtual machine.

The code can be run in a modern browser to build a virtual machine which allows developers to run compiled codes (C++, Rust, etc.) on the client.

WebAssembly is designed to complement and run alongside JavaScript, sharing functionality between them.


### Prerequisites

* Install Emscripten

* Set working directory to stockfish/src/

* Build  `make -C .. emscripten_build ARCH=wasm` or `make -j build ARCH=wasm`

Build options can be set in /src/emscripten/Makefile

A non NNUE version is compiled with this values:
```sh
wasm_simd = yes
embedded_nnue = no
minify_js = no
assertion = no 
```

If you use the "minify_js" option, the version is compiled with warnings.

#### Added and Modified Files:

```sh
src/Makefile
src/emscripten/Makefile --> ML Modified
src/emscripten/embedded_nnue.h --> ML Modified
src/emscripten/misc/embedded_nnue.js --> ML Modified
src/emscripten/misc/timeit.hpp
src/emscripten/preamble.js --> Not used
src/emscripten/public/uci.js --> Not used
src/emscripten/utils.h
src/emscripten/wasm_simd.cpp
src/emscripten/wasm_simd.h
src/emscripten/worker-postamble.js --> Not used
src/evaluate.cpp
src/evaluate.h
src/misc.cpp
src/nnue/features/half_ka_v2_hm.h --> Not modified yet
src/nnue/layers/affine_transform.h
src/nnue/nnue_architecture.h --> Not modified yet
src/nnue/nnue_common.h
src/nnue/nnue_feature_transformer.h
src/search.cpp --> Not modified yet
src/tt.cpp
src/uci.cpp
```

### Acknowledgements

Thanks to the [Stockfish](https://github.com/official-stockfish/Stockfish) team and all its contributors.

The nnue-wasm compilation method (emscripten directory && Makefile) are based on [Hiroshi Ogawa](https://github.com/hi-ogawa/Stockfish) github repo.


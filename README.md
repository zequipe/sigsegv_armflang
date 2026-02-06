This repo tests what flags are needed to force LLVM compilers (flang, amdflang, armflang) to
allocate automatic arrays on the heap instead of the stack, to avoid stack overflow for large
arrays.

As of LLVM 21.1.8, the flags needed are
```
-mmlir -fdynamic-heap-array
```
In contrast, `-fno-stack-arrays` is not sufficient.

Run the [GitHub Action workflow](https://github.com/zequipe/sigsegv_armflang/actions/workflows/flang_heap_arrays.yml) to test when new versions of the compilers are released, to see if
the flags needed have changed.

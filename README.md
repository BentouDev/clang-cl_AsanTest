# clang-cl_AsanTest

## Project for testing address sanitizer in clang-cl

Run with params:
```
ASAN_OPTIONS=abort_on_error=false,halt_on_error=false,strict_string_checks=true,alloc_dealloc_mismatch=true,verbosity=1,print_stats=true
```

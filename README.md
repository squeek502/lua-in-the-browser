# lua-in-the-browser

This is the result of a
[2.5 hour live coding stream](https://youtu.be/DtZBac-IUBQ) in which I tried
to build [Lua](https://www.lua.org/) using [ZIG](https://ziglang.org/),
targeting [WebAssembly](https://webassembly.org/).

# Status

This depends on
[the changes to Zig in this branch of my fork](https://github.com/squeek502/zig/tree/lua-in-the-browser).

Able to produce `lib/lua.wasm`, however in the browser it is still not working.

Issues that need to be resolved:

- `malloc`/`free`/`realloc` need to be implemented somehow ([zee_alloc?](https://github.com/fengb/zee_alloc/blob/master/src/wasm_exports.zig))
- Missing libc functions:
  + localeconv
  + localtime
  + setlocale
  + clearerr
  + isxdigit
  + snprintf
  + strftime
  + difftime
  + freopen
  + realloc
  + fprintf
  + longjmp
  + tmpfile
  + setvbuf
  + strpbrk
  + tolower
  + iscntrl
  + ispunct
  + strcoll
  + ferror
  + fclose
  + fflush
  + fwrite
  + setjmp
  + ungetc
  + getenv
  + strcpy
  + strtod
  + gmtime
  + system
  + remove
  + rename
  + mktime
  + tmpnam
  + memchr
  + signal
  + fopen
  + fread
  + fgets
  + abort
  + fseek
  + ftell
  + atan2
  + log10
  + srand
  + clock
  + frexp
  + fputs
  + getc
  + feof
  + free
  + fabs
  + acos
  + asin
  + log2
  + rand
  + time
  + exit
  + cos
  + exp
  + log
  + sin
  + tan
  + pow

Note: File system functions use placeholder functions provided by Javascript at runtime.

# How to build it and run it

```
zig build install --prefix .
python3 -m http.server
```

Then visit the link printed with a modern browser such as Firefox.

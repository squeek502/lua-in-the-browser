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

- Missing libc functions:
  + localeconv
  + localtime
  + setlocale
  + snprintf
  + strftime
  + difftime
  + setvbuf
  + strpbrk
  + strcoll
  + strcpy
  + strtod
  + gmtime
  + mktime
  + memchr
  + srand
  + clock
  + rand
  + time

- `malloc`/`free`/`realloc` need to be implemented somehow ([zee_alloc?](https://github.com/fengb/zee_alloc/blob/master/src/wasm_exports.zig))
  + realloc
  + free

- libc functions that use a placeholder that prints a warning to the console:
  + setjmp
  + getenv

- libc functions that use a placeholder that throws an error at runtime:
  + longjmp
  + abort
  + exit
  + system
  + signal

- libc IO functions that use a placeholder function that prints a warning to the console:
  + clearerr
  + ferror
  + fclose
  + fflush
  + fwrite
  + fputs
  + getc
  + feof
  + fseek
  + ftell
  + fopen
  + fread
  + fgets
  + freopen
  + fprintf
  + ungetc
  + tmpnam
  + remove
  + rename
  + tmpfile

# How to build it and run it

```
zig build install --prefix .
python3 -m http.server
```

Then visit the link printed with a modern browser such as Firefox.

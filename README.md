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

- `malloc`/`free`/`realloc` need to be implemented somehow
- Some Lua functions are not being provided properly: `LinkError: import object field 'luaopen_package' is not a Function`
- Probably still quite a few more libc functions missing

Note: File system functions use placeholder functions provided by Javascript at runtime.

# How to build it and run it

```
zig build install --prefix .
python3 -m http.server
```

Then visit the link printed with a modern browser such as Firefox.

# ![json.hollywood](json_hollywood_logo.png)

This is a JSON encoder and decoder for Hollywood MAL (<https://www.hollywood-mal.com>) written in the Hollywood language.

It is a port/conversion of the *json.lua* library which can be found here: <https://github.com/rxi/json.lua> Thanks guys for your work!

The conversion of the decode part was done by Christophe Gouiran (bechris13250@gmail.com) and can be found on the [Official Hollywood forums](https://forums.hollywood-mal.com/viewtopic.php?f=22&t=2004&p=11417&hilit=json&sid=bccabff76b4d2f79365092f880330a62#p11232) Thanks a lot, Christophe!
The decode part was modified a bit so it better suits the overall structure of the file.

I will try to keep this repo in sync with development that happens in the *json.lua* project. Please ping me or open an issue if I am behind.

## Usage

Download [json.hws](json.hws?raw=1), drop it into an existing project and include it:

```lua
@INCLUDE "json.hws"
```

The library provides the following functions:

### json.encode(value)

Returns a string representing `value` encoded in JSON.

```lua
json.encode({ 1, 2, 3, { x = 10 } }) ;-- Returns '[1,2,3,{"x": 10}]'
```

Alternatively you can also use the call `json_encode(value)` instead.

### json.decode(str)

Returns a value representing the decoded JSON string.

```lua
json.decode('[1,2,3,{"x":10}]') ;-- Returns { 1, 2, 3, { x = 10 } }
```

Alternatively you can also use the call `json_decode(str)` instead.

### json.debug(value)

Pretty prints a value like a decoded string to the *debug output*.

```lua
json.debug({ 1, 2, 3, { x = 10 } })
```

## Notes

* Trying to encode values which are unrepresentable in JSON will never result
  in type conversion or other magic: sparse arrays, tables with mixed key types
  or invalid numbers (NaN, -inf, inf) will raise an error
* `null` values contained within an array or object are converted to `nil` and
  are therefore lost upon decoding
* Due to Hollywood's handling of boolean values, unfortunately it is not possible to encode those values as `true`/`false`. Instead `true` is converted to `1` in the encoded format and `false` to `0`.
* *Pretty* encoding is not (yet) supported, `json.encode()` only encodes to a compact format

## Contributions

* Christophe Gouiran (decode port)
* Kevin 'invent' Saunders (logo gfx): [Support Kevin's awesome work](https://www.patreon.com/KevinSaunders)

## License
This library is free software; you can redistribute it and/or modify it under
the terms of the MIT license. See [LICENSE](LICENSE) for details.

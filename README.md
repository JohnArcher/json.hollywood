# json.hollywood
JSON encoder and decoder for Hollywood MAL

This is a version where I tried to encapsulate the code even more so you would just have these methode calls available in the global namespace:

`json.encode()`

`json.decode()`

`json_encode()`

`json_decode()`

Unfortunately this does not work. The code crashes in `parse_array()` when `parse()` is called.

This branch was created to keep this version as reference in the hope that one day and with hints from the community the version could be put into practice.

StringEncode
============
[![Latest Release](https://img.shields.io/github/tag/CodeByZach/sublime_string_encode.svg?label=version)](https://github.com/CodeByZach/sublime_string_encode/releases)

Encodes text. "Encode" in this context refers to HTML entities or URL encoding, not character encodings. Most of these commands work in both directions (e.g. you can encode *to* html entities, or *from* html entities).

- Html entities
- Css (e.g. unicode characters)
- Xml entities
- Json strings
- Urls
- Base64 encoding
- Hash: Md5, Sha256, Sha512
- Regex escape
- SQL 'LIKE' escape
- Hexadecimal / Decimal
- Unicode Hexadecimal representation

This plugin was intended to be used with selections, but if you *don't* have any text selected, it will act on *the entire document*. This can be handy (if you're base64-encoding a file, for instance), but also have unintended consequences. For instance, you probably should not use `URL Decode` on an entire text document.

You can also encode the clipboard, use the `string_encode_paste` command, and you will be presented with a menu to choose the encoding, and the clipboard will be encoded and inserted.

Installation
------------

1. Using Package Control, install "StringEncode"

Or:

1. Open the Sublime Text Packages folder
	- OS X: ~/Library/Application Support/Sublime Text 3/Packages/
	- Windows: %APPDATA%/Sublime Text 3/Packages/
	- Linux: ~/.Sublime Text 3/Packages/ or ~/.config/sublime-text-3/Packages
2. Clone this repo
3. Install keymaps for the commands (see example below)
```
[
	{ "keys": ["super+shift+7"], "command": "xml_entitize", "scope": "text.xml" },
	{ "keys": ["super+ctrl+7"], "command": "xml_deentitize", "scope": "text.xml" },
	{ "keys": ["super+shift+7"], "command": "html_entitize" },
	{ "keys": ["super+ctrl+7"], "command": "html_deentitize" },
	{ "keys": ["super+shift+8"], "command": "json_escape" },
	{ "keys": ["super+ctrl+8"], "command": "json_unescape" },
	{ "keys": ["super+shift+6"], "command": "base64_encode" },
	{ "keys": ["super+ctrl+6"], "command": "base64_decode" },
	{ "keys": ["super+shift+5"], "command": "url_encode" },
	// { "keys": ["super+shift+5"], "command": "url_encode", "args": {"old_school": true} },
	{ "keys": ["super+ctrl+5"], "command": "url_decode" },
	{ "keys": ["ctrl+shift+r"], "command": "escape_regex" },
	{ "keys": ["super+ctrl+3"], "command": "hex_dec" }
]
```

Commands
--------

`string_encode_paste`: Converts the clipboard to the desired encoding.

`html_entitize`: Converts characters to their HTML entity

`html_deentitize`: Converts HTML entities to a character

`url_encode`: Uses urllib.quote to escape special URL characters.
- Accepts an `old_school` argument (default: `True`). Setting it to `False` will return `%20` instead of `+` when encoding spaces.

`url_decode`: Uses urllib.unquote to convert escaped URL characters

`json_escape`: Escapes a string and surrounds it in quotes, according to the JSON encoding.

`json_unescape`: Unescapes a string (include the quotes!) according to JSON encoding.

`base64_encode`: Uses base64 to encode into base64

`base64_decode`: Uses base64 to decode from base64

`md5_encode`: Uses sha package to create md5 hash

`sha256_encode`: Uses sha package to create sha256 hash

`sha512_encode`: Uses sha package to create sha512 hash

`escape_regex`: Escapes regex meta characters

`escape_like`: Escapes SQL-LIKE meta characters

`safe_html_entitize`: Converts characters to their HTML entity, but preserves HTML reserved characters

`safe_html_deentitize`: Converts HTML entities to a character, but preserves HTML reserved characters

`xml_entitize`: Converts characters to their XML entity

`xml_deentitize`: Converts XML entities to a character

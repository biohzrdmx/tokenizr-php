# tokenizr-php

Salted, SHA256-hashed token generation and checking

## Requirements

- PHP 5.2+ with the Hash extension
- Hummingbird Lite 3.x or newer

## Basic usage

Include the file.

Use getToken() to tokenize your data. It will return an string with the source data and its message digest:

	$token = Tokenizr::getToken('something');

You can then save the token wherever you want. To check it back, use checkToken()

	$valid = Tokenizr::checkToken('something.xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx');

To get back the data, use getData()

	$data = Tokenizr::getData('something.xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx');

Note that the data and its message digest are separated by a PERIOD, so it wouldn't be a good idea to try to tokenize strings containing periods (duh). Data structures (arrays/objects) aren't supported as-is, if you want to tokenize them, you'll have to serialize and/or base64-encode them before using this class.

NOTE: Since the last update you can change the divider to avoid collisions with PERIODS.

Also note that the data is saved in plain sight, THIS CLASS IS NOT DESIGNED TO ENCRYPT DATA. The purpose of this class is to provide a way to check if the data (from a cookie, for example) has been generated by your code and not forged. The checksum is reliable as long as you NEVER DISCLOSE YOUR SALTS.

## License

The MIT License (MIT)

Copyright (c) 2017 biohzrdmx

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.


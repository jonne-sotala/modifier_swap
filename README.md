# modifier swap

Swap modifiers using [Interception Tools](https://gitlab.com/interception/linux/tools).
Works globally, no requirement of X11 or any graphics. I created this for personal use
in order for my laptop keyboard to mimic the layout of my desktop keyboard. It does a
couple of things:

- Swap left alt and left meta keys.
- Change right alt to left meta.
- Change right ctrl to right alt.

## Install


``` shell
$ cmake -B build -DCMAKE_BUILD_TYPE=Release
$ make -C build
$ sudo cp build/modifier_swap /usr/local/bin/
```

## Usage

Refer to [Interception Tools](https://gitlab.com/interception/linux/tools)'s
README for information on installation and usage.
An example `udevmon` configuration with `caps2esc`:

``` yaml
- JOB: "intercept -g $DEVNODE | caps2esc | modifier_swap | uinput -d $DEVNODE"
  DEVICE:
    LINK: /dev/input/by-path/platform-i8042-serio-0-event-kbd
    EVENTS:
      EV_KEY:
        [
          KEY_CAPSLOCK,
          KEY_ESC,
          KEY_LEFTMETA,
          KEY_LEFTALT,
          KEY_RIGHTALT,
          KEY_RIGHTCTRL,
        ]
```

## Thanks

The code is mostly copied from [ralt2hyper](https://gitlab.com/oarmstrong/ralt2hyper/)
so thanks for oarmstrong.

This also wouldn't exist without [Francisco Lopes](https://gitlab.com/oblitum)
and their [Interception Tools](https://gitlab.com/interception/linux/tools)
project and also [`caps2esc`](https://gitlab.com/interception/linux/plugins/caps2esc)
as a sample codebase.

## License

MIT License.

```
Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

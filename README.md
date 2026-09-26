zathura-pdf-mupdf
=================

zathura is a highly customizable and functional document viewer based on the girara user interface
library and several document libraries. This plugin for zathura provides PDF support using the
`mupdf` library.

Requirements
------------

The following dependencies are required:

* `zathura` (>= 2026.01.30)
* `girara`
* `mupdf` (>= 1.26)

For building plugin, the following dependencies are also required:

* `meson` (>= 1)

Installation
------------

To build and install the plugin using meson's ninja backend:

    meson build
    cd build
    ninja
    ninja install

> **Note:** The default backend for meson might vary based on the platform. Please
refer to the meson documentation for platform specific dependencies.

> **Note:** To avoid conflicts with `zathura-pdf-poppler`, PDF support can be disabled
at compile time by using `meson build -Dpdf=disabled` instead of `meson build`.

Bugs
----

Please report bugs at https://github.com/pwmt/zathura-pdf-mupdf.


Debian Trixie (13.7 and older)
------------------------------
Here are instructions to use mupdf backend just for EPUB files:

0. For formats other than EPUB, just use the poppler-based packages:
`sudo apt install zathura zathura-cb zathura-djvu zathura-pdf-poppler zathura-ps`
1. Download the binary from releases
2. Create a desktop file: `~/.local/share/applications/org.pwmt.zathura-epub.desktop`

```
[Desktop Entry]
Version=1.0
Type=Application
Name=Zathura-mupdf
Comment=A minimalistic document viewer
Exec=zathura --plugins-dir=/path/to/dir/of/libpdf-mupdf %U
Icon=org.pwmt.zathura
Terminal=false
NoDisplay=true
Categories=Office;Viewer;
MimeType=application/epub+zip;
```

(the plugin on Releases is built without pdf support)

3. `update-desktop-database ~/.local/share/applications/`, then choose
   `Zathura-mupdf` for EPUB files on the context menu of your DE file manager

Of course the mupdf backend can also be used exclusively for everything, just
make sure to invoke zathura with the proper `--plugins-dir`

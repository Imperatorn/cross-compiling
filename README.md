# Build binaries for Windows from Linux using dub

Make sure you have LDC installed. If you need to, read [Cross compiling with LDC][1]

In this example we will target x64 Windows.

Download the Windows libraries, for example: \
https://github.com/ldc-developers/ldc/releases/download/v1.35.0/ldc2-1.35.0-windows-x64.7z

Unpack lib to /path/to/your/lib 

Locate your ldc2.conf and create a section for your target.

It could look like this (notice lib-dirs):

```
"x86_64-.*-windows-msvc":
{
    switches = [
        "-defaultlib=phobos2-ldc,druntime-ldc",
    ];
    lib-dirs = [
        "/path/to/your/lib",
    ];
};
```

Now, navigate to your dub-project and run

```cmd
dub build --arch=x86_64-windows-msvc
```

[1]: <https://wiki.dlang.org/Cross-compiling_with_LDC> "Cross compiling with LDC"

# EditorConfig Visual Studio Plugin

This plugin causes Visual Studio to load its indentation options from a standard `.editorconfig` settings file. See the [project web site](http://editorconfig.org) for more information.

## Installing

This plugin works with Visual Studio 2010 or later. The easiest way to install it is through Visual Studio's built-in Extension Manager. Just search for "EditorConfig" in the Online Gallery section. Or, download a copy from the [Visual Studio gallery](http://visualstudiogallery.msdn.microsoft.com/c8bccfe2-650c-4b42-bc5c-845e21f96328) website.

## Building

To build this software, first download and build the [EditorConfig core library](https://github.com/editorconfig/editorconfig-core) in the `Core` directory. To automatically download the core library, use the git command:

    git submodule update --init

Follow the [build instructions](https://github.com/editorconfig/editorconfig-core-c/blob/master/INSTALL.md#installing-from-source) for the core library as normal, but include the `-DMSVC_MD=ON` option when invoking CMake:

    cd Core/
    cmake . -DMSVC_MD=ON

Once the core library is built, open the solution file `EditorConfig.VisualStudio.sln` and compile the plugin. 

You will need to install the [Visual Studio 2010 SDK](http://www.microsoft.com/en-us/download/confirmation.aspx?id=2680) explicitly
since its the last version built against .NET 4.0 and some referenced assemblies might resolve the later SDK requiring .NET 4.5.

The resulting plugin is named `Plugin/bin/(Debug|Release)/EditorConfigPlugin.vsix`, and double-clicking installs it into Visual Studio.

## Supported properties

The plugin supports the following EditorConfig [properties](http://editorconfig.org/#supported-properties):

* indent_style
* indent_size
* tab_width
* end_of_line
* insert_final_newline
* trim_trailing_whitespace
* root (only used by EditorConfig core)

## Reporting problems

If you encounter any problems, feel free to report them at the central EditorConfig [issue tracker](https://github.com/editorconfig/editorconfig/issues).

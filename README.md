# **Building libpng with Visual Studio 2019**

## Precondition

 - zlib ver1.2.11: [https://zlib.net/](https://zlib.net/)
 - libping ver1.6.37: [http://www.libpng.org/pub/png/libpng.html](http://www.libpng.org/pub/png/libpng.html)

Unzip these files in directory "build".
The directory structure is here.

    build                # root for bulding
    ├─ lpng1637          # libpng
    └─ zlib-1.2.11       # zlib

## Build libpng

 1. **Edit "zlib.props"**<br>
    Open file "build\lpng1637\projects\vstudio\zlib.props"

    Change line #34<br>
    `<ZLibSrcDir>..\..\..\..\zlib</ZLibSrcDir>`<br>
    to<br>
    `<ZLibSrcDir>..\..\..\..\zlib-1.2.11</ZLibSrcDir>`<br>
    
 2. **Create zconf.h**<br>
  Duplicate the file "build\zlib-1.2.11\zconf.h.included" and rename to "zconf.h"

 3. **Open Solution file**<br>
   The solution file of Visual Studio is here "build\lpng1637\projects\vstudio\vstudio.sln"<br>
   Some warning daialogs may be shown. Then click OK button on all daialogs.<br> 
   It includes 7 projects as following.

	 - List item
	 - libpng
	 - pnglibconf
	 - pngstest
	 - pngtest
	 - pngunknown
	 - pngvalid
	 - zlib

 4. **Edit Property Pages**<br>
  Open Property Page of "zlib" project.
  Edit as below.<br>
    - Editting with "All Configurations".<br>
      `Configuration Properties` &rarr; `C/C++` &rarr; `General` &rarr; `Treat Warnings As Errors`<br>
      Change **"$(TreatWarningAsError)"** to **"No (/W-)"**
    - Editting each configration.<br>
      `Configuration Properties` &rarr; `C/C++` &rarr; `Preprocessor` &rarr; `Preprocessor Definitions`<br>
      Remove **"Z_SOLO;"**

 5. **Build**<br>
   Set `Solution Configrations` &rarr; `Release Library`<br>
   Menu `Build` &rarr; `Buld Solution`

Completed\! :smile:

# MapViewer
MapViewer is a Windows (C#/.NET)application that displays information extracted from the MAP file (generated by the GNU linker LD) and from the ELF executable image. It displays the module/file wise split of resources consumed along with details of individual symbols found within each module/file. Each view can be filtered and sorted dynaimically allowing the user to quickly calculate the sizes of various modules and symbols or identify those modules that are perhaps unintentionally included in a project. All the list view magic is courtesy of [ObjectListView](http://objectlistview.sourceforge.net/cs/index.html)

The application looks like this:
![](http://imgur.com/8u7qsK7.png)

It was primarily developed for use with the **Bridgetek (formerly FTDI) [FT9xx](https://brtchip.com/product-category/products/ic/mcu-ic/)** Microcontroller and associated toolchain but is generic enough to be useable for other GCC based toolchains. I've tested it with **Microchip's XC16 compiler** and should also be useful for XC32 (with some minimal porting).

I've written a blog post with more details on the application [here](http://www.embeddedrelated.com/showarticle/900.php).
Prebuild executables are available under the [releases](https://github.com/Bridgetek/MapViewer/releases).

# Usage Guide
1. Input the paths to the MAP and ELF image in the text boxes.
2. Click on the Settings button and configure the path to Binutils NM and READELF provided by your toolchain.
3. Update the Segment to Sections mapping if your target is not FT32 or XC16 (PIC24)
4. Close the settings and click on the "Analyze" button. 
5. Right click on the Lists to export to CSV/HTML files
6. [new feature] If you linked with the `-cref` option, a tree view of the module "dependcies" is shown for each module you select. 
This shows you the modules that *depend on/are users of* the selected module. And allows you to easily answer questions like "which application files are responsible for the inclusion of floating point library routines in my project?" for instance. Note that the this view is a bit incomplete in that paths are truncated if the same node appears twice on it. The information looks like this:
![](https://i.imgur.com/i3CP5Gi.png)




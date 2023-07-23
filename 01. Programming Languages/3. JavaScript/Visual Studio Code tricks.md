Running the JS file - Install NodeJS, then `Ctrl + Option + N` <br>

##### Region folding

A third praty extension (from [maptz](https://marketplace.visualstudio.com/items?itemName=maptz.regionfolder)) can be used for it. With it code folding can be done across any custom region using the syntax `// #region REGION_NAME` and `//endregion`. This patten in fact is same across all languages, just that the initial characters should be the standard comments syntax for that language.

In Visual Studio's settings.json (accessible using the gear icon for the extension), an entry must be created appropriately for the applicable language (it is not present by default) and it must be ensured that it has the right characters for the comment syntax.

![image-20230728111346400](assets/image-20230728111346400.png)

The keyboard shortcut to wrap any bunch of code in a region is to select the lines, and then type `Ctl M Ctl R`.

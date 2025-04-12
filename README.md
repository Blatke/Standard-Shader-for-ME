# Standard Shader for ME
An experimental shader mod for HS2 / AI-Shoujo Studio MaterialEditor based on [**Blake/Standard.shader**](https://github.com/Blatke/Standard.shader).

## Main Features
1. **Bump Manipulation**: It provides properties to make the material bump by importing bump maps or remove the bumps via mapping by a mask.
2. **Wet Effect**: It includes a section for adding a wet effect to the material, enhancing the realism and visual appeal.
3. **Fluid Effect**: The shader mod also supports the addition of fluid effects, with detailed adjustability supported by a mask.
4. **Color Masking**: It allows for the changing of original colors brought by tint and main texture with new colors mapped by a mask.

## Installation
1. Download the .zipmod file for the latest version on the [Release](https://github.com/Blatke/Standard-Shader-for-ME/releases) page.
2. Drag and drop it into the **/mods/** folder of your game directory.
3. Start HS2/AIS Studio, select an object and go to the MaterialEditor tab, and then load Blake/Standard as a new shader to the material of the object.

## Tutorial

Please check this [**Tutorial**](https://github.com/Blatke/Standard-Shader-for-ME/blob/main/Tutorial/0.Tutorial.md) for the usage of this shader mod.


> [!TIP]
>
> The tutorial was based on **Version 2.7.2** of this mod.
>
> The textures involved in the tutorial can be checked on: https://github.com/Blatke/Standard-Shader-for-ME/tree/main/Tutorial/Textures%20involved%20in%20Tutorial.
> 
> It took a tight clothing worn on a character to demonstrate the using of this shader mod. In this tight clothing mod, the UV layout is quite similar to that of HS2 character's body, and this makes the textures referred in this tutorial quite similar to the overlay maps putting on character's body. This clothing mod involved in this tutorial can be found on: https://github.com/Blatke/Heels-with-Tight---HS2-AIS-mod.

## Troubleshooting
The following content is about the issues that could be mostly asked. For any further problem, please leave a message on my [Discord](https://discord.gg/nc5pmnf8X3) server if there is any chance.
### Newly imported bump maps look weird in shadow
When importing a custom bump map into this shader (or other shaders) on MaterialEditor, the bumps with shadows might look weird.

This could actually happen because the games based on Unity Engine are compressed their bump maps in [DXT5nm compression format](http://wiki.polycount.com/wiki/Normal_Map_Compression#DXT5nm_Compression), in which red channel is swapped with alpha channel that makes a bump map look pink and semi-transparent instead of blue or purple. This means, if you directly import a purple bump map into MaterialEditor in HS2/AIS Studio, the map might not be correctly read, because its alpha channel that is read as red channel in DXT5nm format is always 1.0.

To avoid this problem, it suggests to directly import the pink bump maps that are **in DXT5nm format**. You can choose [NormalMapTool](https://www.patreon.com/posts/99107961) to do a quick conversion.

### Weird seams appear when using a mask
If importing a compressed image for a mask, suck as in .jpeg or .jpg format, weird seams might appear on the edge mapped by the mask. It suggests to use uncompressed image like **.png** for a mask.

### What are the 7 colors a mask supports?
![image](https://github.com/user-attachments/assets/78c92cbc-5b3a-4390-a878-e62a7fa99413)

### Why the properties have prefixes in names?
The properties mostly have the names like **D913**_ColorMaskEmit_Red. The prefix "D913" has no special meaning. These prefixes are just for sequencing the properties on MaterialEditor tab, which sequences the properties by alphabetic order of their names. By using these prefixes, the properties in the same section can be listed together instead of being separately distributed that could be difficult to find.

# Standard Shader for ME
A shader mod for HS2 / AIS Studio MaterialEditor based on [**Blake/Standard.shader**](https://github.com/Blatke/Standard.shader).

## Main Features
1. **Bump Manipulation**: It provides properties to make the material bump or remove the bumps, allowing for detailed texture adjustments.
2. **Wet Effect**: It includes a section for adding a wet effect to the material, enhancing the realism and visual appeal.
3. **Fluid Effect**: The shader mod also supports the addition of fluid effects, with detailed adjustability supported by a mask.
4. **Color Masking**: It allows for the changing of original colors brought by tint and main texture with new colors mapped by a mask.

## Installation
Download the .zipmod file for the latest version on the [Release](https://github.com/Blatke/Standard-Shader-for-ME/releases) page.

Drag and drop it into the **/mods/** folder of your game directory.

Start HS2/AIS Studio, select an object and go to the MaterialEditor tab, and then load Blake/Standard as a new shader to the material of the object.

## Tutorial
For users on MEGA: https://mega.nz/folder/93QExRKD#VbqWFROqjYvKHejaiVHAAw

For users on Pixiv: https://www.pixiv.net/artworks/129073962

## Troubleshooting
### Newly imported bump maps look weird in shadow
When importing a custom bump map into this shader (or other shaders) on MaterialEditor, the bumps with shadows might look weird.

This could actually happen because the games based on Unity Engine are compressed their bump maps in a DXT5nm compression format, in which red channel is swapped with alpha channel that makes a bump map look pink and semi-transparent instead of blue or purple.

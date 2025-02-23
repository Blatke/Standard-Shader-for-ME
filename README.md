# Standard Shader for ME
A shader mod for HS2 / AIS based on [**Blake/Standard.shader**](https://github.com/Blatke/Standard.shader).

## Main Features
1. **Bump Manipulation**: It provides properties to make the material bump or remove the bumps, allowing for detailed texture adjustments.
2. **Wet Effect**: It includes a section for adding a wet effect to the material, enhancing the realism and visual appeal.
3. **Fluid Effect**: The shader mod also supports the addition of fluid effects, with detailed adjustability supported by a mask.
4. **Color Masking**: It allows for the changing of original colors brought by tint and main texture with new colors designated by a mask.

## Properties
The properties of this shader shown on the MaterialEditor tab are listed below. Most of them have a prefix like "A1_", "B1_", "C1" or "D101" that is for sequencing on the tab.

### Main
- A1_Color
	- Color
   - Tint color that will blend with MainTex.
- MainTex
	- Texture
   - Main Texture that accepts an RGBA image.
   - If a pixel on MainTex has a value in alpha channel less than 1.0, it might be further processed by the following properties.
- A2_Cutout
	- Float
   - Threshold for culling the pixels on MainTex if their alpha channel values are less than 1.0.
- A2_AlphaColor
	- Color
   - If the image for MainTex has the alpha channel values less than 1.0 and greater than the threshold for culling (A2_Cutout), the pixels covered by these values will have their colors blended by this A2_AlphaColor.
   - This functions only if A2_AlphaColor's alpha value is less than 1.0, otherwise no color will be blended under this function.
- A_OMS
	- Texture
  - An OMS texture for assginning respectively Occlusion, Metallic and Smoothness to the Red, Green and Blue channel values in the imported RGBA image.
  - If the image has an alpha value less than 1.0, this value will multiply respectively by the RGB values in the image.
- A5_Occlusion
	- Float
  - Occlusion value that multiplies by the Red channel values of A_OMS texture.
- A7_Metallic
	- Float
   - Metallic value that multiplies by the Green channel values of A_OMS texuture.
- A6_Smoothness
	- Float
   - Smoothness value that multiplies by the Blue channel values of A_OMS texuture.
- A_Emission
	- Texture
   - Texture for light emission and accepts an RGBA image.
- A8_EmissionColor
	- Color
   - Emission color that blends with the one assigned by A_Emission texture.
- A8_EmissionStrength
	- Float
   - Intensity of emission.

### Bump and Eraser
This section is for making the material bump or removing the bumps.
- Normal
	- Texture
 	- Normal map for bump effect.
- A901_NormalStrength
	- Float
 	- Intensity of the bump effect brought by Normal map.
- DetailNormal
	- Texture
 	- Detail Normal 1 map that blends with Normal map.
- A902_DetailNormal1Strength
	- Float
 	- Intensity of the bump effect brought by Detail Normal 1 map.
- DetailNormal2
	- Texture
 	- Another Detail Normal map that blends with Normal and Detail Normal 1 maps.
- A903_DetailNormal2Strength
	- Float
 	- Intensity of the bump effect brought by Detail Normal 2 map.
- A_BumpEraserMask
	- Texture
 	- A mask texture for erasing or removing the bump effects brought by the normal maps above.
  	- It accepts an RGBA image in which the values in RGBA channels greater than 0 will erase the corresponding bump pixels.
- A920_BumpEraserThreshold
	- Float
 	- Intensity of bump erasing.
- _A931_BumpEraserNormal
	- Float
 	- If it is 1.0, bump erasing will affect Normal map. Otherwise, it will not affect Normal map.
- _A941_BumpEraserDetailNormal1
	- Float
 	- If it is 1.0, bump erasing will affect Detail Normal 1 map. Otherwise, it will not affect Detail Normal 1 map.
- _A951_BumpEraserDetailNormal2
	- Float
 	- If it is 1.0, bump erasing will affect Detail Normal 2 map. Otherwise, it will not affect Detail Normal 2 map.

### Wetness
This section is for adding the material with wet effect.
- B_WetnessMap
	- Texture
 	- A given texture providing for wet effect with extra smoothness and metallic that will added to A6_Smoothness and A7_Metallic.
- B1_WetnessDensity
	- Float
 	- Scale of B_WetnessMap texture (and B3_WetnessBump). Greater density means a smaller scale of the texture.
- B2_WetnessStrength
	- Float
 	- Intensity of smoothness and metallic of wetness.
- B_WetnessBumpMap
	- Texture
 	- A given texture providing with bump effect for wetness.
- B3_WetnessBump
	- Float
 	- Intensity of the bump effect brought by B_WetnessBumpMap texture.

### Fluid
This section is for adding fluid effect to the material.
- C_FluidMap
	- Texture
 	- A given texture providing the material with smoothness for simulating fluid effect.
- C_FluidNormal
	- Texture
 	- A given texture providing the fluid with bump.
- C1_FluidColor
	- Color
   	- Color of fluid that blends with the colors brought by _A1_Color and MainTex as well as other diffuse colors.
- C2_FluidDensity
	- Float
 	- Scale of C_FluidMap texture (and C5_FluidBump). Greater density means a smaller scale.
- C3_FluidStrength
	- Float
 	- Intensity of fluid performance in smoothness and tint.
- C4_FluidEmission
	- Color
 	- Color of the light that fluid emits.
- C5_FluidBump
	- Float
 	- Intensity of the bump brought by C_FluidNormal texture.
- C6_FluidRotation
	- Float
 	- Degree of the rotation of C_FluidMap and C_FluidNormal textures.
- C_FluidMask
	- Texture
 	- A mask texture for separately manipulating various parts of fluid.
  	- It accepts an RGBA image on which the parts with one of 7 colors will affect the fluid they overlapped with.
- C900_FluidMaskStrength
	- Float
 	- Total intensity of C_FluidMask to affect fluid.
- C901_FluidMaskStrength_Red
	- Float
 	- Intensity of the red parts on C_FluidMask to affect fluid.
- C905_FluidRotation_Red
	- Float
 	- Degree of the rotation of fluid overlapped with the red parts on C_FluidMask
- C906_FluidPositionX_Red
	- Float
 	- Offset on X axis of fluid overlapped with the red parts on C_FluidMask.
- C907_FluidPositionY_Red
	- Float
 	- Offset on Y axis of fluid overlapped with the red parts on C_FluidMask.
- C908_FluidScaleX_Red
	- Float
 	- Scale on X axis of fluid overlapped with the red parts on C_FluidMask.
- C909_FluidScaleY_Red
	- Float
 	- Scale on Y axis of fluid overlapped with the red parts on C_FluidMask.

The following properties are similar to those from C901_FluidMaskStrength_Red to C909_FluidScaleY_Red:
- C911_FluidMaskStrength_Green
- C915_FluidRotation_Green
- C916_FluidPositionX_Green
- C917_FluidPositionY_Green
- C918_FluidScaleX_Green
- C919_FluidScaleY_Green
- C921_FluidMaskStrength_Blue
- C925_FluidRotation_Blue
- C926_FluidPositionX_Blue
- C927_FluidPositionY_Blue
- C928_FluidScaleX_Blue
- C929_FluidScaleY_Blue
- C931_FluidMaskStrength_Cyan
- C935_FluidRotation_Cyan
- C936_FluidPositionX_Cyan
- C937_FluidPositionY_Cyan
- C938_FluidScaleX_Cyan
- C939_FluidScaleY_Cyan
- C941_FluidMaskStrength_Fuchsia
- C945_FluidRotation_Fuchsia
- C946_FluidPositionX_Fuchsia
- C947_FluidPositionY_Fuchsia
- C948_FluidScaleX_Fuchsia
- C949_FluidScaleY_Fuchsia
- C951_FluidMaskStrength_Yellow
- C955_FluidRotation_Yellow
- C956_FluidPositionX_Yellow
- C957_FluidPositionY_Yellow
- C958_FluidScaleX_Yellow
- C959_FluidScaleY_Yellow
- C961_FluidMaskStrength_White
- C965_FluidRotation_White
- C966_FluidPositionX_White
- C967_FluidPositionY_White
- C968_FluidScaleX_White
- C969_FluidScaleY_White

### Color Mask
This section is for changing the original colors brought by A1_Color and MainTex with new colors designated by a mask texture.
- D_ColorMask
	- Texture
 	- Mask texture for separately changing the original colors. It accepts an RGBA image on which the parts with one of 7 colors will affect the 
original colors they overlapped with.
- D101_ColorMaskStrength
	- Float
 	- Intensity of the mask to change the original colors. If it's 1.0, the original colors are completely replaced by the new colors. If less than 1.0, the original colors are blended with the new colors. If 0, the original colors are kept without any change.
- D911_ColorMaskToColor_Red
	- Color
 	- If the pixels overlapped with the Red parts on the color mask, these pixels' original colors can be affected by a new color designated by this property.
- D912_ColorMaskStr_Red
	- Float
 	- Intensity of the Red parts on the color mask to affect the original colors of the pixels overlapped with these parts.
- D913_ColorMaskEmit_Red
	- Float
 	- Intensity of light emitted by the pixels overlapped with the Red parts on the color mask.
  	- The color of this emission is same as D911_ColorMaskToColor_Red.
 
The following properties are similar to those from D911_ColorMaskToColor_Red to D913_ColorMaskEmit_Red:
- D921_ColorMaskToColor_Green
- D922_ColorMaskStr_Green
- D923_ColorMaskEmit_Green
- D931_ColorMaskToColor_Blue
- D932_ColorMaskStr_Blue
- D933_ColorMaskEmit_Blue
- D941_ColorMaskToColor_Cyan
- D942_ColorMaskStr_Cyan
- D943_ColorMaskEmit_Cyan
- D951_ColorMaskToColor_Fuchsia
- D952_ColorMaskStr_Fuchsia
- D953_ColorMaskEmit_Fuchsia
- D961_ColorMaskToColor_Yellow
- D962_ColorMaskStr_Yellow
- D963_ColorMaskEmit_Yellow
- D971_ColorMaskToColor_White
- D972_ColorMaskStr_White
- D973_ColorMaskEmit_White

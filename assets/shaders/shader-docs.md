# Shader Docs

## Understanding and leveraging RED3 shaders

We do not have official documentation from CDPR about how shaders are used by artists. Thus any 2d/3d artist is looking at hundreds of black-box shaders with unknown usage. This is extremely demotivating for anyone looking to bring new assets to life with REDengine. The following list of tables is an attempt to make life easier for artists by using the community to document commonly used shaders.

## About the documentation

* The name and path of each shader will be documented by the header.
* Next we are using a table for each texture parameter with the _exact name_ listed by CDPR in the w2mg file, how REDengine uses each specific RGBA channel, and the usable range of the channel if not 0-1/0-255.
* When applicable, vertex color properties will be listed underneath the texture table with a similar format.
* Scalar, vector, color, and other properties will follow with their own unique description table.
* An asterisk (\*) is used to notate some degree of uncertainty, or need for more independent testing.

## Shaders

### `pbr_std_tint_mask_det`

```
engine\materials\graphs\pbr_std_tint_mask_det.w2mg
```

| Texture Channels |        Red        |  Green |          Blue         |     Alpha    |
| ---------------- | :---------------: | :----: | :-------------------: | :----------: |
| Diffuse          |       Color       |  Color |         Color         | Transparency |
| Normal           |       Normal      | Normal |         Normal        |   Roughness  |
| Tintmask         | Ambient Occlusion |  Tint  | Detail Mask (128-255) |     None     |

| Properties         | Description                                              |
| ------------------ | -------------------------------------------------------- |
| SpecularColor      | RGB value to assign specular highlight                   |
| DetailNormal1      | 1 of 2 procedural normal map detail overlays             |
| DetailTile         | X/Y tiling values for DetailNormal                       |
| DetailRotation     | Rotation values for DetailNomal                          |
| DetailRange        | Distance at which DetailNormal is applied to mesh        |
| Roughness\_min/max | Clip values to add a global min/max to roughness texture |
| AOPower            | Multiplier for Ambient Occlusion                         |

#### Notes

* Extremely common for character assets
* Uses EnableMask flag to create alpha clipped transparency mask from diffuse texture



### `pbr_std_tint_mask_2det`

```
engine\materials\graphs\pbr_std_tint_mask_2det.w2mg
```

| Texture Channels |        Red        |  Green |             Blue             |     Alpha    |
| ---------------- | :---------------: | :----: | :--------------------------: | :----------: |
| Diffuse          |       Color       |  Color |             Color            | Transparency |
| Normal           |       Normal      | Normal |            Normal            |   Roughness  |
| Tintmask         | Ambient Occlusion |  Tint  | 2 Detail Masks (0-0.5/0.5-1) |     None     |

| Properties         | Description                                              |
| ------------------ | -------------------------------------------------------- |
| SpecularColor      | RGB value to assign specular highlight                   |
| DetailNormal1      | 1 of 2 procedural normal map detail overlays             |
| DetailNormal2      | 2 of 2 procedural normal map detail overlays             |
| DetailTile1/2      | X/Y tiling values for DetailNormals                      |
| DetailRotation1/2  | Rotation values for DetailNomals                         |
| DetailRange        | Distance at which DetailNormal is applied to mesh        |
| Roughness\_min/max | Clip values to add a global min/max to roughness texture |
| AmbientPower       | Multiplier for Ambient Occlusion                         |

#### Notes

* Extremely common for character assets
* Uses EnableMask flag to create alpha clipped transparency mask from diffuse texture
* Based on pbr-std-tint-mask-det
* The tintmask texture packs 2 maps into the blue channel, one map from values 0-127 and another from 127-255. The "zero value" for both textures is at the midpoint, while using values closer to 0/255 will increase the detailmap strength.



### `pbr_std_tint_mask_2det_fresnel`

```
engine\materials\graphs\pbr_std_tint_mask_2det_fresnel.w2mg
```

| Texture Channels |        Red        |  Green |             Blue             |     Alpha    |
| ---------------- | :---------------: | :----: | :--------------------------: | :----------: |
| Diffuse          |       Color       |  Color |             Color            | Transparency |
| Normal           |       Normal      | Normal |            Normal            |   Roughness  |
| Tintmask         | Ambient Occlusion |  Tint  | 2 Detail Masks (0-0.5/0.5-1) |     None     |

| Properties         | Description                                              |
| ------------------ | -------------------------------------------------------- |
| SpecularColor      | RGB value to assign specular highlight                   |
| DetailNormal1      | 1 of 2 procedural normal map detail overlays             |
| DetailNormal2      | 2 of 2 procedural normal map detail overlays             |
| DetailTile1/2      | X/Y tiling values for DetailNormals                      |
| DetailRotation1/2  | Rotation values for DetailNomals                         |
| DetailRange        | Distance at which DetailNormal is applied to mesh        |
| Roughness\_min/max | Clip values to add a global min/max to roughness texture |
| AmbientPower       | Multiplier for Ambient Occlusion                         |
| FresnelPower       | Fresnel multiplier                                       |
| FresnelStrenght    | (misspelled by CDPR) Fresnel multiplier                  |

#### Notes

* Uses EnableMask flag to create alpha clipped transparency mask from diffuse texture
* Based on pbr-std-tint-mask-2det
* The tintmask texture packs 2 maps into the blue channel, one map from values 0-127 and another from 127-255. The "zero value" for both textures is at the midpoint, while using values closer to 0/255 will increase the detailmap strength.
* Uses "fresnel" values to add extra fresnel effect to the mesh. Read more about [fresnel here.](https://www.scratchapixel.com/lessons/3d-basic-rendering/introduction-to-shading/reflection-refraction-fresnel)

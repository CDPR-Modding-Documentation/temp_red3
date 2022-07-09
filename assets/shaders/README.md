---
description: RED3 shaders (w2mg)
---

# Shaders

## What are shaders?

Every visual asset in REDengine 3 uses a specific shader, designated by REDengine as W2MG (.w2mg/Witcher 2 material graph) files. Even meshes "without a shader" are in-fact using a debug shader such as debug.w2mg. Shaders are the most basic expression of a surface, ranging from glass, skin, concrete, and steel. Each shader contains a combination of constant hidden-variables, and exposed variables for artists to tweak. For example, all skin exhibits some similar properties such as subsurface scattering so there is no reason to expose this; artists cannot use the skin shader without subsurface scattering. However skin color can vary dramatically, so these parameters are exposed to the artists using textures. Artists are able to create "instances" of shaders called [**Material Instances**](materials.md) which contain localized variations of the textures and properties exposed by the base shader.

---
name: fashion-asset-locked-tryon-v3
description: Product-fidelity-first virtual try-on pipeline using FASHN VTON 1.5 and region-level visual QA.
version: 3.0.0
---
# Fashion Asset-Locked Try-On V3

## Objective
Produce a NEW photograph of a reference adult model wearing reference SKU clothing. Prioritize product accuracy over aesthetics. Never claim pixel-identical results unless verified.

## Model selection
Primary: fashn-AI/fashn-vton-1.5 (Apache-2.0). Follow upstream license and transitive dependencies. CatVTON and IDM-VTON are noncommercial research-only alternatives, never production fallback. The primary model accepts person image, garment image and category: tops / bottoms / one-pieces. This is NOT a native arbitrary multi-garment multi-accessory editor.

## Mandatory asset manifest
Capture source filename, role, SKU, evidence, uncertainties and nonnegotiable details.
Roles: PERSON, TOP, DRESS, FABRIC_MACRO, GARMENT_DETAIL, SHOES, BAG, FIT_ONLY, SCENE_ONLY.
Do not use fit-only images as authoritative garment masters. Never conflate different SKUs.

## Reference product
TOP: muted beige/greige finely ribbed, washed mottled surface, subtle lettuce/rolled neck and cuff.
DRESS: chocolate brown, small irregular white floral and muted bluish botanical sprigs, thin printed straps, shallow V front, long widening skirt, fluid drape.
PERSON: young adult with soft rounded face, realistic mildly plus-size body; preserve identity from provided person reference.
ACCESSORIES: glossy black chunky loafers with gold vamp ornament; black diamond-quilted flap bag with substantial mixed-tone chain. Keep independent.

## MVP (single dress only, no accessories)
1. Prepare legally usable person photo with clear standing pose and dress product flat-lay. Keep originals unmodified.
2. Run FASHN VTON 1.5 category one-pieces, record model version, seed, device, output size, elapsed time.
3. Compare original garment to generated dress: V neckline, strap count and attachment, floral scale and density, hem and silhouette.
4. Reject obvious drift. Preserve person identity, natural body volume, anatomical consistency.
5. Only if single dress passes, test two-layer styling: first TOP try-on, then DRESS try-on. This is an EXPERIMENT, not guaranteed to preserve inner layer. Inspect for erased collar, sleeves or print; reject failures.
6. Accessories: composite or region-inpaint only after garment validation, then separately verify geometry/hardware.
7. New scene/pose is an optional later stage; baseline VTON primarily retains person pose/background, so it must not be advertised as automatic scene generation.
8. Upscale to 2160x3840 PNG only as a clearly labeled deliverable; don't call upscaled fabric texture native 4K.

## QA gates
Hard fail: incorrect SKU, different face, changed body size, wrong layering, invented floral/texture, deformed hands/feet, missing hem or straps.
Record separate scores 0-5: identity, silhouette, top texture, dress print, layering, accessories, physical fit, photography. No final approval if any applicable SKU dimension <4.
Make side-by-side crops for neckline, chest, sleeves, skirt and hem; compare visible features, not invented fiber composition.

## Practical limitations
FASHN's base CLI is for one garment/category per inference. Multi-layer compositing, material mapping and masked repair require extra modules and may introduce drift. A prompt alone cannot enforce 1:1 pattern placement. No API key or paid service required for local inference, but GPU hardware and model downloads are required.

## Deliverables
- output.png
- qa.json
- original input references and asset manifest
- README of provenance, licensing, native vs upscaled resolution
See README.md and configs/example_manifest.json.

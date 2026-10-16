---
name: fashion-asset-locked-tryon-v3
version: 3.1.0
description: Reference-first commercial fashion try-on; immutable product evidence, white-wall indoor scene, mandatory preflight and rejection gates.
---
# Fashion Asset-Locked Try-On V3.1 — 商品证据优先

## NON-NEGOTIABLE
This skill is NOT generic text-to-image styling. No image generation until source images have been individually inspected and mapped into the asset ledger. If source pixels are unavailable in the current session, STOP and request the original image assets; do not substitute a textual recollection or generated lookalike. GitHub markdown alone does not bind reference images to a model. Never claim exact 1:1 fidelity without image-level verification.

## Source hierarchy and separation
1. PRODUCT_MASTER: front/back flat-lay and product images are authoritative for SKU geometry, cut, color and closures.
2. DETAIL_MACRO: fabric close-ups are authoritative for print motif, density, rib pitch, edge finish and visible texture.
3. PERSON_ID: person face, hair and natural body volume ONLY. Not outfit, background or camera composition.
4. ACCESSORY_MASTER: each shoe and bag independently; never replace with a visually similar branded item.
5. FIT_REFERENCE: dressing order and fit only; NEVER authoritative for construction.
6. SCENE_REFERENCE: white-wall interior, light, framing and lifestyle mood only. NEVER clothing.
Conflicting sources: product and macro always beat streetwear/lookbook examples. Two distinct dress designs in user examples must not be merged. Document uncertain or invisible details as UNKNOWN, not invented.

## Locked SKU ledger (observed / to re-verify against originals)
INNER TOP: muted warm greige/gray-beige, tightly spaced fine vertical rib, irregular subdued washed/mottled appearance, fitted long sleeves, modest mock-neck, gently waved lettuce/rolled edge on collar and cuffs. FORBIDDEN: floral lace, jacquard, large cables, wide ribs, plain smooth knit, embellished collar.
DRESS: dark chocolate brown fluid slip dress; thin shoulder straps; curved/shallow V front; tiny irregular off-white flowers WITH muted dusty blue-gray botanical elements, consistent motif scale and density; natural waist/side seam and drape per product master; long widening skirt. FORBIDDEN: dots masquerading as flowers, generic random beige confetti, oversized flowers, new waist darts, tiered/ruffled-front dress, altered neckline/strap count, false sheerness.
SHOES: black patent-look chunky loafers, broad rounded-square toe, thick sole, specific vamp ornament from accessory close-up. Never swap hardware to a different luxury monogram.
BAG: black quilted flap shoulder bag with padded diamond quilting and reference-specific chain/metalwork, closure and proportions. Never invent labels or logo details.
PERSON: youthful adult East Asian woman, soft rounded facial shape, naturally mildly plus-size figure; no tiny waist, no elongated legs, no generic adult/mature face. Face and hairstyle governed by person reference.
SET: minimalist WHITE-WALL INDOOR living/bedroom space based on provided indoor references; simple pale wall, restrained furniture, natural window daylight and plausible room shadows. NO cafe, brick exterior, street, cluttered bedroom, staged mirror selfie unless requested. Indoor reference controls space only.

## Mandatory pre-generation preflight (hard stop)
For every original image create source_map with filename or immutable reference id, role, SKU, view, observed detail, crop/region, confidence and conflicts.
Confirm: (a) all required source images accessible; (b) exact target SKU distinguished from other dresses; (c) person reference selected; (d) indoor white-wall references selected; (e) output pose and layering; (f) accessories whether included. If any of a-d fail: DO NOT GENERATE.
Build immutable product_manifest and explicit allowed_change list: pose, lighting, natural fabric wrinkles, camera angle. Everything else requires confirmation.
For reference-based image edits use actual input images in the generation tool, not only a text prompt. If tool cannot preserve reference pixels, state limitation and do not present as SKU-accurate.

## Generation sequence
A. Test inner top and dress asset crops against originals, without a model; inspect print/rib/neckline.
B. Single-garment VTON baseline using product image and person image; FASHN VTON 1.5 one-pieces category. This model is single garment per inference, not verified multi-layer.
C. Experimental two-layer: inner top first then dress, with hard check that collar/sleeves survive and top does not change. If fails, composite with masks or reject.
D. Only after garment PASS, introduce shoes/bag via source-conditioned region repair, then independently inspect each.
E. Place subject in independent white-wall indoor photo setting; avoid regenerating garment if possible. New pose/scene requires extra conditioning beyond baseline VTON.
F. Deliver side-by-side evidence crops, output, pass/fail QA and native dimensions; disclose any upscaling.

## QC rejection gates
Hard FAIL if garment floral motif becomes dots, blue-gray botanical accents vanish, fine ribs become jacquard, neck/cuff edges change, straps/waist seams drift, body slims, shoe ornament swaps, bag hardware drifts, scene is not white-wall indoors, or image copies street reference.
Score each 0-5: top color/texture, top neckline/cuffs, dress print, dress cut/straps/seams, person identity/body, accessory fidelity, indoor set, photography. Required >=4/5 for each applicable field; any hard fail overrides average.
Fail -> diagnose exact region and repair with original crop + mask; no unbounded full-frame retries. If exact pattern transfer unavailable, label result approximate, not approved product photo.

## Capability truthfulness
Text-only skill cannot freeze textile pixels. Exact motif placement requires warping/texture projection or manual compositing with masks. FASHN VTON baseline output and identity preservation are not guaranteed; no claim of production readiness until an actual inference and side-by-side QA pass. 2160x3840 PNG may be upscaled and must be labeled accordingly.

---
name: fashion-asset-locked-tryon
version: 2.0.0
description: Multi-reference product-locked fashion try-on with independent model, apparel, accessory and scene anchors, fidelity checks, and 4K PNG delivery.
---
# Fashion Asset-Locked Try-On Skill V2

## Goal
Create a NEW photograph of the reference person wearing the EXACT reference garments and accessories. Do not copy the reference photograph's composition. Never substitute visually similar merchandise for the source SKU.

## Input roles (strict isolation)
- PRODUCT_MASTER: authoritative flat lay / front / back of SKU; controls construction, geometry, color blocks, hem, straps and seams.
- FABRIC_MACRO: authoritative weave/rib pitch, print motifs and density, optical finish, softness and plausible drape.
- DETAIL_MASTER: neckline, cuffs, hardware, zippers, stitches, seams and edge finish.
- MODEL_ID: facial identity, age appearance, hair, real body silhouette and proportions; not clothing or background.
- FIT_REFERENCE: layering and physical fit only; not identity, pose or scene.
- ACCESSORY_MASTER: separate shoe and bag anchors, silhouettes, closures, soles, hardware and chains.
- SCENE_REFERENCE: optional lighting/location inspiration only; use new staging.

## Required asset ledger
For each visible product element record: id, reference_images, observed_features, unknowns, must_preserve, visibility, risk. Distinguish observation from inference. Never invent unseen details.

## Current reference garment ledger
- INNER_TOP: warm gray-beige fitted long-sleeve rib-knit; fine closely spaced vertical ribs; muted irregular washed/clouded mottling; slightly wavy rolled/lettuce collar and sleeve edges; low sheen. Never replace with broad sweater ribs.
- DRESS: dark chocolate brown thin-strap midi/maxi dress; dense small irregular off-white flowers and muted gray-blue botanical sprigs; matching printed straps; shallow V neckline; widening lower skirt; soft pliable drape. Preserve print scale/density, not generic dots/daisies.
- FIT: top UNDER dress, straps outermost; credible contact at shoulder/bust, print bends with cloth; no floating layers.
- SHOES: glossy black chunky loafers, low block heel, broad rounded-square toe, raised outsole, small gold-tone ornamental vamp medallion. Product photo overrides outfit examples.
- BAG: black quilted flap shoulder bag, diagonal padded diamond quilting, substantial mixed-tone interlocking metal/leather chain, central gold-tone emblem. Keep geometry, do not infer authenticity.
- MODEL: youthful adult woman, softly rounded face and naturally mildly plus-size figure; credible arm/waist/hip volume; no artificial slimming or mature styling. Match supplied person reference rather than invent generic face.

## Workflow
1. Inventory and label source images. Detect conflicts; never silently merge different garments. Product master outranks lookbook reference.
2. Build independent product, textile, person and accessory manifests; flag high-risk microflorals, rib pitch, collar, chain and shoe ornament.
3. Plan a NEW everyday photograph, full-body portrait 9:16, natural 50–85mm-equivalent perspective and credible ground contact. Do not clone source pose, scene or framing.
4. Generate physically plausible dressing: gravity, cloth stretch/compression, folds, occlusion, skin-to-fabric contact and realistic skirt weight.
5. Compare reference-aligned crops for neckline, sleeve, bodice, skirt, hem, shoe and bag. Reject any SKU-critical drift.
6. Correct failed REGIONS with source crops and inpainting; preserve passing regions. Avoid full-image regeneration for one detail.
7. Check anatomy, hair separation, skin response and directional light. No fake pores, uniform grain or indiscriminate sharpening.
8. Export lossless PNG, preferably native 2160x3840. Disclose upscaling; never imply upscale recreates genuine fabric microstructure.

## Priorities and acceptance
Hard gates: garment construction, two-layer order, fabric identity, person identity, accessory geometry. Photography is secondary to SKU accuracy.
Weighted review: construction 25%, fabric/print 25%, model 20%, accessories 15%, fit 10%, photography 5%.
Automatic fail: altered silhouette/neckline/straps, wrong flower/rib structure, swapped product, different face, excessive slimming, impossible limbs or fake contact/shadow.
Never call a result pixel-exact 1:1 without reference-aligned verification.

## Negative constraints
No clothing redesign, generic florals, broad ribs, random straps, missing hems, extra seams, melted ornaments, wrong chain links, plastic skin, fused hair, warped hands, floating feet, HDR sheen, invented logos or copied backgrounds.

## Prompt template
Use PRODUCT_MASTER and FABRIC_MACRO as immutable SKU references. Dress the adult MODEL_ID person in the precise INNER_TOP + DRESS, matching construction, rib pitch, washed pattern, tiny irregular flowers, neckline, straps, drape and hem. Use SHOES and BAG from their independent product references, matching visible hardware and silhouette. Shoot a new authentic everyday 9:16 photograph with natural proportions, gravity/contact, real hair/skin and subtle photographic imperfections. Do not alter merchandise. Validate each product region before delivery.

## Technical limits
Text prompts alone cannot guarantee deterministic product identity. Commercial-grade fidelity needs a multi-image-conditioned generation backend, region masks/inpainting, identity reference and ideally texture projection/warping. Exact textile pattern placement may require compositing. Keep reference and output provenance.
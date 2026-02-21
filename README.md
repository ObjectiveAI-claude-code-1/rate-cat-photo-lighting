# rate-cat-photo-lighting

Scores how effectively the lighting in a cat photograph reveals the cat as a subject. Evaluates subject clarity, tonal balance, and lighting integrity. The standard is functional light that makes the cat visible and appreciable — not studio perfection. Penalizes overexposure, deep shadow, glare, and unnatural color casts.

## Input

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `cat_photo` | `image` | Yes | A photograph containing a cat. |

The input is a single photograph of a cat from any source — a phone snapshot in a dim apartment, a DSLR capture in a sunlit garden, a hasty photo from a veterinary clinic. The function does not expect professional photography. It evaluates whatever light was present from the perspective of the cat as subject: does this light let the viewer see the cat?

## Output

A scalar score in the range `[0, 1]` representing how well the lighting in the photograph serves the cat as a subject.

- **1.0** — The lighting fully reveals the cat. Its face, fur texture, and body form are effortlessly visible with balanced exposure and no distracting artifacts.
- **0.5** — The lighting is functional but imperfect. The cat is visible, though some features may lack definition, some tonal detail may be lost at the extremes, or minor artifacts may be present.
- **0.0** — The lighting fails the cat. The animal is hidden by darkness, obliterated by overexposure, or distorted by severe artifacts to the point that the viewer cannot clearly see or appreciate it.

## What It Evaluates

The function evaluates three qualities of lighting, each focused on whether the light serves the cat as a subject.

### 1. Subject Clarity

Does the lighting allow the viewer to clearly perceive the cat's physical presence? The cat's face, eyes, fur texture, and body form should be visible without effort. Fur texture is especially important — it is one of the defining visual characteristics of a cat, and lighting that renders it as a flat, indistinct mass has failed. The function scores highly when soft, functional light models the planes of the cat's face and reveals the depth of its coat. It scores poorly when the cat is lost in darkness or rendered so dimly that the viewer must strain to make out its features.

### 2. Tonal Balance

Does the brightness range across the cat preserve detail at both extremes? The brightest areas should still carry visible texture — not blown out into featureless white. The darkest areas should remain readable — not collapsed into impenetrable shadow. Some contrast is natural and welcome; gentle shadows give the cat dimension. The failure is at the extremes: harsh overexposure that erases detail, or deep underexposure that reduces the cat to a silhouette stripped of individuality.

### 3. Lighting Integrity

Does the light present the cat honestly, without distracting artifacts? The function penalizes extreme glare, hard specular hot spots, and unnatural color casts that interfere with the viewer's perception. Natural color temperatures are acceptable — the golden warmth of late afternoon, the cool blue of shade, the soft neutrality of overcast sky. The failure is when the color or quality of the light feels wrong, incoherent, or obtrusive: a sickly green fluorescent cast, a harsh blue flash, or bright glare that pulls attention away from the cat toward the light itself.

## Use Cases

- **Pet adoption platforms** — Automatically surface or prioritize listings where the animal is clearly visible, helping potential adopters see the cats they're considering.
- **Photo communities and contests** — Filter or rank cat photograph submissions by lighting quality, ensuring featured images show their subjects clearly.
- **Automated image pipelines** — Score incoming cat photographs for quality control, flagging poorly lit images for re-capture or deprioritization.
- **Social media and content curation** — Rank user-submitted cat photos so that well-lit, clearly visible cats appear first in feeds or galleries.
- **Veterinary and breeder documentation** — Ensure that reference photographs of cats are well-lit enough to clearly show physical features, coat condition, and markings.

## Philosophy

The function asks one question: does this light reveal the cat? It is not a general photography aesthetics score. It does not reward dramatic atmosphere, artistic shadow play, or golden-hour backlighting for their own sake. A cat under ordinary kitchen ceiling lights, fully visible with readable fur and a clear face, scores well. A cat silhouetted against a spectacular sunset does not — no matter how beautiful the sky. The light is in service to the cat, not the other way around. When the lighting works, it disappears. You don't think about it. You just see the cat.
--- 
name: launch-deck
description: Use when creating a launch presentation, pitch deck, or product launch slides for a B2B SaaS product. Triggers on: launch deck, presentation, pitch deck, launch slides, product launch presentation, GTM deck, go to market deck, create a deck, build a presentation.
---

# Launch Deck

Creates a fully branded presentation covering the complete product launch story. Each slide is built from research and messaging outputs. Output format is PowerPoint only. Save as: outputs/launch-deck.pptx

## How

### Step 1 - Load context

Always read:
Read clients/[client-name]/brand.md — especially the Visual references, Material and lighting language, Mood descriptors, Anti-references, What is allowed and encouraged, Reference quality test, and Visual approach sections.
Read clients/[client-name]/voice.md

Read if available:
If outputs/jtbd-analysis.docx exists read it.
If outputs/positioning.docx exists read it.
If outputs/messaging-framework.docx exists read it.
If outputs/competitive-analysis.xlsx exists read it.
If outputs/landing-page-copy.docx exists read it.

If no outputs exist ask:
What is the product?
Who is the ICP?
What is the launch goal?
What is the timeline?

### Step 2 - Verify visual approach

This is a mandatory check before any slide is composed.

Read the Visual approach section of brand.md carefully. That section defines the subject direction for this specific client: what the default subject should be for any visual element, which scenes work, which alternatives are allowed, and what must never be the primary subject.

The Visual approach section of brand.md is the authoritative source for subject direction. When any slide in this deck requires a visual element (hero image, section divider background, proof point imagery, transition slide), the subject must follow the rules in brand.md Visual approach.

Also check if the folder clients/[client-name]/references/decks/ exists and contains image files. If it does, read each reference image using vision capability. These references are pattern-matching targets for slide composition, lighting, and layout.

Write down in working memory:
- What is the default visual subject for this client according to brand.md?
- What slide compositions do the deck references suggest?
- What must never be the primary subject?

Carry these rules into every slide that requires a visual element.

### Step 3 - Plan the narrative

Before building establish:
- What is the single story running through all slides?
- What is the one thing the audience must remember?
- What action should they take after seeing this deck?

Every slide must serve that one story. No slide is filler. No slide repeats another.

### Step 4 - Build the presentation using brand guidelines

Mandatory image generation: the following slides must each include a Nano Banana generated image featuring a human subject per brand.md Visual approach rules. This is not optional. The deck is not complete until these images exist on the slides.

Mandatory image treatment (DEFAULT — applies to every deck image): every Nano Banana image injected into the deck MUST pass through `skills/launch-deck/image_fix.py`, which handles aspect-ratio correction, center-crop, AND bakes a left+bottom edge vignette fading into #0a0a0a on the portrait image slots (slides 1, 4, 9 by default). Images must never sit in a visible hard rectangular box. The vignette is controlled by the per-slot `vignette` field in the `SLOTS` registry in `image_fix.py` — `{"fade_left": 0.30, "fade_bottom": 0.40}` by default on image-right portrait slots; `{}` on slides that use a different treatment (e.g. slide 3's tight crop or slide 5's full-bleed). Do not bypass `prepare_image()` and inject raw Nano Banana output directly into the pptx. Use the `build-deck.py` pipeline (or the same pattern) so pre-processing, picture insertion at spTree index 3, and XML patching all happen in order.

SLIDE 1 - COVER: Generate a Nano Banana image of a human subject that evokes the product tagline. Use as a full-bleed or partial background behind the title text. The human should be in a premium editorial scene connected to the product story.

SLIDE 3 - MARKET PROBLEM: Generate a Nano Banana image of a human experiencing the frustration described in the pain points. This person is the ICP before they find the product. Dark, moody, editorial.

SLIDE 4 - TARGET AUDIENCE: Generate a Nano Banana image that serves as a portrait of the persona. Profile or three-quarter view, editorial lighting, the person absorbed in their work. This is the face of the ICP.

SLIDE 5 - PRODUCT OVERVIEW: Generate a Nano Banana image of a human using the product. Over-the-shoulder shot of someone looking at a screen showing a dark-mode UI, or hands on a keyboard with screen glow. The product in use, through the lens of the human using it.

SLIDE 9 - THANK YOU: Generate a Nano Banana image of a human in a moment of quiet confidence or satisfaction. The emotional payoff of the deck story. Someone who has just closed a deal, stepped back from their desk, or achieved the outcome the product promises.

Slides 2, 6, 7, and 8 (Executive Summary, Competitive Landscape, Marketing Strategy, Launch Timeline) are data-driven slides and are exempt from image generation. They use typography, color, and layout only.

For each image generation call:
- Write a Nano Banana prompt of 60-100 words minimum.
- Start with the specific human scene, not style descriptors.
- Include composition, lighting, color palette (black 0a0a0a, Vibranium Purple 7B2FBE), and mood.
- Reference the closest match from clients/[client-name]/references/decks/ if available.
- Save each generated image to a temporary path, then embed it in the corresponding slide.

The deck generation workflow is: generate all five images first, then build the nine slides with the images placed on the appropriate slides, then save the pptx. Do not build the slides first and add images later. Images first, slides second.

Background: #0a0a0a
Primary accent: #7B2FBE
Deep purple: #4A0E8F
Light purple: #9D4EDD
Soft lavender: #C77DFF
Font: Inter from Google Fonts
Primary text: #FFFFFF
Secondary text: #CCCCCC
Card background: #111111
Slide counter: bottom right of every slide

SLIDE 1 - COVER
Product name large and centered. Tagline directly below. Launch date or version below tagline. Vibranium Purple accent line or border. Clean. Minimal. Confident.

SLIDE 2 - EXECUTIVE SUMMARY
What is being launched. Primary launch goal. Key timeline milestones. Top 3 success metrics. One screen. No scrolling.

SLIDE 3 - MARKET PROBLEM
Lead with the pain the ICP lives with. Use trigger events from JTBD analysis. 3 to 5 specific pain points. Quantify where possible. End with the cost of doing nothing.

SLIDE 4 - TARGET AUDIENCE
Primary persona name and title. Key responsibilities. What they care most about. What keeps them up at night. Simple card layout. Clean.

SLIDE 5 - PRODUCT OVERVIEW
Product name and one line description. How it works in 3 simple steps. 5 key features with benefits. Steps numbered in Vibranium Purple.

SLIDE 6 - COMPETITIVE LANDSCAPE
Visual comparison matrix. Rows are key buying criteria. Columns are this product and top 3 competitors. Strong, Partial, or Weak ratings. This product column is highlighted in Vibranium Purple.

SLIDE 7 - MARKETING AND LAUNCH STRATEGY
Pre launch activities. Launch day activities. Post launch activities. Key channels and messages. Three column layout or timeline.

SLIDE 8 - LAUNCH TIMELINE
Visual timeline from today to launch. Key milestones marked clearly. Pre launch phase in grey. Launch in Vibranium Purple. Post launch in white.

SLIDE 9 - THANK YOU
Large centered "Thank you" in Inter Bold. Product name below in smaller Inter Regular. Primary CTA below that (contact, demo link, or next step). One Vibranium Purple accent element. Optional: a subtle atmospheric background element if brand.md Visual approach allows, otherwise keep the slide pure #0a0a0a with type only. Feel: confident close, not decorative.

### Step 5 - Review before saving

Check every slide:
- Brand colors consistent throughout.
- Inter font used everywhere.
- Vibranium Purple accents on key elements.
- Every slide has one clear message.
- No slide is too text heavy.
- Slide counter is accurate.
- Product name visible on every slide.
- Narrative flows logically slide to slide.

### Step 6 - Save output

Save as: outputs/launch-deck.pptx

## When
- When asked for a launch deck
- When asked for a pitch deck
- When asked for launch slides
- When asked for a GTM presentation
- Works standalone or as part of full agent workflow
- If prior outputs exist they feed the slide content automatically
- If no prior outputs exist asks four questions and builds from available information

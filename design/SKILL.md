---
name: design
description: Use when creating visual assets for a B2B SaaS product launch. Covers social graphics, presentation decks, and landing page visual direction. Triggers on design, create a graphic, social post, LinkedIn image, carousel, presentation, deck, slides, visual, brand asset, launch graphic, banner, design the deck, design the post.
---

# Design

## What this skill does
Creates visual assets for a B2B SaaS product launch. Three output types:

Social graphic
A single branded image for LinkedIn or similar platforms. Generated via Nano Banana.
Saved as: outputs/social-graphic.png

Launch deck
A nine-slide PowerPoint launch deck with a fixed narrative structure.
Saved as: outputs/launch-deck.pptx

Design brief
A detailed visual direction document for the developer agent to build from.
Saved as: outputs/design-brief.md

## How this skill works

### Step 1 - Load context

Read these files in order, before doing anything else:

1. clients/[client-name]/brand.md — especially the Visual references, Material and lighting language, Mood descriptors, Anti-references, What is allowed and encouraged, Reference quality test, and Visual approach sections.
2. clients/[client-name]/voice.md
3. clients/[client-name]/outputs/positioning.md or positioning.docx if it exists
4. clients/[client-name]/outputs/messaging-framework.md or messaging-framework.docx if it exists

If any of these files are missing, stop and report what is missing. Do not proceed with partial context.

### Step 2 - Verify visual approach

This is a mandatory check before any visual is produced.

Read the Visual approach section of brand.md carefully. That section defines the subject direction for this specific client: what the default subject should be (humans, product UI, abstract, etc.), which scenes work for the product, which compositions are allowed alternatives, and what must never be the primary subject.

The Visual approach section of brand.md is the authoritative source for subject direction. It overrides any default assumptions this skill might make about what subjects are appropriate.

Write down in your working memory:
- What is the default subject for this client according to brand.md?
- What are the allowed alternatives?
- What must never be the primary subject?

Carry these rules into every deliverable in the rest of this skill.

### Step 3 - Check for reference library

Check if the folder clients/[client-name]/references/ exists. If it does, check its subfolders:
- references/social-graphics/
- references/decks/
- references/landing-pages/

For each subfolder that contains image files, read each image using vision capability. For each reference, note in working memory: the subject, the composition, the lighting, the color handling, and the overall feeling.

These references are pattern-matching targets. When producing a deliverable, identify which references are closest matches and use them to ground the Nano Banana prompts, deck slide compositions, and landing page visual direction.

If the references folder is empty or does not exist, proceed using only brand.md as the guide.

### Step 4 - Social graphic

The social graphic is a single branded image produced via Nano Banana.

Platform dimensions:
- LinkedIn and Twitter: 1200 x 628 px (default for this skill)
- Instagram square: 1080 x 1080 px
- Instagram story: 1080 x 1920 px

Use 1200 x 628 px unless the client specifies otherwise.

Production sequence:

1. Concept phase. Read the tagline and key message from messaging-framework.md. Propose three distinct visual concepts for the graphic. Each concept must reference a specific subject from the Visual approach section of brand.md, must have a clear narrative connection to the tagline, and must leave clear negative space for text overlay. Evaluate the three concepts and pick the strongest. Never default to floating abstract forms, crystals, polyhedrons, or luxury object macros unless brand.md explicitly lists them as allowed.

2. Reference anchor. Identify the closest-matching image in references/social-graphics/ (if any) or the closest-matching named brand in the brand.md Visual references section (if no image library). The Nano Banana prompt must explicitly pattern-match to this reference.

3. Prompt construction. Write a Nano Banana prompt that is 60-100 words minimum. The prompt must include:
   - The specific subject and scene from the picked concept, stated concretely. Not a style descriptor.
   - A reference anchor phrase like "in the visual language of [named brand or reference image]."
   - Composition direction: rule of thirds, centered hero, left-anchored subject, etc. State which one explicitly.
   - Lighting direction: single directional source, rim light, screen glow, volumetric rays. State which one explicitly.
   - Color palette: black #0a0a0a background, Vibranium Purple #7B2FBE accent. State these explicitly.
   - Mood: premium, cinematic, quiet, intentional. Pick the relevant mood words.
   - Negative space instruction: reserve a specific portion of the frame (typically 40-50%) for text overlay, and specify which side.

4. Generate. Call the Nano Banana MCP tool with the constructed prompt. Save the output to clients/[client-name]/outputs/social-graphic.png.

   When compositing the final 1200x628 graphic via skills/design/social-graphic-template.html, the image side of the canvas MUST blend into the #0a0a0a canvas via a CSS mask-image vignette, never sit in a hard box with a border. The template ships with the correct mask-image + mask-composite: intersect CSS already in place — do not re-add border-radius, border, or pseudo-element gradient overlays on the image container. The subject should look like they're emerging from the page.

5. Quality check. Before finishing, ask: does this image have a recognizable subject connected to the product, or is it generic AI render? Does it respect the Visual approach rules in brand.md? Would it look at home next to the reference images or named brands? If any answer is no, regenerate with a revised concept.

### Step 5 - Launch deck

The launch deck is a nine-slide PowerPoint file with a fixed narrative structure.

Slide structure (in order):

Slide 1 - Cover
Product name large and centered. Tagline below in Vibranium Purple. Launch context small below tagline. Feel: confident, premium, minimal.

Slide 2 - Executive Summary
What is being launched, the primary launch goal, key milestones (three points), success metrics (three numbers). Two-column clean grid layout.

Slide 3 - Market Problem
Open with the JTBD trigger event. Three to five specific pain points, one line each, quantified where possible. End with the cost of doing nothing. Vibranium Purple numbers on each point.

Slide 4 - Target Audience
Persona name and title large. Key responsibilities (three points). What they care about (three points). What keeps them up at night (one line). Single persona card centered.

Slide 5 - Product Overview
Product name and tagline at top. How it works in three steps with Vibranium Purple numbered markers. Key capabilities as five bullet points. Steps on the left, bullets on the right.

Slide 6 - Competitive Landscape
Matrix comparing this product against the top three competitors. Rows are key buying criteria. Columns are products. Ratings are Strong, Partial, or Weak. This product's column highlighted in Vibranium Purple.

Slide 7 - Go To Market Strategy
Pre-launch activities and channels. Launch activities and channels. Post-launch activities and channels. Three-column layout with Vibranium Purple dividers.

Slide 8 - Launch Timeline
Visual timeline running left to right. Key milestones as Vibranium Purple dots. Phase labels above the line. Dates below the line.

Slide 9 - KPIs and Forecast
Primary metric large and centered in Vibranium Purple. Three to five supporting metric cards. Each card shows metric, target, and timeframe. Vibranium Purple on all target numbers.

Deck design rules (enforced on every slide):
- Background #0a0a0a on every slide.
- Vibranium Purple #7B2FBE accent applied purposefully, never decoratively.
- Inter font family throughout, maximum two weights per slide.
- One idea per slide. If the slide has two ideas, split it.
- Headlines are statements, not labels. Not "Problem." Write "Most sales teams lose 40% of pipeline to slow follow-up."
- Maximum 15 words of body text per slide where possible.
- Visual focal point on every slide. Never a title plus bullet list only.
- Product name small in the top-left corner of every slide. Slide number in the bottom-right.
- When a slide has a visual element (image, diagram, chart), apply Visual approach subject direction from brand.md.
- Every Nano Banana image injected into the deck MUST pass through skills/launch-deck/image_fix.py, which pre-applies a left+bottom edge vignette (fading into #0a0a0a) by default via the per-slot `vignette` field in SLOTS. Image slots must never sit in a hard rectangular box with a visible edge. If a slot should skip the vignette (e.g. the full-bleed product slide), set its `vignette` entry to `{}` in SLOTS.

Production method:
Generate the deck as a real PowerPoint file (.pptx) using python-pptx. Before saving, read /mnt/skills/public/pptx/SKILL.md for the technical method. The output must be a genuine .pptx that opens cleanly in PowerPoint and Keynote.

Save as: clients/[client-name]/outputs/launch-deck.pptx

### Step 6 - Design brief

The design brief is a detailed visual direction document for the developer agent. Not code. Direction.

Produce a brief covering the following sections:

Overall direction
Which aesthetic is being applied. What makes it memorable. What the visitor should feel in the first five seconds of landing on the page.

Navigation specs
Height, background treatment, scroll behavior, logo placement, CTA button placement, button styling.

Hero section specs
Height, background treatment, headline typography and color, subheadline typography and color, CTA button styling, trust signal placement. Explicitly reference the Visual approach from brand.md for hero imagery direction — whether the hero uses a human subject, a product UI element, or abstract composition.

Hero image treatment: the hero image MUST blend into the page background via a CSS mask-image vignette, never sit in a boxed container with a border or rounded corners. Strongest fade on the left edge (into the headline text column) and the bottom edge (into the next section); subtle fade on top and right. Use two mask-image gradients composited with mask-composite: intersect. No border-radius, no border, no drop shadow, no gradient overlay pseudo-elements. The subject should appear to emerge from the page.

Social proof bar specs
Background, logo treatment, framing line.

Problem section specs
Background, typography for numbers and text, maximum number of pain points.

Solution section specs
Background, step number treatment, step text treatment, layout pattern.

Features section specs
Background, card background, card border, card radius, card padding, typography for feature name and benefit, hover state behavior.

Social proof testimonial specs
Background, card background, border treatment, typography for quote, name, and title.

FAQ specs
Background, question typography, answer typography, divider treatment, icon behavior.

Closing CTA specs
Background, headline typography, button styling.

Footer specs
Background, border treatment, text color.

Animation specs
Page load behavior, scroll-triggered elements, hover transitions, button scale, card hover states.

Color system
List the exact hex values from brand.md and which UI elements each color applies to.

Typography system
List the exact Inter weights from brand.md and which UI elements each weight applies to.

Save as: clients/[client-name]/outputs/design-brief.md

### Step 7 - Quality review

Before considering any deliverable complete, run this checklist:

- Does the deliverable pass the Reference quality test from brand.md? Does it look like a $200M Series B SaaS company's marketing, or like a startup template?
- Does the deliverable respect the Visual approach rules from brand.md, especially subject direction?
- Is the background pure black #0a0a0a with optional subtle texture, never flat and dead?
- Is Vibranium Purple used purposefully on the most important element, never decoratively across multiple elements?
- Is Inter the only font family, with no more than two weights per composition?
- Is there a clear visual hierarchy with a single focal point?
- Is there enough negative space that the composition feels confident rather than crowded?
- Would a VP Marketing at a premium B2B SaaS company be willing to share this publicly under their own name?

If any answer is no, iterate on that element before saving.

## When to use this skill

- When asked to create any visual asset for a B2B SaaS launch
- When asked for a social graphic, LinkedIn image, or carousel
- When asked for a launch deck or presentation
- When asked for a landing page design brief or visual direction
- When the design agent is invoked
- Always reads brand.md first, especially the Visual approach section
- Always checks for a reference library before generating prompts
- Uses Nano Banana for social graphics
- Uses python-pptx for the launch deck
- Produces a design brief for the developer agent
- Works standalone or as part of the full agent workflow

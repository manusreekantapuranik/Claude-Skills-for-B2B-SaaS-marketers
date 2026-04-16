--- 
name: competitive-analysis 
description: Use when researching competitors, analyzing competitive landscape, or producing a competitive analysis for a B2B SaaS product.
Triggers on: competitive analysis, competitor research, competitive landscape, how do we compare, competitor positioning, battlecard, competitive intelligence. 
---

# Claude Skill Name: Competitive Analysis

## What does this skill do?
A focused competitive analysis that researches competitor positioning, messaging, features, integrations, and key customers.
Produces a structured Excel workbook with actionable intelligence. 
Saved as: outputs/competitive-analysis.xlsx 

## How does the skill work?

### Step 1 - Load context
Always read:
Read icp.md
Read brand.md
Read voice.md
Read competitors.md

Read if available:
If outputs/jtbd-analysis.docx exists read it.
If outputs/positioning.docx exists read it.

If competitors.md does not exist ask:
Who are the top 3 to 5 competitors?
What is the product being compared?
What is the primary ICP?

### Step 2 - Research each competitor
For each competitor use Apify to scrape 
their website thoroughly.

Scrape these pages for each competitor:
Homepage
Product and features page
Pricing page structure (not prices)
Integrations page
Customers and case studies page
About page
Blog (last 5 posts for messaging themes)

Extract for each competitor:

Positioning
Their exact headline word for word.
Their exact tagline word for word.
Their exact subheadline word for word.
What category they claim to own.
Who they explicitly say they are for.
What outcomes they explicitly promise.
How they describe their ideal customer.
What problem they say they solve.

Messaging
Every repeated phrase across pages.
What emotions they target.
What fears they address.
What aspirations they speak to.
What objections they pre-empt.
How they talk about AI and automation.
What their CTA says exactly.
What their social proof says.

Features
Every core feature they list.
Every AI or automation capability.
How they describe each feature.
What benefit they attach to each feature.
What they lead with on the homepage.
What they bury deep in features pages.
Any unique or proprietary technology.
Any certifications or compliance claims.

Integrations
Every integration they list.
Which integrations they highlight first.
Which categories of tools they cover.
Whether they have an open API.
Whether they have a marketplace.

Key customers
Every logo they show publicly.
Every case study they publish.
Which industries they serve.
Which company sizes they target.
Specific results they claim in 
case studies.
Any notable enterprise customers.

Competitive claims
Do they have a comparison page?
Who do they compare against?
What claims do they make vs competitors?
What do they say they do better?

Recent activity
Last 5 blog post titles and topics.
Any recent product announcements.
Any recent press releases.
Any awards or recognitions shown.

### Step 3 - Build competitive matrix
Compare this product against all competitors across these criteria:
- Positioning clarity
- Messaging strength
- Feature depth
- AI capabilities
- Integration breadth
- Ease of use
- ICP fit
- Market presence

For each criterion rate each product: Strong, Partial, or Weak. Do not add scores or percentages. Simple three tier rating only. Rate this product honestly. Gaps are useful intelligence.

### Step 4 - Identify whitespace
Based on all research identify:
Where are all competitors weak?
What do customers consistently want that nobody delivers?
What positioning angle is unclaimed?
What ICP is underserved?
What messaging theme is overused?
What integration is missing everywhere?
This is the most valuable output. It tells you exactly where to win.

### Step 5 - Produce Excel output
Create an Excel workbook with these sheets:

SHEET 1 - SUMMARY
One row per competitor.
Columns: Name, Category, ICP, Core value proposition, Key strength, Key weakness, Notable customers.

SHEET 2 - POSITIONING AND MESSAGING
Columns: Competitor, Headline, Tagline, Category claimed, ICP stated, Core promise, Emotional angle, Key phrases used.

SHEET 3 - FEATURES AND INTEGRATIONS
Columns: Competitor, Core features, AI capabilities, Key integrations, API availability, Unique capabilities, What they lead with.

SHEET 4 - COMPETITIVE MATRIX
Rows are buying criteria. Columns are this product and each competitor. Values are Strong, Partial, or Weak. Highlight this product column in Vibranium Purple.

SHEET 5 - WHITESPACE
Unmet customer needs.
Unclaimed positioning angles.
Underserved ICP segments.
Missing integrations.
Recommended differentiation moves.

Save as: outputs/competitive-analysis.xlsx

## When should you use this skill?
- When asked for competitive analysis
- When asked about competitors
- When asked how we compare
- When building positioning or messaging
- Uses Apify to scrape live data

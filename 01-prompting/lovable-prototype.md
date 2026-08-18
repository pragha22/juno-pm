# Lovable Prototype · Juno

> Module 1 · Prompting. The clickable Lovable prototype that brings the system prompt to life.

Act as a Senior Principal Frontend Engineer with 10+ years of experience building high-density B2B SaaS analytics dashboards. You specialize in crafting polished React 18, Tailwind CSS, and Shadcn/UI interfaces featuring dark-mode aesthetics, strict spatial hierarchy, and zero layout shift.

1. PRODUCT CONTEXT & CORE GOAL
Build a clickable single-page prototype for 'Juno PM', an AI Associate PM tool at RocketShip.
Juno synthesizes messy customer feedback (interview transcripts, support tickets, emails) into evidence-backed PRD drafts, replacing context switching across Slack, Notion, and Jira.

2. DESIGN SYSTEM & TECHNICAL STACK SPECIFICATIONS
UI Architecture: React 18 (Functional Components, useState), Tailwind CSS, Lucide React icons (Sparkles, FileText, Zap, RotateCcw, Copy, Check).

Color Palette & Design Tokens:

Canvas Background: #07162C (deep midnight blue)

Surface Elevation 1 (Cards & Containers): #0C2244 with border rgba(255, 255, 255, 0.08)

Primary Action Color: #1241B0 (electric blue, hover: brightness-115)

Accent Highlights: #60A5FA (light sky blue) and #79C0FF

Priority P0 Badge: Background rgba(239, 68, 68, 0.12), Border rgba(239, 68, 68, 0.3), Text #FCA5A5

Priority P2 Badge: Background rgba(245, 158, 11, 0.12), Border rgba(245, 158, 11, 0.3), Text #FDE047

Filtered Badge: Background rgba(148, 163, 184, 0.08), Border rgba(148, 163, 184, 0.2), Text #CBD5E1

Typography:

Headings: Poppins (Bold, 600-800 weight)

Body & UI Text: Lato or standard sans-serif (400-500 weight)

Code & Textarea Inputs: IBM Plex Mono / Fira Code

Border Radii: 14px (rounded-xl) for panel containers; 8px (rounded-lg) for sub-cards; 999px (rounded-full) for main pill buttons.

3. LAYOUT ARCHITECTURE
Page Layout: Full viewport height (h-screen, overflow-hidden), flex column shell with a top navbar and a main 3-column equal-width layout.

Header (56px fixed height):

Left: Logo badge (width: 32px, height: 32px, background #1241B0, letter "J" in bold white) + Title "Juno PM" with subtitle "/ AI Associate PM".

Right: Subtle pill status tag: Green live pulse dot + text "RocketShip Workspace · Claude 3.5 Sonnet".

Dashboard Grid: 3 equal columns (grid grid-cols-3 gap-4, min-w-[1280px]). Ensure columns fill remaining vertical screen height with internal scrollable bodies.

4. COLUMN-BY-COLUMN COMPONENT SPECIFICATION
Column 1: RAW USER TRANSCRIPTS
Header: Title "1. RAW USER TRANSCRIPTS" + Secondary action button "Reset Input".

Main Input: Full-height monospace for raw user transcripts.

Default State: Pre-populate with this exact transcript text:
Interviewer: So, tell me about your workflow.
User (Sarah, Data Analyst): honestly, it's been a week. My dog has been barking all morning, sorry if you hear him. Anyway, I log into RocketShip every Monday. The first thing I notice is that the new blue navigation bar is really bright, like hurts my eyes bright. Can we change that? But yeah, so I go to the 'Quarterly Reports' tab. I select my date range, usually last 90 days, and hit 'Generate PDF.' That works fine. But then, and this is the part that makes me want to scream, I try to click 'Export to CSV' because I need to pivot this in Excel. It spins for like 5 minutes and then just crashes. No error message. Just blank. I've lost hours because of this. I end up just taking screenshots of the table, which is stupid. Oh, and I'd love a dark mode.

Footer Action Bar: Prominent, full-width pill button "⚡ Process Transcript" pinned persistently to the bottom of the column.

Column 2: STRUCTURED INSIGHTS
Header: Title "2. STRUCTURED INSIGHTS" + Dynamic badge showing "0 Signal Items" (idle) or "3 Items Synthesized" (processed).

Idle State: Centered empty state container featuring a Sparkles icon:

Title: "Awaiting Processing"

Description: "Click 'Process Transcript' to synthesize raw inputs into actionable signal."

Processed State: Render 3 distinct structured cards:

Card 1 (Critical Problem):

Badges: [P0 · REVENUE BLOCKER] [FRUSTRATED]

Title: "CSV Export Timeout & Silent Crash"

Quote: "It spins for like 5 minutes and then just crashes. No error message. Just blank. I've lost hours because of this."

Card 2 (Usability Issue):

Badges: [P2 · ERGONOMICS] [NEGATIVE]

Title: "Navigation Luminance & Eye Strain"

Quote: "The first thing I notice is that the new blue navigation bar is really bright, like hurts my eyes bright."

Card 3 (Noise Exclusion):

Badges: [FILTERED NOISE] [NEUTRAL]

Title: "Background Noise Excluded"

Note: "Personal banter regarding barking dog automatically filtered from requirements model."

Column 3: DRAFT PRD
Header: Title "3. DRAFT PRD" + Secondary action button "Copy Markdown" (hidden during idle state, visible when processed).

Idle State: Centered empty state container with a FileText icon:

Title: "No PRD Draft Generated"

Description: "Processed transcripts will automatically construct an evidence-backed Opportunity Brief here."

Processed State: Scrollable markdown container rendering an Opportunity Brief:

Title: # Opportunity Brief: Fix CSV Export Timeout & Silent Failure

Section 1: ## 1. Problem Statement (Detailing timeout & silent crash on 90-day exports).

Section 2: ## 2. Evidence & Business Impact (Target Persona: Sarah; Pain Quote; Workaround: Manual table screenshots; Priority: P0 Revenue Blocker).

Section 3: ## 3. Proposed Solution (Asynchronous Celery/Redis queue for CSV generation + frontend status polling & progress bar + error toast boundaries).

Section 4: ## 4. Success Metrics (0% silent crashes, export dispatch latency <200ms).

5. INTERACTIVE STATE MACHINE & LOGIC
Processing Simulation:

Clicking "⚡ Process Transcript" disables the button, replaces icon with a spinning loader, and changes label to "Synthesizing Signal & PRD...".

After a 1500ms delay, reveal the 3 structured insight cards in Column 2 and the populated PRD in Column 3. Update status badges accordingly.

Copy Action:

Clicking "Copy Markdown" copies the raw PRD text to navigator.clipboard and displays a floating green toast message ("Copied PRD Markdown to clipboard") in the bottom-right for 2 seconds.

Reset Action:

Clicking "Reset Input" restores the default Sarah interview text in Column 1 and clears Columns 2 & 3 back to their initial empty states.

6. STRICT BOUNDARY CONSTRAINTS
DO NOT create login/signup screens, authentication modal flows, or onboarding walkthroughs.

DO NOT include sidebars, vertical navigation panels, or settings/configuration pages.

DO NOT allow standard laptop screen widths (≥1280px) to reflow or stack columns vertically.

DO NOT hide the "Process Transcript" button behind vertical scrollbars.

## Prototype link

https://rocketship-prd-new.lovable.app/


## What it demonstrates

_The one flow this prototype proves._

_____

## Debrief

- **What worked:** _____
- **What broke / felt like a toy:** _____
- **What I'd change next pass:** _____

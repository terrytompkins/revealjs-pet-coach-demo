# Claude Code Prompt: Build the Promptly-at-9 Reveal.js Lesson Deck

## Purpose

Create a Reveal.js-based lesson deck for an internal Promptly-at-9 AI class.

The class topic is:

**Presentations as Code: Using Claude Code and Reveal.js to Build Adaptive Product Walkthroughs**

The goal of this deck is to teach the class why AI coding agents make frameworks like Reveal.js newly practical for a wider audience, including product managers, UX designers, architects, engineering leads, and other non-front-end specialists.

This is the **teaching deck**, not the Pet Coach demo artifact. The Pet Coach demo deck will be a separate Reveal.js deck that this lesson deck links to or launches as a separate browser tab.

---

## High-level teaching message

The central lesson is:

> AI coding agents make it practical for more people to create software-shaped work artifacts. Reveal.js is a good example: it has existed for years, but setup, HTML, CSS, JavaScript, dependency management, and deployment made it feel out of reach for many non-developers. Claude Code can now help people generate, revise, restructure, and maintain these artifacts.

The lesson should not claim that Reveal.js replaces PowerPoint or AI slide generators such as Claude Cowork or Claude Design. Instead, the deck should objectively explain that each tool has different strengths.

Use this framing:

- PowerPoint / Claude Cowork / Claude Design are excellent for polished, linear slide decks.
- Reveal.js + Claude Code is useful when a presentation should behave more like a structured, navigable, web-native artifact.
- Reveal.js shines when a deck needs optional depth, branching, embedded examples, code, diagrams, UI mockups, version control, or publication as a static site.

---

## Required project structure

The repository is named `revealjs-pet-coach-demo/`. Place both decks as sibling subfolders inside it, with the prompts and a top-level README at the root:

```text
revealjs-pet-coach-demo/
  lesson-deck/                  # Teaching artifact (this prompt builds it)
  pet-coach-journey-deck/       # Generated demo artifact (separate prompt)
  prompts/                      # Source prompts, including this file
  vendor/reveal.js/             # Vendored Reveal.js (no network at present-time)
  README.md                     # Top-level overview
```

For this prompt, create the **lesson-deck** portion and any shared setup (such as the vendored `vendor/reveal.js/` folder) needed to run it locally.

The two decks share the vendored Reveal.js library via relative paths (`../vendor/reveal.js/...`).

Add or update the top-level README with basic commands for running the lesson deck locally.

---

## Technical requirements

Use Reveal.js.

Requirements:

- Create a working local development setup. The deck must run by opening `index.html` in a browser — no server required, no Wi-Fi required.
- Reveal.js should be vendored locally under `vendor/reveal.js/` and shared with the Pet Coach deck via relative paths.
- Optionally provide an `npm` script as a convenience (e.g., a static-server one-liner), but the primary runtime is plain static HTML.
- Keep the deck easy to edit.
- Use a clean, professional style appropriate for an internal enterprise technology audience.
- Use speaker notes for every horizontal slide.
- Include a clear visual distinction between teaching slides and demo transition slides.
- Include a working link to `../pet-coach-journey-deck/index.html` (open in a new tab) on the demo transition slide.
- Lean into Reveal.js features that demonstrate why the framework is interesting: fragments for incremental reveals, slide backgrounds and gradients for thematic moments, the zoom plugin for inspecting prototypes, the search plugin for live navigation, and code-highlight for showing prompt snippets.
- Prefer maintainable HTML, Markdown, CSS, and simple JavaScript.
- Avoid relying on external network assets unless absolutely necessary.

---

## Suggested visual style

Use a polished but restrained visual style:

- Dark or light professional theme is fine, but keep contrast strong.
- Use large headings and concise slide text.
- Use card layouts for comparison slides.
- Use simple diagrams made with HTML/CSS or Mermaid where helpful.
- Avoid dense paragraphs.
- Use consistent labels for:
  - Lesson concept
  - Demo artifact
  - Main path
  - Optional depth
  - AI coding agent workflow

### Sizing rules for dense layouts (important)

A 1280×800 Reveal.js slide does **not** scroll. If the content overflows vertically, the bottom is clipped and the audience can't see it. Any layout with many small elements needs deliberate sizing:

- **Card grids with 6+ cards** must use an explicit column count, not `auto-fit` with a generous `minmax`. For 8 cards, use a 4×2 grid; for 9-10 cards, a 5×2 grid. Don't let the grid choose how many columns to use.
- **Card titles must fit on one (preferably) or two lines.** Three-line wrapping inflates card height and is the most common cause of overflow. Pair a smaller card-title font (≈0.6–0.75em of slide base) with `line-height: 1.15-1.2`.
- **On dense slides, shrink the h2 a step** (e.g., 1.4em instead of 1.7em) to free vertical room for the cards.
- **Verify the slide visually after generation.** If a card grid would generate 6+ cards, mentally compute: do all cards fit on the 800px-tall stage with the chosen padding? If not, switch to an explicit grid and reduce typography until they do.
- **Walk every slide once after the deck is built.** Anything clipped at the bottom edge — even something subtle like a closing paragraph below a list — is a bug, not a styling preference. Tighten or shrink until the bottom of the slide has visible breathing room.

Provide CSS modifier classes (e.g., `.card-grid.cols-4`, `.card-grid.cols-5`, `.card-grid.compact`, `.dense-cards`) so dense slides can opt in without affecting other slides.

### CSS specificity gotcha for custom list components

When you style a `<ul>` with a custom class — for example a `.takeaway-list` whose `<li>`s render as styled cards — the default Reveal.js rule `.reveal ul` (selector `.reveal ul`, specificity 0,1,1) beats your single-class selector (specificity 0,1,0). The native disc bullet markers will leak through and a left margin will offset every list item, so the audience sees both bullets *and* your custom card styling.

Always declare `list-style: none !important;`, `margin-left: 0 !important;`, and `padding-left: 0 !important;` on any custom-styled list class. This is one of the most common visual bugs when authoring Reveal.js content.

---

## Lesson deck outline

Create the following deck.

### Slide 1: Title

Title:

**Presentations as Code**

Subtitle:

**Using Claude Code + Reveal.js to Build Adaptive Product Walkthroughs**

Include a brief line:

> Promptly-at-9 AI class

Speaker note:
Explain that this session is about using AI coding agents to create presentation artifacts that go beyond linear slides.

---

### Slide 2: The problem with linear decks

Main idea:

Traditional slide decks are useful, but they force a mostly fixed path.

Bullets:

- Great for a planned story
- Awkward when the audience wants selective depth
- Complex topics often become either too shallow or too long
- Backup detail gets buried or skipped

Speaker note:
Use this to set up the problem: many product and technical conversations need both a simple main path and optional detail.

---

### Slide 3: Why this matters now

Main idea:

AI coding agents lower the barrier to technical frameworks.

Bullets:

- Reveal.js has existed for years
- Many people avoided it because it required web development comfort
- Claude Code can scaffold, revise, refactor, and maintain the deck
- Non-specialists can now use more powerful tools by describing the artifact they need

Include this quote visually:

> Coding agents expand the scope of tools people can use in their everyday work.

Speaker note:
Make clear that the value is not “non-technical users become developers overnight.” The value is that software-shaped tools become more approachable.

---

### Slide 4: What Reveal.js adds

Main idea:

Reveal.js turns presentations into web-native, navigable artifacts.

Include cards for:

- Horizontal main path
- Vertical deep dives
- Speaker notes
- Markdown authoring
- Diagrams and code
- UI prototypes
- Static publishing
- Version control

Speaker note:
Briefly explain the horizontal/vertical navigation model. Left-to-right is the main flow; down is optional detail.

---

### Slide 4b: Diagrams as code — live Mermaid demo

This slide is aimed at the developer subset of the audience and demonstrates that Reveal.js can render diagrams from text-based DSLs (Mermaid, PlantUML, D2) live inside the slide.

Title:

**Diagrams as code, rendered live in the slide.**

Layout:

Two side-by-side panels, fixed height (~470px), both with rounded headers and bodies.

- **Left panel** ("Mermaid source · chat-to-case.mmd"): a vertically- and horizontally-scrollable `<pre><code>` block containing readable Mermaid source. Dark background, monospace font, small line-height. The source should be the Pet Coach chat-to-case handoff so it ties back to the existing architecture content.
- **Right panel** ("Rendered SVG · mermaid.js"): a `<pre class="mermaid">` containing the same Mermaid source, rendered live by the Mermaid library as an inline SVG.

Beneath the two panels, a one-line caption explaining the demo and naming sibling tools (Mermaid, PlantUML, D2).

Technical wiring:

- Vendor Mermaid locally at `vendor/mermaid/mermaid.min.js` (≈3.3MB from `npm pack mermaid@10`). Do not load from a CDN.
- Initialize Mermaid with `startOnLoad: false`, a theme matching the deck palette, and `securityLevel: 'loose'`.
- Render after Reveal's `ready` event by calling `mermaid.run({ querySelector: '.mermaid' })`. Mermaid sets `data-processed="true"` on each rendered element, so re-runs are idempotent.

Speaker note:
For a developer audience this is the "ah-ha" beat. Talk through what Mermaid is — a small DSL for diagrams — and why developers like it: diagrams diff cleanly in git, they update with the system, and there's no separate drawing tool to keep in sync. Mention PlantUML, D2, and Structurizr as siblings. Point at https://mermaid.live as a playground.

---

### Slide 5: The key pattern

Title:

**Main journey across. Optional detail downward.**

Show a simple diagram:

```text
Intro → Step 1 → Step 2 → Step 3 → Takeaways
          ↓        ↓
       Detail   Detail
          ↓        ↓
       Example  Prototype
```

Explain:

- Horizontal slides provide the quick path.
- Vertical stacks provide optional depth.
- Presenter can adapt to time, audience, or questions.

Speaker note:
This is the most important mental model. Make the diagram visually clear.

---

### Slide 6: Not better than PowerPoint — different

Main idea:

This is a tool-fit decision.

Create two comparison columns.

Column 1:

**PowerPoint / Claude Cowork / Claude Design**

Best for:

- Polished linear decks
- Executive-ready visuals
- Familiar editing and review
- Business handoff
- Fast first draft

Column 2:

**Reveal.js + Claude Code**

Best for:

- Adaptive talks
- Product journey walkthroughs
- Optional deep dives
- Embedded prototypes
- Architecture and data diagrams
- Source control and web publishing

Speaker note:
Keep this objective. Reveal.js is not a universal replacement.

---

### Slide 7: The workflow

Title:

**From idea to navigable artifact**

Show a pipeline:

```text
Journey outline
  → Claude Code scaffold
  → Reveal.js deck
  → Vertical deep dives
  → UI prototype slides
  → Architecture/data detail
  → Publish or share
```

Speaker note:
Explain that the deck evolves like a small software project.

---

### Slide 8: The demo scenario

Title:

**Demo: Pet Coach user journey**

Explain:

Pet Coach is an AI-assisted app that helps pet owners:

- Triage pet health concerns
- Determine whether a clinic visit is recommended
- Schedule a visit
- Preserve pre-visit context for clinic staff
- Ask follow-up questions after the visit about diagnostics, prescriptions, and care instructions

Speaker note:
Explain that the demo deck is a separate generated artifact, similar to an app demo.

---

### Slide 9: What the demo deck will show

Title:

**The demo deck is the artifact**

Bullets:

- Horizontal slides show the quick user journey
- Vertical slides show optional depth
- Selected vertical slides include UI mockups
- Technical deep dives can show data, architecture, and safety boundaries
- The same artifact can support product, UX, architecture, and leadership conversations

Speaker note:
Emphasize that the Pet Coach deck is not just a presentation; it is a navigable product model.

---

### Slide 10: Launch demo

Title:

**Switching to the Pet Coach journey deck**

Include text:

> Now we switch from the lesson deck to the generated artifact.

Include a clear, working button/link:

**Open Pet Coach Journey Demo**

The link must point to:

```text
../pet-coach-journey-deck/index.html
```

and open in a new tab (`target="_blank"`) so the presenter can return to the lesson deck for the after-demo reflection.

Speaker note:
Tell the audience to think of the Pet Coach deck as they would an app demo.

---

### Slide 11: After-demo reflection

Title:

**What changed?**

Bullets:

- The deck became navigable, not just linear
- Detail was available without disrupting the main story
- UI mockups could live beside journey steps
- Architecture and data concerns could be attached where they matter
- The artifact could be versioned, revised, and reused

Speaker note:
Use this after returning from the demo.

---

### Slide 12: Prompting lessons

Title:

**What to tell the coding agent**

Bullets:

- Define the audience and purpose
- Specify horizontal vs vertical structure
- Provide the journey outline
- Identify which steps need deep dives
- Ask for speaker notes
- Ask for reusable styling
- Add UI prototype and architecture requirements in stages

Speaker note:
Point out that the quality of the generated artifact depends heavily on structural prompting.

---

### Slide 13: Risks and limits

Title:

**Where this can go wrong**

Bullets:

- Too much hierarchy can become a maze
- Generated UI may look plausible but not be validated
- Technical setup may still need a knowledgeable reviewer
- Brand and accessibility need deliberate review
- PowerPoint may still be better for formal executive decks

Speaker note:
Keep this balanced and credible.

---

### Slide 14: Takeaways

Title:

**Takeaways**

Bullets:

- AI coding agents can make technical frameworks accessible to more people
- Reveal.js is useful when a deck needs optional depth
- Product journeys are a natural fit for 2D presentation structure
- The artifact can connect story, UI, data, and architecture
- This pattern applies beyond Reveal.js

Speaker note:
End with the broader pattern: AI lets people create structured artifacts that previously required specialized implementation skills.

---

## Additional required content

Add a slide or appendix that shows the recommended two-deck structure:

```text
lesson-deck/
  Teaches the technique

pet-coach-journey-deck/
  Demonstrates the generated artifact

prompts/
  Stores the prompts used to generate and revise both decks
```

Also add a short speaker note explaining why the two-deck approach was chosen:

- The lesson deck explains the concept.
- The Pet Coach deck is treated like an app demo.
- Keeping them separate makes it clear what was generated as the example artifact.

---

## Success criteria

The deck is successful if:

- It clearly explains why Reveal.js plus Claude Code is interesting.
- It avoids claiming that Reveal.js replaces PowerPoint.
- It makes the “presentations as code” idea concrete.
- It prepares the audience to understand the Pet Coach demo deck.
- It can be run locally.
- It has a clean visual style.
- It includes speaker notes.
- It includes a demo transition slide with a link placeholder.

---

## Implementation instructions

Please implement the project, not just describe it.

After implementation:

1. Provide the commands to install dependencies and run the lesson deck locally.
2. Summarize the files created.
3. Note any assumptions made.
4. Suggest how to wire the demo link once the Pet Coach journey deck exists.

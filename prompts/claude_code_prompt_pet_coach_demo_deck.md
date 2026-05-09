# Claude Code Prompt: Build the Pet Coach Reveal.js User Journey Demo Deck

## Purpose

Create a Reveal.js-based demo deck for an internal Promptly-at-9 AI class.

This deck is the **generated artifact** used in the class. It should demonstrate how Claude Code and Reveal.js can turn a product journey into a navigable, adaptive, two-dimensional presentation.

The deck should not feel like a normal linear slide deck. It should feel like a structured product walkthrough:

- Horizontal slides represent the quick top-level user journey.
- Vertical slides under selected journey steps provide optional detail.
- Some vertical slides include lightweight UI prototypes.
- Some vertical slides include architecture, data, workflow, or safety considerations.

This demo deck will be launched from a separate lesson deck.

---

## Core concept to demonstrate

The class should be able to see this pattern clearly:

```text
Horizontal navigation = main product journey
Vertical navigation = optional detail under a journey step
```

The presenter should be able to move left-to-right through the quick path, or move downward from selected parent slides to explore details.

The deck should make this navigation pattern visually obvious.

---

## Product scenario

Use this fictional product:

**Pet Coach**

Pet Coach is an AI-assisted application that helps pet owners:

- Triage concerns about a sick pet
- Determine whether a clinic visit is recommended
- Schedule a clinic visit when needed
- Save the pre-visit AI chat transcript and/or summary for clinic staff
- Support clinic staff review of the pre-visit context
- Help the pet owner understand care instructions, diagnostic results, prescriptions, and next steps after the visit

The domain should be handled responsibly. The AI assistant should be framed as a support tool, not as a substitute for veterinary care. Use safe language around medical topics.

---

## Technical requirements

Use Reveal.js.

Requirements:

- Create the deck inside `revealjs-pet-coach-demo/pet-coach-journey-deck/` as a sibling of `lesson-deck/`. Both decks share the vendored Reveal.js library at `../vendor/reveal.js/...`.
- The deck must run by opening `index.html` in a browser — no server, no Wi-Fi.
- Optionally provide an `npm` script as a convenience.
- Keep files organized and easy to edit.
- Use speaker notes for every main journey slide.
- Add clear visual cues on parent slides that have vertical deep-dive slides (a "↓ Optional deep dive" badge in a corner).
- Include a journey map near the beginning, with three phases (Before / During / After).
- Include lightweight UI prototype slides using HTML/CSS — phone frames, chat bubbles, scheduling cards, staff review panel.
- Include architecture/data slides using simple HTML/CSS flow diagrams, timelines, and a RAG-style context-assembly diagram. Avoid external Mermaid CDN; if Mermaid is desired, vendor it locally.
- Lean into Reveal.js features that make the demo richer: fragments for incremental reveals, slide backgrounds and gradients on phase boundaries, the zoom plugin (Alt+Click) so the presenter can zoom into prototype screens live, the search plugin for "press / to find a slide," and slide hash links for deep linking to specific verticals.
- Do not rely on external network assets.
- Keep the deck visually polished but maintainable.
- Avoid building a full application. The prototypes should be illustrative screens embedded in the deck.

---

## Desired folder structure

Place this deck at `pet-coach-journey-deck/` inside the existing `revealjs-pet-coach-demo/` repository. Reveal.js itself is vendored once at the repo root and shared by both decks:

```text
revealjs-pet-coach-demo/
  lesson-deck/
  pet-coach-journey-deck/
    index.html
    css/pet-coach.css
    README.md
  prompts/
  vendor/reveal.js/             # shared, vendored Reveal.js library
  README.md
```

A simple `index.html` + `css/` layout is preferred. Avoid build tools unless they earn their place.

---

## Visual style

Create a clean, modern, product-oriented visual design.

Suggested design language:

- Calm, professional, healthcare-adjacent feel
- Clear phase labels: Before visit, During visit, After visit
- Cards for journey steps
- Badges for optional detail, UX, data, safety, architecture
- Embedded UI mockups that look like app screens
- Strong readability on a projector or video call

Do not use overly playful styling. The Pet Coach example can be approachable, but this is for a professional internal AI class.

---

## Deck structure

Create the following horizontal main path.

### Horizontal slide path

1. Title
2. How to navigate this deck
3. Journey map overview
4. Pet owner starts AI triage in Pet Coach
5. Pet Coach captures symptoms and recommends next action
6. Pet Coach saves a pre-visit summary for the clinic
7. Pet owner schedules a clinic visit
8. Pet owner and pet arrive and check in
9. Clinic staff reviews the AI pre-visit summary
10. Veterinarian examines pet and orders diagnostics if needed
11. Diagnostic results are produced or returned
12. Veterinarian prescribes medication if needed
13. Pet owner returns home with care instructions
14. Pet owner later asks Pet Coach follow-up questions
15. Presenter paths
16. Takeaways

The top-level horizontal flow should be understandable in about 5-7 minutes if the presenter does not descend into vertical stacks.

---

## Required vertical stacks

Create vertical child slides under the following horizontal parent slides.

### Parent slide 4: Pet owner starts AI triage in Pet Coach

Vertical slides:

1. Example pet owner chat
2. Information captured
3. Safety boundaries and escalation
4. UX prototype: triage chat screen

Details:

- Show the pet owner describing symptoms such as low energy, decreased appetite, vomiting, coughing, limping, or medication questions.
- Keep examples safe and non-alarming.
- Show the AI asking clarifying questions.
- Include a safety note that urgent symptoms should prompt contacting a clinic or emergency veterinary care.

---

### Parent slide 5: Pet Coach captures symptoms and recommends next action

Vertical slides:

1. Possible next actions
2. Confidence and uncertainty handling
3. Clinical guardrails

Details:

Possible outcomes might include:

- Monitor at home with care guidance
- Schedule a routine appointment
- Schedule a same-day visit
- Contact emergency veterinary care

Make clear that the AI should not overstate certainty.

---

### Parent slide 6: Pet Coach saves a pre-visit summary for the clinic

Vertical slides:

1. Transcript vs structured summary
2. Data captured for clinic team
3. Privacy, audit, and review considerations
4. Architecture: chat-to-case handoff

Details:

Include a distinction between:

- Raw transcript
- AI-generated structured summary
- Confirmed staff notes
- Pet owner-reported symptoms

The architecture slide should show something like:

```text
Pet Owner Chat
  → AI Triage Service
  → Summary Generator
  → Clinic Case / Visit Context
  → Staff Review UI
```

Use Mermaid if practical.

---

### Parent slide 7: Pet owner schedules a clinic visit

Vertical slides:

1. Appointment type selection
2. Availability and urgency matching
3. Confirmation and reminders
4. UX prototype: scheduling screen

Details:

Show the system recommending an appointment type based on triage.

Example appointment types:

- Wellness concern
- Sick visit
- Same-day urgent visit
- Follow-up visit

The prototype should show a few available time slots and a confirmation action.

---

### Parent slide 9: Clinic staff reviews the AI pre-visit summary

Vertical slides:

1. Staff-facing pre-visit summary
2. What staff should confirm
3. Risks of relying on an AI summary
4. UX prototype: staff review screen

Details:

The staff review screen should show:

- Pet name
- Owner name
- Reported symptoms
- Duration
- AI summary
- Questions to confirm
- Flag for urgent concern if applicable
- Button or area for staff-confirmed notes

Emphasize that clinic staff should review and confirm, not blindly accept the AI summary.

---

### Parent slide 10: Veterinarian examines pet and orders diagnostics if needed

Vertical slides:

1. In-house diagnostics path
2. Reference lab path
3. Decision points and branching logic
4. Workflow view: diagnostics order to result

Details:

Show both paths:

- In-house diagnostics may produce results during the visit.
- Reference lab results may return after the visit.

Keep the presentation product-focused, not medically detailed.

---

### Parent slide 11: Diagnostic results are produced or returned

Vertical slides:

1. In-house results during visit
2. Reference lab results after visit
3. Data flow: diagnostics to Pet Coach
4. Safety boundary: explanation, not diagnosis

Details:

Show how results may later be used as context for Pet Coach follow-up questions.

Include the idea that Pet Coach can explain owner-facing care instructions and result summaries when those are available, but should escalate clinical concerns to the clinic.

---

### Parent slide 14: Pet owner later asks Pet Coach follow-up questions

Vertical slides:

1. Lab result explanation question
2. Missed dose question
3. Symptom monitoring question
4. When to call the clinic
5. UX prototype: follow-up question screen
6. RAG-style context assembly

Details:

Use examples such as:

- “What do these lab results mean?”
- “What should I do if I missed a dose?”
- “Is this side effect expected?”
- “When should I call the clinic?”

The AI responses should be careful and should encourage contacting the clinic for uncertainty, worsening symptoms, or urgent concerns.

The RAG-style context assembly slide should show:

```text
Pet owner question
  + care instructions
  + medication instructions
  + diagnostic result summary
  + clinic guidance
  + safety rules
  → Pet Coach response
```

---

## Journey map slide

Add a visually clear journey map near the beginning.

It should show three phases:

```text
Before the visit
During the clinic visit
After the visit
```

Map the top-level journey into those phases.

Suggested mapping:

### Before the visit

- AI triage starts
- Symptoms captured
- Next action recommended
- Pre-visit summary saved
- Appointment scheduled

### During the clinic visit

- Check-in
- Staff review
- Vet exam
- Diagnostics
- Medication and care plan

### After the visit

- Return home
- Care instructions
- Diagnostic results
- Prescription clarification
- Follow-up questions

---

## UI prototype slides

Create lightweight but polished UI mockups directly inside the Reveal.js deck using HTML and CSS.

Create prototype slides for:

### Triage chat screen

Should show:

- Pet owner asking about symptoms
- AI asking clarifying questions
- A visible safety/escalation hint
- A simple chat interface

### Appointment scheduling screen

Should show:

- Recommended visit type
- Urgency level
- Available time slots
- Confirmation action

### Staff review screen

Should show:

- AI-generated pre-visit summary
- Captured symptoms
- Questions for staff to confirm
- Place for staff-confirmed notes

### Follow-up question screen

Should show:

- Pet owner asking about a missed medication dose or diagnostic result
- AI response with cautious, owner-friendly explanation
- Recommendation to contact the clinic when appropriate

Use reusable CSS classes for:

- phone/app panels
- chat bubbles
- cards
- buttons
- status badges
- timeline items
- staff review panels

---

## Architecture and data deep dives

Add optional technical deep-dive slides where appropriate.

Include:

### Under pre-visit summary

- Data captured from chat
- Raw transcript vs structured summary
- Suggested data model for pre-visit summary
- Architecture diagram showing Pet Coach chat to clinic case handoff

### Under diagnostic results

- In-house diagnostic result flow
- Reference lab result flow
- How results become available for Pet Coach follow-up
- Boundary between explaining existing clinical information and generating new medical conclusions

### Under at-home follow-up

- Retrieval of care instructions, medication data, and diagnostic results
- RAG-style context assembly
- Escalation rules for contacting the clinic

---

## Presenter paths slide

Add a horizontal slide titled:

**Presenter paths**

Describe three ways this same deck can be presented:

### Executive path

- Stay mostly horizontal
- Focus on value, experience, and workflow continuity

### Product / UX path

- Dive into user journey details and UI prototype slides

### Architecture path

- Dive into data handoffs, diagnostics flow, RAG context, and safety boundaries

The slide should reinforce this lesson:

> A Reveal.js deck can act as an adaptive presentation where the same artifact supports different audiences.

---

## Navigation cues

Add visual hints to help users understand when a slide has vertical detail.

Examples:

- “Press ↓ for details”
- “Optional deep dive below”
- Small downward arrow badge
- Label such as “UX deep dive,” “Data deep dive,” or “Architecture deep dive”

Also include a “How to navigate” slide near the beginning explaining:

- Right arrow = continue main journey
- Down arrow = explore detail
- Up arrow = return to parent
- Esc = overview mode

---

## Speaker notes

Add speaker notes for all horizontal slides.

The notes should:

- Explain what the presenter should emphasize
- Mention when optional deep dives are available
- Avoid overexplaining every bullet
- Help connect the demo back to the Promptly-at-9 teaching point

---

## Responsible AI / safety language

Because the scenario involves pet health, use careful language.

The deck should make clear:

- Pet Coach supports triage and follow-up education.
- Pet Coach does not replace veterinarians or clinic staff.
- Urgent or worsening symptoms should be escalated.
- AI-generated summaries should be reviewed by clinic staff.
- Medication and diagnostic explanations should rely on clinic-approved information when available.

---

## Success criteria

The deck is successful if:

- The horizontal flow tells the Pet Coach journey clearly.
- Vertical stacks provide meaningful optional depth.
- The navigation model is obvious.
- UI prototype slides look polished enough to be credible.
- Architecture/data slides are understandable without being too dense.
- The artifact demonstrates why Reveal.js is useful for adaptive product walkthroughs.
- The deck can be run locally.
- The source is organized and easy to modify.
- Speaker notes are included.
- The deck feels like a product exploration artifact, not just a standard slide deck.

---

## Implementation instructions

Please implement the deck, not just describe it.

After implementation:

1. Provide commands to install dependencies and run the deck locally.
2. Summarize the files created.
3. Point out where the horizontal and vertical slide structure is defined.
4. Explain how to add another vertical deep-dive stack under a journey step.
5. Note any assumptions made.

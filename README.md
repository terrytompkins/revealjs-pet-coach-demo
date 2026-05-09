# Promptly-at-9 Reveal.js Prompt Pack

This prompt pack contains Claude Code prompts for creating two Reveal.js decks for a Promptly-at-9 AI class.

## Session concept

**Presentations as Code: Using Claude Code + Reveal.js to Build Adaptive Product Walkthroughs**

The class uses a two-deck structure:

1. **Lesson deck**  
   Explains the technique, why Reveal.js matters, how AI coding agents expand the set of tools people can use, and when this approach is better or worse than linear slide tools.

2. **Pet Coach user journey demo deck**  
   A generated Reveal.js artifact that models a product journey. Horizontal slides show the quick path; vertical slides provide optional deep dives into UX, data, architecture, safety, and prototype UI screens.

## Files

- `claude_code_prompt_lesson_deck.md`  
  Prompt for Claude Code to create the Promptly-at-9 lesson deck.

- `claude_code_prompt_pet_coach_demo_deck.md`  
  Prompt for Claude Code to create the Pet Coach Reveal.js user journey demo deck.

## Recommended workflow

1. Create a new empty working folder.
2. Run Claude Code with `claude_code_prompt_lesson_deck.md`.
3. Confirm the lesson deck runs locally.
4. Run Claude Code with `claude_code_prompt_pet_coach_demo_deck.md`.
5. Confirm the Pet Coach demo deck runs locally.
6. Wire the lesson deck's "Open Pet Coach Journey Demo" link to the local or hosted demo deck URL.
7. Use the Pet Coach prompt as a class handout so participants can try generating their own version.

## Suggested final folder layout

```text
promptly-revealjs-session/
  lesson-deck/
  pet-coach-journey-deck/
  prompts/
    claude_code_prompt_lesson_deck.md
    claude_code_prompt_pet_coach_demo_deck.md
  README.md
```

## Optional additional artifacts to produce later

These are not strictly required, but may be useful:

- A short "participant handout" explaining the Reveal.js navigation model.
- A condensed version of the Pet Coach prompt for live demonstration.
- A follow-up prompt that asks Claude Code to improve visual polish after the first deck is generated.
- A follow-up prompt that asks Claude Code to publish both decks to GitHub Pages, Vercel, Netlify, or S3.
- A slide or README section comparing Claude Cowork, Claude Design, Claude Code, PowerPoint, and Reveal.js.

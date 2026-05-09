# Optional Claude Code Follow-up Prompt: Polish and Package Both Reveal.js Decks

Use this after Claude Code has generated both the lesson deck and the Pet Coach demo deck.

## Goal

Review, polish, and package the two-deck Promptly-at-9 Reveal.js session.

The repository should contain:

```text
promptly-revealjs-session/
  lesson-deck/
  pet-coach-journey-deck/
  prompts/
  README.md
```

## Tasks

1. Confirm both decks run locally.
2. Ensure the lesson deck includes a working link to the Pet Coach demo deck.
3. Ensure both decks have consistent but distinguishable styling.
4. Add README instructions for running each deck.
5. Add a brief explanation of the two-deck strategy:
   - Lesson deck = teaches the technique.
   - Pet Coach deck = generated product journey artifact.
6. Confirm the Pet Coach deck has:
   - horizontal main journey slides
   - vertical deep dives
   - UI prototype slides
   - architecture/data slides
   - speaker notes
   - navigation help
7. Add a `/prompts` folder containing the prompts used to generate the decks.
8. Add a short "How to adapt this for your own product journey" section to the README.

## Do not

- Do not merge the two decks into one deck.
- Do not remove speaker notes.
- Do not replace the Pet Coach demo with generic content.
- Do not add unnecessary frameworks unless already needed.

## Final response

After making changes, provide:

1. Install/run commands.
2. Folder structure summary.
3. How to present the class using the two decks.
4. How someone could adapt the Pet Coach prompt to their own product journey.

# BSides Perth website: notes for Claude

Static site served by GitHub Pages from `main`. No build step: edit the HTML directly.

## Schedule page (`schedule.html`): standing rules

These are the default for every schedule change. Don't drop them when moving, adding or retitling talks.

1. **The published schedule is the source of truth.** Times, titles, speaker names and slot order on `schedule.html` win over the internal draft sheet and older emails, unless Alex says otherwise.

2. **Every talk expands to show its abstract, speaker bio and headshot.** Each talk is an
   `<li class="slot slot--talk" id="speaker-slug">` containing a `<details class="talk">`:
   - `<summary class="talk-summary">` holds the title (`h3.slot-title`), speaker (`p.slot-speaker`),
     topic (`p.slot-meta`) and the "Abstract and bio" toggle. Keep these exact classes.
   - `<div class="talk-detail">` holds `h4.talk-label` "Abstract", one `p.talk-abstract` per paragraph,
     then `h4.talk-label` "Speaker"/"Speakers" and one `div.speaker` per person
     (`img.speaker-photo` + `p.speaker-name` + `p.speaker-bio`).
   - No headshot yet: drop the `img` and add `speaker--nophoto` to the `div.speaker`.
   - No abstract yet: `<p class="talk-abstract talk-abstract--pending">Abstract coming soon.</p>`.
   - Two presenters: two `div.speaker` blocks, each with its own photo and bio.
   - A group photo (e.g. the PS Sides kids) goes in `img.talk-photo` after the abstract.
   Copy an existing talk block when adding a new one. Breaks (`slot--break`) and TBA slots (`slot--tba`) don't expand.

3. **Moving a talk = move the whole `<li>`**, details included. Never rebuild a slot as a plain title-only entry.

4. **Deep links:** the `id` on each talk `<li>` is its link (`schedule.html#matt-jones`). The script at the bottom opens that talk on load. Keep ids stable once published, since they get shared on socials.

5. **Headshots:** `assets/img/speakers/<speaker-slug>.jpg`, square, 480x480, JPEG. Originals live in the Drive folder 2026 Conference > Speakers > headshots. Don't guess which person is the speaker in a group photo: ask.

6. **Where details come from:** CFP form responses sheet (bio + description columns), otherwise the speaker's acceptance-email reply. Use the speaker's own words; only fix obvious typos, remove internal notes (e.g. timing breakdowns) and use curly quotes/apostrophes to match the page.

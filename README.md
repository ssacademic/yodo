# Yodo

*alpha 6*

An outline you can tick off.

Everything is a line. A line becomes a project the moment it gets parts — nobody declares
it. Step inside any line and it becomes the whole screen, with a breadcrumb to get back.

Two modes over one tree:

- **Map** — structure. Nest, reorder, edit, break things down.
- **Do** — everything dated or flagged, in order, check-off only. With a focus timer.

New users get a short introduction on first run — five cards, then three pointers at the
real buttons. It can be replayed any time from **⚙ → Show the introduction again**.

---

## Put it online in about two minutes

```bash
git init
git add .
git commit -m "Yodo alpha 1"
git branch -M main
git remote add origin https://github.com/<you>/yodo.git
git push -u origin main
```

Then on GitHub: **Settings → Pages → Source: Deploy from a branch → main → / (root) → Save.**

It appears at `https://<you>.github.io/yodo/` within a minute or two. Send that link to
anyone; on a phone they can use **Add to Home Screen** and it behaves like an app —
full screen, its own icon, works with no signal.

## What's in here

These six files **are** the whole thing. There is nothing to compile and nothing to install.
Drop them in a repo, turn on Pages, done.

```
index.html              the entire app — one file, no build step, no dependencies
manifest.webmanifest    name, icons and colours, so "Add to Home Screen" works
sw.js                   service worker: caches the shell so it opens with no signal
icon-192.png            placeholder icon, drawn from the progress ring
icon-512.png            the same, larger
README.md               this
```

It opens **empty**. First thing anyone sees is one line of prose and a single faint bullet.
No sample tasks, no folders, no worlds — the structure is whatever they type.

## Things worth telling testers

- **It saves to their own browser and nowhere else.** No account, no server, no tracking.
  Clearing site data wipes it. There is no sync between devices yet.
- **Enter** makes a new line, **Tab** tucks it under the one above, **Shift-Tab** pulls it
  back out, **Backspace** on an empty line removes it. On a phone, the four arrows in the
  **move** row of a line's controls do the same thing.
- Tap a line once to open its controls; tap again to type. The keyboard only appears when
  you actually mean to write something.
- Tap the **dot on the right** of any line to step inside it. That is how a to-do turns
  into a project.
- Marking something **urgent**, **important** or giving it a **day** is what makes it show
  up in Do. Do puts **one** thing at the top and says why it chose it.
- The **cue** on a line — *where will you be when you do this?* — is not decoration. A task
  that knows its moment gets done roughly twice as often as one that only knows what it is.

## Questions worth asking them

1. Did you understand, without being told, that tapping the right-hand dot goes *inside*?
2. After a week, is Map still readable, or has it turned into a wall?
3. Does Do contain the right things, or is it full of noise / nearly empty?
4. Did you ever lose something you had typed?
5. Did you use the cue field? Did anything change when you did?

## Deploying again later

Bump `CACHE` in `sw.js` (e.g. `yodo-a2`) whenever you change `index.html`, or returning
testers will keep seeing the old build from their cache.

## Cues

**⚙ → Cues** has two settings. *Only when I want to* is the default. *Ask me every time*
puts the cursor in the cue field whenever a line gets a day or a mark — it asks, it never
blocks. A task you cannot write down is worse than one with no cue.

## Getting your list out

**⚙ → Your list** has: back up as `.json`, export as plain text, copy the outline to the
clipboard, **print / save as PDF** (the browser's print dialog does the PDF part), and
restore a backup. Worth telling testers, since nothing syncs.

## On notifications, and whether this needs to be a "real" app

Honest position: **a static site cannot reliably remind you of anything.**

Web push needs a server to send the push — the whole point is that it reaches you when the
page is shut. There is a browser API for locally scheduled notifications
(`showTrigger`) but it is not shipped in any current browser. So a page hosted on GitHub
Pages, with no backend, can only notify you while it happens to be open. That is not a
reminder; it is a nudge you were already looking at.

What is genuinely available now, and is in here: **long-press the home-screen icon** and
Android offers *Do — one thing* and *New line*, which jump straight in. Manifest shortcuts,
not widgets.

Android **home-screen widgets are not available to web apps** at all. There is a Widgets
spec, but nothing implements it for installed PWAs.

So: if reminders turn out to be the thing that makes this work, that is the moment it needs
either a small server or a native shell — and not before. Until then the honest answer is
that Yodo remembers for you, it does not interrupt you.

## Known gaps

- No sync, no accounts, no export yet.
- Repeats show a day but do not yet generate the next occurrence.
- Swipe-to-indent on touch is not built; Tab is a desktop-only gesture.
- Swipe-to-indent on touch (the arrows in the controls cover it for now).
- No calendar view; dates are set from a picker, not a month grid.
- No reminders or notifications — see the section above for why.
- No sync between devices. Back up manually if it matters.

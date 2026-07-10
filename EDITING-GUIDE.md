# Editing the lab website — a guide for students

This guide covers the two things you'll do most often: **adding or editing a publication** and
**adding or editing a lab member profile**. You don't need to know Hugo or write code — you only
edit small text files (Markdown) and drop in images.

## Before you start

- **How to preview your changes locally.** In RStudio, open the project and run:

  ```r
  blogdown::serve_site()
  ```

  A live preview opens and refreshes automatically as you save. Always check your change here
  before committing.

- **Each item lives in its own folder.** A publication is a folder under `content/pub/`; a profile
  is a folder under `content/profiles/`. Inside each folder, the text of the page lives in a file called
  `index.md`, and any images sit in the same folder next to it.
  
- **The part between the two `---` lines at the top of `index.md` is the "front matter"** — a list
  of `field: value` settings. The part below the second `---` is the page body (the abstract, or
  the bio).

> ### ⭐ The numbering system (read this first)
>
> Both publications and profiles are ordered by a hidden `weight:` number in the front matter.
> **Visitors never see this number** — it only controls the order items appear in. The two
> sections sort in **opposite directions**, so pay attention to which one you're editing:
>
> | Section | Rule | To make a new item appear first |
> |---|---|---|
> | **Publications** (`content/pub/`) | **Higher number = shown first** (newest on top) | Give it a weight **one higher** than the current highest |
> | **Profiles** (`content/profiles/`) | **Lower number = shown first** (more senior on top) | Give it a **low** number to slot it near the top, or a higher one to place it further down |
>
> You never have to renumber everything. To insert an item, just pick a number that puts it where
> you want relative to its neighbors. I'd like to keep profiles organized as follows: the most senior graduate student comes first, 
> followed by all other graduate students in order of seniority, then by undergraduate students in order of seniority, and ending with 
> the lab alumni page.

---

## Editing the publications page

Publications appear on the **Publications** page, newest (highest `weight`) first, each with its
title, author list, venue, year, DOI/PDF buttons, and a collapsible abstract.

### ➕ Creating a NEW publication

1. **Make a new folder** under `content/pub/`. Give it a short, lowercase, dash-separated name —
   the convention here is `lastname-year-journal`, e.g. `content/pub/spake-24-ehb/`. 
2. **Create a file called `index.md`** inside that folder. The easiest way is to copy the
   `index.md` from an existing publication folder and change the values. Here is a template:

   ```yaml
   ---
   title: "Full title of the paper"
   author: "Spake L, Coauthor B, Coauthor C"   # full author list, in order
   date: '2026-05-01'                          # the year shown on the page comes from this
   publishDate: '2026-05-01'                   # used only as a tiebreaker when sorting
   weight: 16                                  # one higher than the current top paper
   publication: 'Journal Name'                 # the venue shown in bold
   summary: 'One-sentence plain-language summary of the finding.' # this is not currently shown to visitors
   featured: no
   links:
   - icon: doi
     icon_pack: ai
     name: DOI
     url: https://doi.org/10.xxxx/xxxxx        # your DOI link
   - icon: file-pdf
     icon_pack: fas
     name: PDF
     url: https://link-to-the-pdf              # optional; delete these 4 lines if no PDF
   format: hugo
   ---

   Paste the abstract here as plain text. The page shows the first couple of sentences and
   lets visitors click the down-caret (⌄) to expand the rest, so you don't need to shorten it.
   ```

3. **Set the `weight`.** Look at the publication currently at the top of the page, find its
   `weight`, and give your new paper **the next number up**. That's all it takes to make the new
   paper lead the list. (See the numbering box above.)
4. **Paste the abstract** below the second `---`. Plain text is fine — no heading, no image needed.
5. **Preview** with `blogdown::serve_site()` and confirm the paper appears at the top and the
   DOI/PDF buttons work.

### ✏️ Editing an EXISTING publication

1. **Find its folder** under `content/pub/` (named like `spake-24-ehb`) and open `index.md`.
2. **Change what you need:**
   - Fixing a typo in the **title, authors, journal, or abstract**? Edit that field (or the body
     text) directly.
   - Adding a **DOI or PDF link** that wasn't there before? Add or edit the entries under `links:`,
     matching the indentation shown in the template above.
   - Want to **move it up or down the list**? Change only its `weight` number (higher = higher up).
3. **Preview** to confirm the change looks right.

---

## Editing lab member profiles

Each profile is one folder under `content/profiles/`. Profiles are listed on the **About the Lab**
page (most senior first), and each has its own page with the person's photo and bio. At the bottom
of every profile there's an automatic "See another profile:" bar linking to the others — you don't
have to maintain that; it updates itself.

### ➕ Creating a NEW profile

1. **Make a new folder** under `content/profiles/`, named for the person in lowercase, e.g.
   `content/profiles/jordan/`.
2. **Add a photo** to that folder named `featured.jpeg` (or `featured.jpg`/`featured.png`). This is
   the thumbnail shown next to the person on the About the Lab page. You can also add a larger photo
   (any filename) to show inside the bio.
3. **Create `index.md`** inside the folder (copy an existing one and edit it). Template:

   ```yaml
   ---
   title: Jordan Smith                # the person's name
   subtitle: PhD Student              # their role, shown under the name
   excerpt: One line about them, shown on the About the Lab page.
   weight: 4                          # ⭐ lower = more senior/higher on the page (see box above)
   categories:
   - Lab Members
   author:
   draft: false
   featured: true
   layout: single
   ---

   ## About me

   Write the bio here. You can use normal Markdown — paragraphs, links, and lists all work.

   Add links like this:

     + [ResearchGate](https://www.researchgate.net/...)

   Show the larger photo like this (filename must match the file you added):

   ![](jordan-full.jpeg)
   ```

4. **Set the `weight`.** Profiles sort **lowest number first**, and lower means more senior. Pick a
   number that places the person in the order described in the numbering box above — graduate
   students (by seniority) first, then undergraduates (by seniority). For example, a new
   undergraduate goes below all the graduate students but above the Lab Alumni page. Keep the
   **Lab Alumni** page at the **highest** weight number so it always stays last.
5. **Preview** and confirm the person shows up in the right spot with their photo and bio.

### ✏️ Editing an EXISTING profile

1. **Find their folder** under `content/profiles/` and open `index.md`.
2. **Change what you need:**
   - Updating the **role, one-line blurb, or bio**? Edit `subtitle`, `excerpt`, or the body text.
   - **Replacing the photo?** Drop a new image in the folder. If you keep the name `featured.jpeg`
     it just works; if you use a new filename, update the `![](...)` line in the body to match.
   - **Changing seniority order** (e.g. someone got promoted)? Change only the `weight` number
     (lower moves them up).
3. **Preview** to confirm.

> **Removing / graduating a member:** there's a separate **Lab Alumni** profile
> (`content/profiles/alumni/`) for people who've moved on — move them there rather than deleting their
> folder, so their contribution is still credited.

---

## Committing your changes to update the live website

Once the preview looks right:

1. Save your files.
2. Commit and push (in RStudio's Git pane, or on the command line). The live site rebuilds
   automatically after the change reaches the site's repository. This can take a few minutes.

If anything looks off in the preview, don't commit — ask Laure. It's much easier to fix before it
goes live.

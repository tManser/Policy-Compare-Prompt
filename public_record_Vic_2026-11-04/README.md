# Public record: Victoria political party commitments

Collected 2026-11-04.
This folder was made on 21 November 2026.

## What this is

The website this record belongs to shows what each political party says it
will do, side by side, in plain and neutral words. It does this by reading
each party's own policy pages and using an AI (Anthropic's Claude models) to
pick out each commitment and describe it without the emotional or
persuasive language.

This folder exists so you don't have to take that on trust. It shows
**which pages were read**, **exactly what they said on the day they were
read**, and **the exact instructions the AI was given**. With it you can
take any commitment on the website, find the party's original words, and
judge for yourself whether the neutral description is fair.

## What's in this folder

| File or folder | What it is |
|---|---|
| `sources.csv` | Every web page and PDF used, one per line: which party, the address, whether it was read successfully, the date it was read, how many commitments came from it, and where its text is saved in `raw_text/`. Opens in any spreadsheet program. |
| `link_lists/` | For each party, the list of its web pages that was chosen to be read, exactly as used. These were picked by hand from each party's own website: its policy pages. |
| `pdfs/` | Any policy documents a party published as a PDF, exactly as used. |
| `raw_text/` | The text of every page, exactly as it was read, one folder per party. Websites change and pages disappear, so this is the lasting copy of what each party said at the time. The first line of each file is the page's address. Menus, footers and text hidden from human readers were left out when the page was read; nothing else was changed. |
| `prompts.md` | The instructions the AI was given at every step. A party's own words appear in square-bracket stand-ins such as `[THE PASSAGE ...]`, so you can see exactly how every party's text was handled, and that every party was handled the same way. |

## How to check a commitment yourself

1. On the website, note the commitment and the source link under it.
2. Find that address in `sources.csv`, then open the file it names in
   `raw_text/` and find the passage. (Or open the live page, but it may
   have changed since.)
3. Compare. The neutral description should state the same action, with the
   same strength, and every figure, name, date and listed item the party
   gave; it should leave out attacks on opponents and self-praise. Where
   the party gave a reason, it's stated as theirs: "The stated aim is to …".

## Parties included

| Party | Pages / documents listed | Read successfully | Not read | Commitments |
|---|---|---|---|---|
| Animal Justice Party | 78 | 0 | 78 | 625 |
| Australian Citizens Party | 1 | 0 | 1 | 83 |
| Australian Labor Party | 11 | 0 | 11 | 94 |
| Climate Action Now Party | 1 | 0 | 1 | 27 |
| Family First | 1 | 0 | 1 | 132 |
| Free Palestine | 1 | 0 | 1 | 17 |
| Legalise Cannabis | 1 | 0 | 1 | 3 |
| Liberal Party | 1 | 0 | 1 | 88 |
| Libertarian Party | 1 | 0 | 1 | 119 |
| National Party of Australia | 1 | 0 | 1 | 103 |
| One Nation | 11 | 0 | 11 | 245 |
| Sustainable Australia Party | 30 | 0 | 30 | 387 |
| The Greens | 34 | 0 | 34 | 1429 |
| The West Party | 6 | 0 | 6 | 36 |
| Victorian Socialists | 28 | 0 | 28 | 663 |
| **Total** | **206** | **0** | **206** | **4051** |

A page that was "not read" could not be downloaded at the time (for example
the page had been removed); see `sources.csv` for which.

## How it works, in short

Each party's pages go through the same steps with the same instructions
(the full text of each is in `prompts.md`):

1. **Segment** finds each commitment on a page and the party's exact words for it.
2. **Extract** writes a neutral description of each one.
3. **Evaluate** notes how it would be funded and how specific it is,
   quoting the party's words as evidence for every "yes".
4. **Audit** checks everything against the party's words. Before it does,
   code checks that every listed item and every figure appears in the
   source. Anything that fails is redone (**Rewrite**).
5. **Filing** groups commitments from all parties into shared issues, so
   they can be compared.

A person then checked possible cases of one party stating the same
commitment twice, and combined real double-ups into one (keeping both
source pages).

The AI models used for each step:

| Step | Model |
|---|---|
| Segment | `claude-opus-5-5` |
| Extract | `claude-sonnet-5-5` |
| Evaluate | `claude-haiku-5-5` |
| Audit | `claude-haiku-5-5` |
| Rewrite | `claude-opus-5-5` |
| Filing | `claude-sonnet-5-5` |

## What this record doesn't cover

- Only the pages listed in `link_lists/` and the PDFs in `pdfs/` were read:
  not media releases, speeches, social media, budget papers, or anything a
  party published after the collection date.
- Independent candidates are not included.
- "No commitment found" on the website means nothing was found on these
  pages, not that the party opposes the idea.
- The AI is careful but not perfect. If you find a description that doesn't
  match its source, please report it.

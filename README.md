# helenwilsonburns.com

```
index.html     content
styles.css     design layer
cv.pdf         served at helenwilsonburns.com/cv.pdf
images/        every photo on the site
CNAME          your domain — currently MISSING, see below
```

---

## The one rule

Four colours mean four research domains, everywhere on the site:

| Domain | Hex | Classes |
|---|---|---|
| migration | `#F2A93B` | `b-mig` `d-mig` `h-mig` |
| environment | `#10765C` | `b-env` `d-env` `h-env` |
| population health | `#D4356B` | `b-hea` `d-hea` `h-hea` |
| rurality | `#3457D5` | `b-rur` `d-rur` `h-rur` |

Don't use them for anything else. That restraint is what lets someone
read the research matrix at a glance. Publication status uses a separate
grey ramp (`--st1` to `--st5`) for exactly this reason.

## Add a project

Copy a whole `<li class="project">` block. It has two halves: `.pbody`
holds the writing, `.pcells` holds the four matrix columns.

```html
<li class="project">
  <div class="pbody">
    <h3>Project title</h3>
    <p class="role-line">What it is and what you did.</p>
    <p class="meta">Funder. <a href="https://...">Project link</a></p>
    <ul class="papers"> ... </ul>
  </div>
  <div class="pcells">
    <span class="cell on d-mig"><i>migration</i></span>
    <span class="cell d-env"><i>environment</i></span>
    <span class="cell on d-hea"><i>population health</i></span>
    <span class="cell d-rur"><i>rurality</i></span>
  </div>
</li>
```

**Keep all four `<span>`s, always in that order.** Add `on` for a domain
the project works in; leave it off otherwise. The empty columns are what
make the grid scannable — deleting them breaks the alignment down the page.

The `<i>` text is hidden on desktop. On phones the matrix collapses and
those become the coloured chips above each title, so keep the words correct.

## Add a paper

Inside a project's `<ul class="papers">`, copy one `<li class="paper">`.
The status class sets both the label colour and its square:

| Class | Shows as |
|---|---|
| `s-prog` | In progress |
| `s-near` | Near submission |
| `s-rev` | Under review |
| `s-cond` | Conditionally accepted |
| `s-pub` | Published |

Authors, venue, and DOI stack with `<br>` inside one `<p class="a">`:

```html
<p class="a">Wilson Burns, Donato, and Carrico<br>
<em>Demography</em><br>
<a href="https://doi.org/...">doi:10.xxxx/xxxxx</a></p>
```

## Paper-level domains

Each paper also carries its own small chips, right under the title, because a
paper doesn't always cover everything its project does:

```html
<p class="t">Paper title</p>
<p class="pdoms"><span class="d-mig">migration</span><span class="d-rur">rurality</span></p>
<p class="a">Authors ...</p>
```

Unlike the project columns, here you only list the domains that apply — there
are no empty placeholders. Keep them in the order migration, environment,
population health, rurality so they read consistently down the page. A paper
can have one chip, or none at all (the "Dataset in preparation" row has none,
since it isn't a paper).

## Add courses taught or talks

There's a commented-out `<ul class="listing">` block in the Teaching
section. Uncomment it and edit — `<span class="when">` is the right-hand
date column, `<span class="sub">` is the smaller second line.

## Swap a photo

Easiest: give the new photo the **same filename** and overwrite it in
`images/`. Nothing else changes.

Otherwise upload under a new name and update both the `src` and the `alt`
in `index.html` — `alt` is what a screen reader announces and what shows
if the image fails to load. Resize to about 1400px wide first; phone
photos are 4000px+ and will make the page slow.

## Update your CV

Upload the new PDF over `cv.pdf` in the root, keeping that filename.

## CNAME

`CNAME` was deleted in commit `9d15ac7`, which is why
**helenwilsonburns.com still serves the old Google Site** while this one
lives at helenwilsonburns.github.io/hwb_site. To point the domain here,
add a file named `CNAME` (no extension) in the repo root containing one
line:

```
helenwilsonburns.com
```

Then check Settings → Pages that the custom domain is set and DNS is
verified.

## Fonts

Newsreader (display) and Inter Tight (text), loaded from Google Fonts in
the `<head>`. Changing either means changing `--display` / `--text` at the
top of `styles.css` and the font link in `index.html`.

# helenwilsonburns.com


```
index.html     copy
styles.css     design layer
cv.pdf         served at helenwilsonburns.com/cv.pdf
CNAME          your domain; don't delete this file
images/        every photo on the site
```

---

### Swap a photo

Easiest way: give the new photo the **same filename** as the one you're replacing, then
upload it into `images/` and let it overwrite. Nothing else changes.

Otherwise, upload it under a new name and update the filename in `index.html`:

```html
<img src="images/field-river.jpg" alt="A village along a wide river">
```

Change the caption on the line below it, and update the `alt` text too — that's what a
screen reader announces and what shows if the image fails to load.

Resize photos to about 1400px wide before uploading. Phone photos are 4000px+ and will
make the page slow.

### Add a paper

Inside a project, copy one whole `<li class="paper">` block and edit it. The status label
is set by the class on the `<span>`:

| Class | Shows as |
|---|---|
| `s-pub` | Published |
| `s-cond` | Conditionally accepted |
| `s-rev` | Under review |
| `s-near` | Near submission |
| `s-prog` | In progress |

### Add a project

Copy one whole `<li class="project">` block. Two things to update beyond the text:

**The tags** — each is one `<li class="tag">` with a coloured dot:

```html
<li class="tag"><span class="dot mig"></span>migration</li>
```

Dot classes are `mig`, `env`, `hea`, `rur`.

**The stripe** down the left edge, which should list the same domains in the same order.
For three domains:

```html
style="--stripe:linear-gradient(to bottom,#eda100 0 33.3%,#008300 33.3% 66.6%,#2a78d6 66.6% 100%)"
```

For two, use `0 50%` and `50% 100%`. The colours:

| Domain | Hex | Dot class |
|---|---|---|
| migration | `#eda100` | `mig` |
| environment | `#008300` | `env` |
| population health | `#e34948` | `hea` |
| rurality | `#2a78d6` | `rur` |

### Update your CV

Upload the new PDF over `cv.pdf` in the root, keeping that exact filename. The download
button needs no change.

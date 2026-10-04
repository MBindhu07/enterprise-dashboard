# Semantic HTML5 & Accessible Enterprise Dashboard — Galaxy Theme

This project implements the enterprise dashboard specification with a deep-space galaxy visual theme and an optional daylight theme.

## Structure

```text
enterprise-dashboard/
├── index.html
├── users.html
├── reports.html
├── settings.html
├── 404.html
├── components/
│   ├── header.html
│   ├── sidebar.html
│   ├── footer.html
│   ├── data-table.html
│   ├── modal-dialog.html
│   ├── form-controls.html
│   ├── kpi-cards.html
│   ├── breadcrumb.html
│   ├── tabs.html
│   ├── toast.html
│   ├── accordion.html
│   ├── progress-meter.html
│   ├── notifications.html
│   ├── empty-loading.html
│   ├── avatar-menu.html
│   └── pagination.html
├── css/
│   └── styles.css
├── js/
│   ├── modal.js
│   ├── theme.js
│   ├── dashboard.js
│   ├── table.js
│   ├── tabs.js
│   └── settings.js
├── docs/validation/
│   └── README.md
└── README.md
```

## Theme

The default theme is Galaxy: deep-space backgrounds, star field, glass surfaces, violet/cyan accents, and neon-style borders. A Daylight mode is available from the header.

The theme uses CSS custom properties and respects `prefers-color-scheme` on first load. The user's explicit choice is saved with `localStorage`.

The theme was designed around the uploaded specification's accessibility requirements: high-contrast text, visible focus, reduced-motion support, text labels alongside status colors, and responsive reflow.

## Semantic HTML5

Every page uses:

- `header`
- `nav`
- `aside`
- one `main id="main"`
- `section`
- `article` where content is self-contained
- `footer`
- `figure` / `figcaption`
- `time datetime`

Each page has one `h1`, followed by logical heading levels.

A skip link is the first focusable element.

## Accessible table

The users page includes:

- `caption`
- `thead`
- `tbody`
- `tfoot`
- `th scope="col"`
- `th scope="row"`
- `aria-sort`
- real button sort controls
- horizontally scrollable wrapper with `tabindex="0"`, `role="region"` and accessible label
- text-based status badges with icons so meaning is not color-only

## Accessible modal

`js/modal.js` implements:

- native `<dialog>`
- `aria-labelledby`
- `aria-describedby`
- focus movement into the dialog
- keyboard focus trap
- Escape/cancel behavior
- labelled close button
- focus restoration to the triggering button
- form validation and `aria-invalid`

## Accessible forms

Settings demonstrates:

- text
- email
- telephone
- password
- number
- date
- select
- textarea
- checkbox
- radio

It uses:

- `required`
- `pattern`
- `minlength`
- `maxlength`
- `min`
- `max`
- `type="email"`
- `autocomplete`
- `aria-invalid`
- `aria-describedby`
- `role="alert"`
- `aria-live="polite"`

Required fields explicitly say `(required)` rather than depending on color alone.

## Additional components

The `components/` directory includes reusable reference markup for:

- KPI cards
- Breadcrumbs
- Tabs
- Toasts
- Accordion/FAQ
- Progress and meter
- Notifications
- Empty/loading states
- Avatar/user menu
- Pagination

The reports page demonstrates tabs and native `details/summary`.

## WCAG 2.1 checklist

- [x] Keyboard-operable native controls
- [x] Visible `:focus-visible` indicator
- [x] Color is not the only status indicator
- [x] Responsive reflow down to 320px
- [x] Text uses scalable relative sizing
- [x] Decorative avatar uses empty alt text
- [x] Interactive controls target approximately 44px
- [x] `prefers-reduced-motion` support
- [x] Semantic landmarks
- [x] Accessible tables
- [x] Accessible modal
- [x] Accessible form labels and validation
- [x] Live status/error messaging

## Contrast

The galaxy theme tokens were selected to provide strong contrast, but CSS comments or design assumptions are not validation evidence. Measure the final rendered token pairs using a contrast checker and record the measured ratios here before final submission.

Recommended contrast table to complete:

| Pair | Required | Measured |
|---|---:|---:|
| `--text` / `--space-0` | 4.5:1 | Validate |
| `--text-muted` / `--space-0` | 4.5:1 | Validate |
| `--violet` / `--space-0` | 4.5:1 | Validate |
| `--cyan` / `--space-0` | 4.5:1 | Validate |
| `--focus` / surrounding colors | 3:1 UI | Validate |
| button text / primary background | 4.5:1 | Validate |

## Validation

Use the official W3C Nu HTML Checker:

https://validator.w3.org/nu/

Validate every page and save screenshots under `docs/validation/`.

Do not claim zero errors or zero warnings until the actual validator has been run.

Recommended pages:

- `index.html`
- `users.html`
- `reports.html`
- `settings.html`
- `404.html`

Optional quality evidence:

- Lighthouse accessibility
- axe DevTools
- WAVE

## GitHub Actions

For a stronger submission, add CI that runs an HTML validator and accessibility test on every push. The project is deliberately static and can be extended with `html-validate` and `pa11y` in GitHub Actions.

## Local run

From the project directory:

```bash
python3 -m http.server 8000
```

Open:

```text
http://localhost:8000
```

## Suggested commit history

```text
feat: add semantic galaxy dashboard
feat: add accessible users table
feat: add keyboard accessible modal
feat: add accessible settings form
feat: add galaxy and daylight themes
feat: add tabs notifications and dashboard components
docs: add accessibility and validation documentation
```

## Submission checklist

- [ ] Run W3C validation on every HTML page.
- [ ] Save real validator screenshots.
- [ ] Test keyboard-only navigation.
- [ ] Test at 320px width.
- [ ] Test text zoom to 200%.
- [ ] Test dark and daylight themes.
- [ ] Test reduced motion.
- [ ] Run Lighthouse/axe/WAVE if required.
- [ ] Commit validation evidence.
- [ ] Push to a public GitHub repository.

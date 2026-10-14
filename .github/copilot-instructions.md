# Copilot instructions

Soc Ops is a Java 21 Spring Boot social bingo application. Application code lives
in `socops/`; the guided Copilot workshop lives in `workshop/`.

## Design guide

### Creative direction: the conversation arcade

Make the experience feel like a printed game card at a lively community meetup:
editorial, tactile, warm, and a little playful. Carry that identity across the
lobby, bingo board, victory dialog, and README. Favor deliberate compositions over
generic dashboard cards, blue call-to-action buttons, or purple gradients.

### Palette and typography

Use the theme variables defined in
`socops/src/main/resources/static/css/app.css`:

| Token | Value | Purpose |
| --- | --- | --- |
| `--paper` | `#f6f1e7` | Warm page and card surfaces |
| `--ink` | `#252b23` | Primary text, outlines, and buttons |
| `--muted` | `#5e655a` | Supporting copy |
| `--orange` | `#c44221` | Editorial accents and emphasis |
| `--lime` | `#d5ed8a` | Matched squares and celebration accents |
| `--line` | `#b9b9a7` | Subtle separators and tile borders |

Use `--display` for expressive serif headlines and `--mono` for small uppercase
labels, numbering, and card metadata. Body copy uses the local Trebuchet MS /
Gill Sans stack. Keep fonts local; do not add remote font requests. Use fluid
headline sizes and generous line height for readable body text.

### Layout and surfaces

- Give the lobby a strong editorial headline beside a tilted sample game card.
  Stack those elements on narrow screens.
- Use restrained dotted paper texture, thin ink outlines, offset hard shadows,
  and occasional circular stickers. Keep decoration separate from controls.
- Keep the playable board upright and in five columns at every viewport size.
  Let rows grow to fit prompts; never truncate conversation starters.
- Use lime plus a check mark for selected tiles, warm peach for a winning line,
  and ink with lime lettering for the free space. Do not rely on color alone.
- Preserve existing CSS utilities. Add reusable utilities or low-specificity
  component classes to `app.css`, not inline styles or an external CSS framework.
  The arcade theme tokens take precedence over legacy blue/gray color utilities
  when styling the redesigned game.

### Motion and interaction

Use CSS for short, staggered entrance reveals and subtle tactile hover/press
feedback. Honor `prefers-reduced-motion` by disabling animation and transitions.
Disable the start button while loading and expose request failures visibly with
a retry path; never leave a failed request looking successful.

### Accessibility and responsive behavior

Use semantic headings, native buttons, visible keyboard focus, and descriptive
accessible names. Keep tile selection exposed through `aria-pressed`, hide purely
decorative symbols from assistive technology, and announce progress with a polite
live region. When repainting tiles, restore keyboard focus to the tapped tile.

The victory dialog must have an accessible title, move focus into the dialog,
keep background controls inert, support Escape, and return focus when dismissed.
Check the lobby, active board, and victory state on narrow mobile and desktop
layouts, including long prompts and enlarged text. Maintain readable contrast
and adequate touch targets.

### Copy and README

Write short, inviting, human copy about meeting people and hearing their stories.
Use the "Strangers. Stories. Bingo." motif without crowding the interface.
The README is the project's landing page: use repository-local artwork with
meaningful alt text, clear links to playing and the workshop, and accurate setup
instructions. Avoid remote badge clutter and unsupported feature claims.

### Preserve the game

Visual changes must retain shuffled 5-by-5 boards, the selected centre free space,
toggleable matches, row/column/diagonal victories, browser persistence, and the
ability to keep playing after bingo. Keep the existing DOM IDs and public game
handlers unless updating every caller.

## Validation

From `socops/`, use `./mvnw verify` for Java tests and Checkstyle. No separate
Maven installation is required. For frontend changes, also exercise loading,
marking/unmarking, persistence, victory, keyboard focus, and request failures.

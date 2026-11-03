# HTML Report Format

The architectural review is a single self-contained HTML file in the OS temp directory. Use inline CSS, semantic HTML, and static inline SVG. It must render offline without JavaScript or external resources. Draw dependency graphs, sequences, mass diagrams, and cross-sections directly; vary the diagram to suit the candidate.

Escape repository-derived text for its HTML or SVG context. Never insert source snippets as raw markup, event handlers, scripts, or embedded documents. Keep the restrictive content-security policy from the scaffold as a second guardrail, not a substitute for escaping.

## Scaffold

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <meta http-equiv="Content-Security-Policy" content="default-src 'none'; style-src 'unsafe-inline'; base-uri 'none'; form-action 'none'" />
    <title>Architecture review for {{repo name}}</title>
    <style>
      * { box-sizing: border-box; }
      body { margin: 0; background: #fafaf9; color: #0f172a;
             font: 1rem/1.5 system-ui, sans-serif; }
      main { max-width: 70rem; margin: auto; padding: 3rem 1.5rem; }
      header, section { margin-bottom: 3rem; }
      article { margin-bottom: 2rem; padding: 1.5rem; background: white;
                border: 1px solid #cbd5e1; border-radius: .75rem; }
      .comparison { display: grid; grid-template-columns: repeat(2, minmax(0, 1fr));
                    gap: 1rem; }
      figure { margin: 0; }
      svg { display: block; width: 100%; height: auto; }
      .files { font: .875rem ui-monospace, monospace; overflow-wrap: anywhere; }
      .module-label { font-size: .75rem; letter-spacing: .05em; text-transform: uppercase; }
      .seam { stroke-dasharray: 4 4; }
      .leak { stroke: #dc2626; }
      .deep { fill: #0f172a; stroke: #0f172a; stroke-width: 3; }
      @media (max-width: 45rem) { .comparison { grid-template-columns: 1fr; } }
    </style>
  </head>
  <body>
    <main>
      <header>...</header>
      <section id="candidates">...</section>
      <section id="top-recommendation">...</section>
    </main>
  </body>
</html>
```

## Header

Repo name, date, and a compact legend: solid box = module, dashed line = seam, red arrow = leakage, thick dark box = deep module. No introduction paragraph. Straight into the candidates.

## Candidate card

The diagrams carry the weight. Prose is sparse, plain, and uses the glossary terms (from the `/codebase-design` skill) without ceremony.

Each candidate is one `<article>`:

- **Title**: short, names the deepening (e.g. "Collapse the Order intake pipeline").
- **Badge row**: recommendation strength (`Strong` = emerald, `Worth exploring` = amber, `Speculative` = slate), plus a tag for the dependency category (`in-process`, `local-substitutable`, `ports & adapters`, `mock`).
- **Files**: monospaced list, using the `.files` class.
- **Before / After diagram**: the centrepiece. Two columns, side by side. See patterns below.
- **Problem**: one sentence. What hurts.
- **Solution**: one sentence. What changes.
- **Wins**: bullets, ≤6 words each. e.g. "Tests hit one interface", "Pricing logic stops leaking", "Delete 4 shallow wrappers".
- **ADR callout** (if applicable): one line in an amber-tinted box.

No paragraphs of explanation. If the diagram needs a paragraph to be understood, redraw the diagram.

## Diagram patterns

Pick the pattern that fits the candidate. Mix them. Don't make every diagram look the same. Variety is part of the point.

### Static SVG graph (dependencies / call flow)

Use labelled boxes and SVG paths when the point is "X calls Y calls Z, and look at the mess." Colour leakage edges red and the deep module dark. Draw sequence diagrams with vertical lifelines and horizontal arrows for "before: 6 round-trips; after: 1." Give every diagram an accessible title and a visible caption. Use unique IDs for SVG titles and markers when repeating diagrams.

```html
<figure>
  <svg viewBox="0 0 440 120" role="img" aria-labelledby="candidate-1-before-title">
    <title id="candidate-1-before-title">Order intake leaks pricing decisions</title>
    <defs>
      <marker id="candidate-1-arrow" viewBox="0 0 10 10" refX="9" refY="5"
              markerWidth="6" markerHeight="6" orient="auto-start-reverse">
        <path d="M 0 0 L 10 5 L 0 10 z" fill="#dc2626" />
      </marker>
    </defs>
    <rect x="10" y="25" width="150" height="60" fill="#f1f5f9" stroke="#64748b" />
    <text x="85" y="60" text-anchor="middle">Order intake</text>
    <path class="leak seam" d="M 160 55 H 275" fill="none" stroke-width="2"
          marker-end="url(#candidate-1-arrow)" />
    <rect x="280" y="25" width="150" height="60" fill="#f1f5f9" stroke="#64748b" />
    <text x="355" y="60" text-anchor="middle">Pricing</text>
  </svg>
  <figcaption>Before: pricing decisions leak across the seam.</figcaption>
</figure>
```

### Hand-built boxes-and-arrows (editorial layouts)

Modules as `<div>`s with borders and labels. Arrows as inline SVG `<line>` or `<path>` elements positioned over a relative container. Use this when you want the "after" diagram to feel like one thick-bordered deep module with greyed-out internals. Keep labels readable on narrow screens.

### Cross-section (good for layered shallowness)

Stack horizontal bands with a fixed minimum height and a thick left border to show layers a call passes through. Before: 6 thin layers each doing nothing. After: 1 thick band labelled with the consolidated responsibility.

### Mass diagram (good for "interface as wide as implementation")

Two rectangles per module: one for interface surface area, one for implementation. Before: interface rectangle is nearly as tall as the implementation rectangle (shallow). After: interface rectangle is short, implementation rectangle is tall (deep).

### Call-graph collapse

Before: a tree of function calls rendered as nested boxes. After: the same tree collapsed into one box, with the now-internal calls shown faded inside it.

## Style guidance

- Lean editorial, not corporate-dashboard. Generous whitespace. System serif fonts are optional for headings; do not fetch web fonts.
- Colour sparingly: one accent (emerald or indigo) plus red for leakage and amber for warnings.
- Keep diagrams ~320px tall so before/after sits comfortably side by side without scrolling.
- Use the `.module-label` class for module labels inside diagrams, so they read as schematic, not as UI.
- No scripts, event handlers, external stylesheets, network resources, or embedded documents. Use local fragment links for navigation within the static report.

## Top recommendation section

One larger card. Candidate name, one sentence on why, anchor link to its card. That's it.

## Tone

Plain English, concise, but the architectural nouns and verbs come straight from the `/codebase-design` skill. Concision is not an excuse to drift.

**Use exactly:** module, interface, implementation, depth, deep, shallow, seam, adapter, leverage, locality.

**Never substitute:** component, service, unit (for module) · API, signature (for interface) · boundary (for seam) · layer, wrapper (for module, when you mean module).

**Phrasings that fit the style:**

- "Order intake module is shallow: interface nearly matches the implementation."
- "Pricing leaks across the seam."
- "Deepen: one interface, one place to test."
- "Two adapters justify the seam: HTTP in prod, in-memory in tests."

**Wins bullets** name the gain in glossary terms: *"locality: bugs concentrate in one module"*, *"leverage: one interface, N call sites"*, *"interface shrinks; implementation absorbs the wrappers"*. Don't write *"easier to maintain"* or *"cleaner code"*, because those terms aren't in the glossary and don't earn their place.

No hedging, no throat-clearing, no "it's worth noting that…". If a sentence could be a bullet, make it a bullet. If a bullet could be cut, cut it. If a term isn't in the `/codebase-design` glossary, reach for one that is before inventing a new one.

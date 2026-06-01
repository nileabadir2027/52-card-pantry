# The 52-Card Pantry

A 52-card deck of recipe cards for college students — built for **CS 330**, Northwestern.

> Students trade off affordability, nutrition, and convenience at every meal. The Pantry deck makes the choice fast and fun: shuffle, draw a card, cook what comes up.

**Team:** Nile · Anthony · Ryan

---

## Try it now

**Live shuffler →** _Paste your GitHub Pages URL here once you enable Pages (Settings → Pages → main branch / root)._

Or just download this repo and double-click `index.html` to open the prototype locally — no install required.

---

## How the deck works

| Element | Meaning |
|---|---|
| **Suit (numbered cards)** | Meal type — ♥ Breakfast, ♦ Lunch, ♣ Dinner, ♠ Dessert |
| **Number** (2–10) | Number of ingredients in the recipe |
| **Face cards** (J, Q, K, A) | 10-ingredient "signature" recipes — J = Breakfast, Q = Lunch, K = Dinner, A = Dessert |

Total: **13 cards per meal type × 4 meal types = 52 cards.** Every recipe's ingredient count exactly matches its card number.

### Sample cards

![Breakfast sample cards — 3♥ Yogurt Berry Bowl and 5♥ Banana Oat Pancakes](screenshots/sample-cards-breakfast.jpg)
![Dinner sample cards — 8♣ Sheet-Pan Sausage and K♣ One-Pot Chicken Pasta](screenshots/sample-cards-dinner.jpg)

---

## What's in this repo

```
/
├── index.html              ← the working shuffler (open in any browser)
├── recipes.json            ← all 52 recipes as structured data
├── README.md
├── docs/
│   ├── prototype-deck.pptx     ← L7 high-fidelity prototype explainer
│   ├── sample-cards.pptx       ← 16 designed sample cards used in user testing
│   └── iteration-plan.docx     ← MVP definition, key features, task ownership
└── screenshots/
    └── ...
```

### The shuffler

`index.html` is a self-contained prototype — one HTML file with embedded recipe data, no build step, no dependencies. Open it and you can:

- **Shuffle & Draw** — pull a random card from the deck (no repeats until you reset).
- **Filter by meal type** — restrict the pool to Breakfast / Lunch / Dinner / Dessert.
- **Plan My Day** — draw one random card from each suit for a full day of surprise meals.
- **Reset** — re-shuffle the full deck.

### The recipe data

`recipes.json` is the source of truth — 52 entries with this shape:

```json
{
  "id": "5H",
  "rank": "5",
  "suit": "H",
  "suitName": "Hearts",
  "suitSymbol": "♥",
  "meal": "Breakfast",
  "name": "Banana Oat Pancakes",
  "ingredients": ["½ cup rolled oats", "1 ripe banana", "1 egg", "¼ cup milk", "Pinch of cinnamon"],
  "ingredientCount": 5,
  "steps": ["Blend everything smooth.", "Pour onto a hot non-stick pan.", "Flip when bubbles form.", "Stack and eat."],
  "cost": "$0.85",
  "time": "10 min",
  "servings": 1
}
```

To use this data in a fuller app (React, mobile, etc.), `fetch('recipes.json')` and render however you like.

---

## User testing & next iteration

We tested the sample-card design with a college-student user. The clearest themes:

- The card layout and the **suit-as-meal + number-as-ingredients system was immediately intuitive**.
- **Face cards** can confuse non-card-players — the explicit "Ingredients: 10" label saves it, and we'll reinforce that in the next round.
- The biggest design tension was **organize vs. shuffle**: testers want an organized cookbook-style default for daily use, but loved the random shuffle for social occasions (date night, group night). The MVP supports both modes.
- Future ideas (intentionally scoped as stretch so they don't crowd the card): nutrition macros and "joker"-style grocery-store helper cards.

Full write-up in [`docs/iteration-plan.docx`](docs/iteration-plan.docx).

---

## Roles

| Member | Owns |
|---|---|
| **Nile** | Card design, user testing, the shuffler UX |
| **Anthony** | Recipe content (ingredient counts validated against ranks) |
| **Ryan** | Concept & content brainstorming, organize-vs-shuffle play modes, stretch ideas |

---

## Running locally

No build step. No install. Just:

```
# clone or download this repo
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

Or double-click `index.html` in your file browser.

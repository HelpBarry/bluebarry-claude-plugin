---
name: setup
description: Set up bluebarry for the user's online store, from connecting the store to a first thing to build. Use right after the plugin is installed, or when the user asks to set up, connect or get started with bluebarry.
---

Help the merchant get from "installed" to their first useful result in bluebarry. The merchant's own requests come first: if they ask for something specific, do that instead.

1. Call `get_store_overview`. Don't assume anything about the store before it answers. In Claude it also shows the store card: the setup checklist with a button per step while the store isn't set up, then what the store runs.
2. If `ready` is false, nothing can be built, previewed or read yet. Say so in a sentence, then give `nextStep` in your own words with its link. Don't retell the whole checklist: the card shows it. Stop there and wait.
3. The card checks the store again while it's open and tells you when a step is done. When the merchant says they did it, or the card tells you, call `get_store_overview` again and continue with the next step. A step with status `waiting` (the first product import) finishes by itself: say so.
4. Once `ready` is true, say in one line what this connection may do (`connection.mayDo`). If it's read only and they want to build, give them `connection.settingsUrl`.
5. Summarize what the store runs in a short list: each feature in `setup.features`, live, draft or not set up, with any blocker. Mention the open `setupSteps` for going live (switching bluebarry on in the theme) only when the merchant gets to publishing.
6. Propose one concrete first step that fits what's missing, for example a product quiz when there is none, or fixing searches that find nothing when search is live. Ask whether they want to start with it, and build nothing until they say yes.

Keep it short: a few sentences and one list. Don't quote prices or offers beyond what a setup step says.

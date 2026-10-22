---
name: build
description: Build, change, preview and publish product quizzes, on-site search, popups, collection pages and recommendations in the user's bluebarry store. Use when the user wants a product finder or quiz, a newsletter or offer popup, a collection page, product recommendations or other changes to their own store in bluebarry.
---

Work in the merchant's bluebarry store through the bluebarry tools. The merchant's explicit instructions come first, then the standing instructions `get_store_overview` returns, then these steps.

## Before you build

1. Call `get_store_overview` once per conversation and follow `merchantInstructions`. If the store isn't set up or has no plan, help with that first (the setup skill) instead of building.
2. Collection pages are written into a Shopify theme, so they're for stores whose `onlineStore.platform` is shopify. Offer the other surfaces to WooCommerce, Magento and CCV stores.
3. Read `get_guide` for the surface you're about to build or change (quiz, search, popup, collectionPage, merchandising for recommendations) and follow it: it holds the rules bluebarry's own assistant works by. `get_guide fields/<entityType>` has every field of a payload.
4. Read what exists with `list_entities` and `get_entity`. Base what you build on the store's real catalog (`search_products`, `get_catalog_schema`) and data (`query_analytics`). Never invent products, numbers or results.

## Build and check

5. Create with the surface's `create_` tool (`create_quiz`, `create_popup`, `create_collection_page`, `create_recommendation_block`, ...) and change it with its `edit_` tool. Send only the fields you set, and batch related fields into one change.
6. Check visual work with `render_previews` on mobile and desktop. Claude shows the screenshots as a strip the merchant can enlarge. Fix what looks wrong before you call it done.
7. Share each result's `studioUrl` so the merchant can review it in bluebarry Studio.

## Going live

8. New quizzes, popups and pages are drafts. Publish only when the merchant asks. `publish` first returns `confirmationRequired`, and Claude shows a card with what goes live and a Publish button. Tell them in one line what goes live and that they can press Publish or tell you to go ahead. Call `publish` again with the token only after they say yes, and never confirm for them. If they pressed the button, it's done: don't publish again.
9. Then call `check_storefront` to say what shows on the store now and give the one step for what doesn't yet: on Shopify the app embed or a widget's theme block, on WooCommerce and Magento the widget's placement, elsewhere the Studio page that places it. Call it again once they say they did it.

## Limits

- A quiz question, answer, filter or result card, a search synonym, redirect, banner or rule, and a collection page section can be deleted with the edit tool's `operation` delete, after the merchant confirms like a publish: it can't be undone. Whole quizzes, popups and pages, sending email campaigns and points for individual customers stay in bluebarry Studio. Say so and share the Studio link instead of trying.
- Shopper email addresses are never available. Use counts and aggregates.
- When a result's `canUndo` is false, tell the merchant before you change the same thing again. `undo_changes` reverses the rest.

---
name: fix-search
description: Find and fix searches on the user's online store that find nothing or the wrong products, with bluebarry synonyms, redirects and merchandising rules. Use when the user asks why their site search doesn't find something, about searches with no results, or wants better search results.
---

Fix the store's search with bluebarry's search tools. Search changes reach shoppers right away, so the merchant approves the list of fixes before you make them.

1. Call `get_store_overview`. If search isn't set up, offer to set it up with the build skill instead.
2. Read `get_guide` topic `search`, then find the search profile with `list_entities` (type searchProfile).
3. For searches that find nothing, call `query_analytics` with report `searchZeroResults` and `filters.searchProfileId`. Each term comes classified:
   - `fixable`: one synonym away. The fix is a SearchSynonym to its `suggestedSynonymTarget`.
   - `contentGap`: a question rather than a product. The fix is a SearchRedirect to the page that answers it.
   - `catalogGap`: demand the store doesn't stock. Search can't fix it: report it to the merchant with how often it was searched.
4. For a term that finds the wrong products, or one the merchant names, call `diagnose_search`: it says how the term was read and why each product shows or is missing. Fix the cause, for example a SearchRule that pins or boosts the right products, or a synonym.
5. Show the merchant one table: term, searches, what you'd add. Wait for their yes.
6. Make each fix with `create_search_setup`, with `entityId` set to the search profile id. They apply to the live search at once and each can be undone with `undo_changes`: say so.
7. Check two or three of the fixed terms again with `diagnose_search` and report what shoppers now get.

---
name: store-report
description: Report how the user's online store and its bluebarry quizzes, search, recommendations and popups perform, what changed and what to do next, in chat or as a spreadsheet, document or slide deck. Use when the user asks how their store, quizzes, search or popups are doing, wants a weekly or monthly report, or wants store numbers in Excel, Word or PowerPoint.
---

Report on the merchant's store from bluebarry's numbers. Every figure comes from a tool result: never estimate one you didn't read.

## Gather

1. Call `get_store_overview` for what the store runs. Only report on features that are live or had traffic in the period.
2. Pick the period: what the merchant asked for, otherwise the last 30 days against the 30 days before. Say which dates you used.
3. Call `query_analytics` with these reports, each over the same `dateRange`:
   - `storePerformance`: orders, average order value, conversion, new and returning customers, bestsellers, products bought together. Say where the order history starts when it says so.
   - Quizzes: `quizFunnelPerformance` for every quiz, and `quizSummary` with `compareToPrevious` for the trend. Report `quizInsights` ranks what to fix.
   - Search: `searchAnalytics`, and `searchZeroResults` per search profile when the zero-result rate stands out.
   - `recommendationPerformance` and `popupPerformance` when those run.
4. Read `get_guide` topic `analytics` before you interpret, and topic `optimize` before you propose work.

## Write

5. Open with three headline numbers and how each moved. Then one short section per surface: what happened and why it matters.
6. Quote differences the tools computed as they are, never recompute them. Call something better or worse only when the result's verdict says so; "too early" stays too early.
7. End with at most three next steps, each sized in money from the numbers you read and each one thing bluebarry can do (a quiz question to fix, synonyms for searches that find nothing, a recommendation block for products bought together). Offer to build the first one.

## Deliver

8. In chat by default: the summary and one compact table per surface.
9. When they want a file, or the report is for a meeting, make it with Claude's file creation: a spreadsheet with a summary sheet and one sheet per report table, a slide deck with one slide per section, or a document. Use only the numbers you read, and put the period and "Source: bluebarry" on it.
10. If they want it every week or month, offer to set it up as a scheduled task where their Claude app has them (Cowork): this skill, the period ("last 7 days against the 7 days before") and the format as the task's prompt. Say it's scheduled only after it is.

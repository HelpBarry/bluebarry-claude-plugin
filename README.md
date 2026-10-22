# bluebarry for Claude

bluebarry helps online stores turn browsers into buyers with product quizzes, on-site search, popups, collection pages and recommendations. This plugin connects Claude to your bluebarry store, so you can build, check and publish them from a conversation, on your real catalog, and ask how your store is doing.

![bluebarry](./assets/logo.png)

## What you can ask

- "Set up bluebarry for my store." Walks you through connecting your store and proposes a first thing to build.
- "Build a quiz that helps shoppers pick the right chef's knife, then show me a mobile preview."
- "Which searches on my store found nothing this month? Fix the obvious ones."
- "How did my store do last month? Put it in a spreadsheet."
- "Publish the quiz." Claude shows what goes live and a Publish button; nothing goes live until you confirm.

## What's in the plugin

| Part | What it does |
|---|---|
| bluebarry connector | The bluebarry MCP server at `https://mcp.bluebarry.ai/mcp`. Its tools read your store's setup, catalog and analytics, create and edit drafts, render previews and publish what you confirm. Claude shows your store, previews and publish confirmations as cards in the conversation. |
| `setup` skill | Gets a new store from connected to a first useful result. |
| `build` skill | How Claude builds and changes quizzes, search, popups, collection pages and recommendations: read first, preview, publish only when you confirm. |
| `store-report` skill | A report on your store and its quizzes, search, recommendations and popups, in chat or as a spreadsheet, document or slide deck. |
| `fix-search` skill | Finds searches that return nothing or the wrong products and fixes them with synonyms, redirects and rules once you approve the list. |

## Install

In Claude, find bluebarry in the plugin directory and add it. In Claude Code:

```
/plugin install bluebarry --marketplace HelpBarry/bluebarry-claude-plugin
```

Then connect your bluebarry account when Claude asks.

## What you need

- A bluebarry account. You can create one while connecting.
- A store connected to bluebarry: the bluebarry app for Shopify, or the WooCommerce, Magento or CCV Shop integration.

## Data and permissions

The plugin talks only to bluebarry's MCP server, over HTTPS, with the OAuth sign-in you complete when you connect. It runs no code on your computer.

- In bluebarry Studio, under Settings and then AI assistants, you choose what assistants may do: read only, create and edit, or also publish. You can disconnect Claude there too.
- New quizzes, popups and pages start as drafts. Publishing and switches that go live for shoppers always need your confirmation.
- Every change shows up in your bluebarry history, where most changes can be undone.
- Shopper email addresses and loyalty member details never reach Claude. Deleting a part of something, such as a quiz question or a search synonym, always needs your confirmation. Deleting whole quizzes, popups and pages, sending email campaigns and loyalty points stay in bluebarry Studio.

Privacy policy: https://bluebarry.ai/privacy-policy#ai-assistants. Help: https://bluebarry.ai/help/integrations-automation/connect-bluebarry-mcp-to-claude. Support: support@bluebarry.ai.

---
title: API Tokens.
date: Last Modified 
permalink: /usage/api-tokens/index.html
eleventyNavigation:
  key: usage-api-tokens
  order: 585
  title: API Tokens.
  parent: usage
---

![]({{"/content/images/api_tokens.jpg" | url}})

* API tokens allow programmatic access to the Jelu REST API without exposing your password
* This is useful for automation scripts, third-party integrations, CI/CD pipelines and tools like [jelu-importer](https://github.com/aauren/jelu-importer)
* Tokens use the standard `Authorization: Bearer` header and work alongside existing session-based authentication
* Each token has fine-grained scopes so you can limit what it can access

## Creating a token

* Navigate to the settings menu (accessible from the left sidebar) and click **API Tokens**
* Click the **+ Create Token** button
* Enter a name for your token (eg: "Backup Script", "Importer")
* Select the scopes you need (see table below)
* Optionally set an expiration date, or leave it as "Never expires"

![]({{"/content/images/api_token_create.jpg" | url}})

!!! danger
    * The full token is shown **only once** after creation. Copy it immediately and store it securely.
    * If you lose the token you will need to create a new one.

## Available scopes

| Scope | Description |
|-------|-------------|
| `books:read` | View books, authors, tags, series, publishers |
| `books:write` | Create, modify and delete books and metadata |
| `reading:read` | View reading events and statistics |
| `reading:write` | Create, modify and delete reading events |
| `reviews:read` | View reviews |
| `reviews:write` | Create, modify and delete reviews |
| `lists:read` | View custom lists, shelves and quotes |
| `lists:write` | Create, modify and delete lists, shelves and quotes |
| `import:write` | Import and export data |
| `metadata:read` | Fetch external metadata from providers |

!!! tip
    * Only grant the scopes your integration actually needs. For example a backup script might only need the `:read` scopes.

## Using a token

Once you have a token, pass it in the `Authorization` header :

```bash
curl -H "Authorization: Bearer jelu_a1b2c3d4..." http://localhost:11111/api/v1/books
```

* This works with any endpoint available through the [REST API]({{"/usage/api/index.html" | url}})

## Managing tokens

* On the API Tokens page you can see all your tokens with their name, scopes, creation date, last used date and usage count
* Click the delete button to immediately revoke a token
* Admins can view and revoke tokens for all users

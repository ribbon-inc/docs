# Ribbon API Documentation

Official documentation for the Ribbon API and platform.

**Live docs:** [docs.ribbon.ai](https://docs.ribbon.ai)

## Structure

- `/docs` - API guides and quickstart
- `/ribbon-public-api` - API reference (generated from OpenAPI spec)
- `/knowledge-base` - Platform knowledge base articles
- `/images` - Screenshots and assets

## Local Development

Install the [Mintlify CLI](https://www.npmjs.com/package/mintlify):

```bash
npm i -g mintlify
```

Run locally:

```bash
mintlify dev
```

Preview at `http://localhost:3000`

## Updating the OpenAPI Spec

When the API changes, update the documentation:

1. **Download the latest spec** from production:

```bash
curl -o api-spec.json https://app.ribbon.ai/be-api/doc/api-spec.json
```

2. **Regenerate the API reference pages** (optional - only if endpoints changed):

```bash
npx @mintlify/scraping openapi-file api-spec.json
```

This creates or updates `.mdx` files in `/ribbon-public-api` from the spec.

3. **Add new endpoints to the sidebar** – Mintlify only shows pages that are listed in `docs.json`. For each new endpoint:

   - Open `docs.json` and go to the **API Reference** tab → **Ribbon Public API** section.
   - **New endpoint in an existing group** (e.g. another interview endpoint): add the page path to that group’s `pages` array, e.g. `"ribbon-public-api/get-my-endpoint"` (no `.mdx`).
   - **New group** (e.g. a new resource like “Teams”): add a new object to the `pages` array with `group`, `expanded: true`, and `pages` listing the endpoint paths:

   ```json
   {
     "group": "Your Group Name",
     "expanded": true,
     "pages": ["ribbon-public-api/your-endpoint-slug"]
   }
   ```

   The slug is the filename without `.mdx` (e.g. `get-teams` for `get-teams.mdx`).

4. **Commit and push** – changes deploy automatically.

## Deployment

Changes pushed to `main` are automatically deployed via Mintlify.

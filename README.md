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

This will output a navigation suggestion. Update `docs.json` if new endpoints were added.

3. **Commit and push** - changes deploy automatically.

## Deployment

Changes pushed to `main` are automatically deployed via Mintlify.

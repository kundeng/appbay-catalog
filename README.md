# Appbay Catalog

Curated app definitions for [Appbay](https://github.com/kundeng/appbay).

Each directory is a catalog entry containing:

```
<app-name>/
  catalog.yaml          # browse metadata (description, tags, required inputs)
  appbay.yaml           # deployment config (traits, scope, upstream ref)
  docker-compose.yml    # upstream compose file
  .env.defaults         # optional: default environment values
  README.md             # optional: notes about the app
```

## Readiness levels

- **raw** — upstream compose only, no `appbay.yaml`. Works with Appbay's upstream transform but may need manual env setup.
- **augmented** — upstream compose + curated `appbay.yaml` with traits (ingress, secrets, backup, etc.). Works with sensible defaults.
- **native** — compose + `appbay.yaml` written together. Full Appbay integration.

## Usage

```bash
# Add this catalog to Appbay
appbay catalog add-source appbay-catalog https://github.com/kundeng/appbay-catalog

# Or if already bundled
appbay catalog list
appbay install <app-name>
```

## Contributing

Each app is manually curated. To add an app:

1. Create a directory named after the app
2. Add the upstream `docker-compose.yml`
3. Write `catalog.yaml` with metadata and `required_inputs`
4. Write `appbay.yaml` with trait configuration and sensible defaults
5. Test: `appbay install <name> && appbay validate <name> && appbay up <name>`

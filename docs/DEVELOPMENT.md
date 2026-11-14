# Development

## Supported workflow

Prerequisites are Git and Docker Desktop (Windows/macOS) or Docker Engine with
the Compose plugin (Linux). The supported lifecycle is:

```bash
docker compose up --build
docker compose ps
docker compose logs -f
docker compose down
```

Open `http://localhost:8080`; the backend is at `http://localhost:8000` and its
interactive docs at `/docs`. Ports can be changed through `.env` copied from
`.env.example`.

## Tests and quality

The Python configuration in `pyproject.toml` runs pytest over `tests`,
`app/backend/tests`, and `model/tests`, with Ruff rules `E`, `F`, `I`, and `UP`
and a 100-character line limit. Run targeted tests for changed components, then
the relevant broader suite. Validate Compose behavior for cross-component
changes. Add tests for new functionality.

## Data and provenance

Keep downloads in ignored `data/raw/`, derived files in ignored
`data/processed/`, and supplied external files in ignored `data/external/`.
Never commit secrets, large datasets, or model weights. Record source, version,
license, retrieval date, query, transformations, units, quality flags, and
validation results. Mock and simulated values must be visibly labeled.

## Compatibility

Use portable paths and commands where practical. Keep the baseline CPU
compatible and avoid platform-specific assumptions. Do not claim an external
integration works until a repeatable test has passed.


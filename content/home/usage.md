+++
weight = 20
+++

# Usage

---

## Prerequisites

- Have a postgres database set
- Some initial metadata files
- Docker

---

### Configuration

Inside `metadata/tables.yaml`:

```yaml
- table:
    schema: public
    name: posts
  select_permissions:
  - role: api
    permission:
      columns:
      - id
      - title
      - body
      - updated_at
      - created_ad
      filter: {}
      allow_aggregations: true

```

---

# Configure database

Supabase
```sql
CREATE TABLE posts (
    id              SERIAL PRIMARY KEY,
    title           TEXT,
    body            TEXT,
    created_at      TIMESTAMP WITH TIME ZONE DEFAULT now(),
    updated_at      TIMESTAMP WITH TIME ZONE DEFAULT now()
);
```

---

# Configure Environment

.env
```
HASURA_GRAPHQL_DATABASE_URL=postgres://postgres:xxxxxxxxxxxxxxxxxxxxx@db.dwaudnmhfvswvnggkxxk.supabase.co:5432/postgres
HASURA_GRAPHQL_ENABLE_CONSOLE=true
HASURA_GRAPHQL_DEV_MODE=true
HASURA_GRAPHQL_METADATA_DIR=metadata/
```

---

### Docker run


```sh
docker run -d -p 8080:8080 \
    --env-file .env \
    -v /Users/francisco/Desktop/hasura-poc/server/metadata:/metadata \
    hasura/graphql-engine:v1.2.0.cli-migrations-v2
```

<small>This docker images auto applies migrations on run.</small>

---

### Presentation at '/{section}/'

Add slides to `content/{section}/_index.md`:

```markdown
+++
outputs = ["Reveal"]
+++

# Slide 1

---

# Slide 2
```

---

Add slides from other files in `content/{section}/*.md`

```markdown
+++
weight = 10
+++

# Slide 3

---

# Slide 4
```

<small>💡 Tip: Use `weight` to specify the order that files should be considered.</small>


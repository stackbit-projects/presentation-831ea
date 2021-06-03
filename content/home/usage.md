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

# Slide 1

Hello world!
```

---

### Add slides

Separate them by `---` surrounded by blank lines:

```
# Slide 1

Hello world!

---

# Slide 2

Hello program!
```

---

### Add slides with other files

Add slides to `content/home/*.md`

```markdown
+++
weight = 10
+++

# Slide 3

---

# Slide 4
```

<small>💡 Tip: Use `weight` to specify the order that files should be considered.</small>

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


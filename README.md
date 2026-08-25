# todo

The canonical tutorial app: a reactive list with add / toggle / remove.

Concepts demonstrated:

- **Array signals** - `signal_array("todos")` holds an ordered list of
  record maps; `.all()` snapshots it, `.set(rows)` writes it back.
- **`<for each="todos" key="id">`** - one row subtree per item, diffed by
  the `key` field so focus / scroll survive edits. Row fields are read
  with the `{row.field}` form.
- **Per-row actions** - buttons interpolate the row id into their own id
  (`id="rm|{row.id}"`); the global `on_click(id)` fallback parses the
  prefix. Compare with the per-id `on("click", ...)` routing used for
  the static Add button.
- **Derived presentation** - `mark` / `label_cls` / `check_cls` are
  computed in the script (`make_row`), keeping markup declarative.
- **Records in candela** - a map literal holds one value type, so a row's
  fields are strings; `as_list` / `as_map` read the array back, and a filter
  is an explicit loop because candela has no closure value.
- **`<scroll>`** - the list scrolls independently; try adding 30 rows.

Run it:

```sh
lumenc run .
```

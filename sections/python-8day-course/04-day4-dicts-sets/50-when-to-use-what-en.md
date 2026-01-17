# When to Use What?

## Lists

**Use when:**
- Order matters
- Need duplicates
- Need to modify items
- Need indexing/slicing

**Example:** Shopping list, sequence of steps

## Tuples

**Use when:**
- Data shouldn't change
- Need hashable type (for dict keys)
- Slightly faster than lists

**Example:** Coordinates, RGB colors, database records

## Dictionaries

**Use when:**
- Need key-value mapping
- Need fast lookup by key
- Data has labels/names

**Example:** User profiles, configuration, word counts

## Sets

**Use when:**
- Need unique items only
- Need set operations (union, intersection)
- Fast membership testing

**Example:** Unique tags, removing duplicates, finding common items

## Comparison Table

| Feature | List | Tuple | Dict | Set |
|---------|------|-------|------|-----|
| Ordered | ✓ | ✓ | ✓* | ✗ |
| Mutable | ✓ | ✗ | ✓ | ✓ |
| Indexed | ✓ | ✓ | By key | ✗ |
| Duplicates | ✓ | ✓ | Keys: ✗, Values: ✓ | ✗ |
| Syntax | `[]` | `()` | `{}` | `{}` |

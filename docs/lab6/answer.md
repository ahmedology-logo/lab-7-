# Lab 6 answers

## Task A1
No. 100% coverage only shows every line was executed by some test, not that the tests check the right behaviour.
## Task C1: smells in legacy_invoice.py

| Smell | Where | Principle it breaks |
|---|---|---|
| Long if/elif chain on `kind` | loop body + after the loop | OCP: a new student type means editing this function |
| One function calculates, formats, writes a file and prints | whole `make_invoice` | SRP: several reasons to change |
| Magic numbers (1200, 2000, 5000, 0.5) | inside the loop and after it | Readability / DRY (1200 is repeated) |
| File opened inside the function, without `with` | `open(...)` / `f.close()` | DIP: depends on the disk, cannot be tested without writing files |
| Fee worked out per course, though only total hours matter | the `for` loop | KISS: needless complexity |
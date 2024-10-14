# Reproducer for `git grep` Issue

This is a simple reproducer repo for an issue with `git grep` not finding
all occurrences of a string:

```bash
macOS$ git --version
git version 2.47.0

# this is the good case
macOS$ git grep quz
bad.txt:3:quz.baz=3
good.txt:3:quz.baz=foo
good2.txt:2:quz.baz=3

# this is the bad case: bad.txt is missing
macOS$ git grep quz.baz
good.txt:3:quz.baz=foo
good2.txt:2:quz.baz=3

# same thing on Linux works
linux$ git grep quz.baz
bad.txt:3:quz.baz=3
good.txt:3:quz.baz=foo
good2.txt:2:quz.baz=3
```

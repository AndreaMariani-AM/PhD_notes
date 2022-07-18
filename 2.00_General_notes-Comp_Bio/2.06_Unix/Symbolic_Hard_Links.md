
# Symbolic_Hard_Links
Topic: #Unix #ComputerScience 
Date: 2022-07-14

---

## Summary
This is a note on Sym and Hard links

## Notes
* When creating symlinks (ln -s) it super easy to create one that's broken. The error is :

```
"OSError: [Errno 40] Too many levels of symbolic links: path/to/link" with python "Too many levels of symbolic links" with find command *find -L -xtype l* in the dir of the symlink  
```

An easy fix to this is *ALWAYS* specify the full path for the source file. This prevents broken links.  

## Questions
- Item




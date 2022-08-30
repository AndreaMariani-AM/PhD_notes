
# Miscellaneous
Topic: #Unix #ComputerScience #Bionformatics 
Date: 2022-07-14

---

## Summary
This is a note containing usefull tips and tricks on Unix commands.

## Notes
  
* Cleaver way to remove header form a file (usually a bed):
```
tail -n +2 file.txt > file.stdout
```

- find files with the same name and remove them (helpful when snakemake stops and incomplete files are created)

```
find . -name "*partial_name*" | xargs rm -rf
```
- Kill open processes by PID name
```
lsof . +d
kill -9 PID_number
```
## Questions
- Item




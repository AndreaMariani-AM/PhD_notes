
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
- 
```
lsof . +d
kill -9 PID_number
```

- Look for a specific partial file name, take just some of the results (from 15 to 38) and copy them in another directory
```
find directory -name "*fastq.gz*" | sort | sed -n '15,38p' | xargs -I{} cp "{}" direcotry
```

- retrieve local IP address

```
ifconfig | grep "inet " | grep -Fv 127.0.0.1 | awk '{print $2}'
```
## Questions
- Item




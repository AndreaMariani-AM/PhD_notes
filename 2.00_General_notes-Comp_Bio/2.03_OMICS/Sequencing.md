
# Sequencing
Topic: #ComputatinalBiology #Bionformatics #Sequencing 
Date: 2022-09-22

---

## Summary
This is a note on various topics about the Sequencing *techniques*, *biases* and *other stuff *

## Notes
- In Pair End sequencing it's often confusing talking about *libray/insert/fragment size* , so we're gonna laid them out here. In  *PE* sequencing both *ends* of the *same* fragment are sequenced, as opposed to *SE* where only one end is sequenced. [Blog post here](https://thegenomefactory.blogspot.com/2013/08/paired-end-read-confusion-library.html)
	- If you think about a fragment of DNA being a line, PE seq starts from both ends and *not* covering the whole fragment length. The actual number of *unknown* bases between the two mates it's called *Inner Mate Distance* (*NOT* insert size).
	- The *Insert Size* is a piece of DNA inserted between the *adaptors* which enables the amplification and sequencing of that piece of DNA, and encompasses both *Mates* and the *Inner Mate Distance*. Can be negative if read *overlap*
	- *Fragment Size* is the computed/inferred size in *bp* of the fragment.

## Questions
- Item


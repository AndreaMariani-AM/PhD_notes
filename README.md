# Organization of the folders

## Introduction
This repo is free to use by anyone that wants to level up his/hers note taking game. This is a variation of the Zettelkasten method for note taking that seems to work well w/ Obsidian. I took inspo from [this YT video](https://www.youtube.com/watch?v=4T0q2kQwc2o&t=88s) and then made it my own. Feel free to use it in anyway you'd like. It's hosted here on Github to have it as backup and be ready for a simple pull. 

### Requirements

- Goes without saying that to see the true potential of this system and the linked notes, you have to download Obsidian, [link here](https://obsidian.md/).
- Customization is left to the user, a good place to start and that works very weel, at least IMO, is the community plugin [Sliding Panes (Andy's Mode)](https://github.com/deathau/sliding-panes-obsidian).
- Once Obsidian is downloaded and the customization part is done simply

```
git pull git@github.com:AndreaMariani-AM/PhD_notes.git
```
 and tell Obsidian to open it up as a Vault. Then, you're good to go.
 
 
## 0.00_References
In this dierctory there's inbox and reference metadata subdirectories

- *0.01_Inbox* : contains notes that are just the template with general info but empty on the main body. They stay there untill the paper is read and notes are taken. When it happens, then the note is moved to 0.002_References_meta. PDFs are not stored here.
- *0.02_Reference_meta* : contains notes for a specific paper. **ALL** file names must be have the same format:
	- AuthorsName_year
	This are the actual notes that have to be referenced in later notes.

## 0.10_Templates
In this directory i'm storing various templates, for now i only have two that seems to work well for pretty much any situation.

- *0.11_Template_research_paper* : contains a template for notes to be used in *0.00_References/0.01_Inbox* or *0.02_Reference_meta*.
- *0.12_Template_notes* : contains a template for general notes, ideally for MOCs on broader subjects or for *2.00_General_notes-Comp_Bio*.

## 1.00_Papers_List
In this directory and subdirectory i'll store the index (00_Index_papers) of the papers that have been read and taken notes on. Divided in topics, the index is linked back to its original note. There's also a section *ADD REFERENCE* that can be used as an inbox for papers to be read.

## 2.00_General_notes-Comp_Bio
This folder is central to the system, and contains notes related to Computational Bio and Bioinformatics on different subjects. Folders are:   
- *2.01_Definitions*  
- *2.02_Miscellaneous*  
- *2.03_OMICS*  
- *2.04_Softwares*  
- *2.05_Statistics*  
- *2.06_Unix*  
- *2.07_Math*  
- *2.08_NewTechnologies*  



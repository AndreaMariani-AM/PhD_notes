
# Nextflow
Topic: #Nextflow #Pipeline #ComputatinalBiology #WorkflowManager #DSL
Date: 2022-06-09


---

## Summary
Nextflow, much like snakemake, is a Domain Specific Language (DSL) used for pipelines. It's infact a workflow manager intended to organized various steps that need to be run for a bioinformatics experiment. This document contains alle the info as i'm migrating our pipelines from snakemake to nextflow

## Notes
- Starting new pipelines from nf-core templates to adhere to community guidelines
- Processes are connected via their outputs and inputs to other processes and run as soon as they receive an imput.
- *Process*: describe a task to be run, can be any language. They spawn a task for each complete input set, each task is run independently and cannot interact with the others. Define inputs and outputs for a task. Is the equivalent of :
```  
shell: 
	""" 
	software -params 
	""" 
``` 
in a snakemake rule.
- *Channel*: asynchronous queue that's is charge of passing data from one process to the otherr. Only way to do pass data from processes. Manipulate the flow of data
- *Workflow*: A workflow section is the interaction between processes is defined.
- *Workflow execution*: a process *defines* what command/script has to be executed and the *executor* determines how the script is actually run in that system (I.e. if local or HPC or cloud)
- *Pipeline parameters* are defined in the workflow as *params.input* in the workflow where *params* is the prefix and the *input* is a variable name accessed through *dot (.)* character. Allows you to change input at runtime via " --input " at command line or through a config file. 

## Channels
- How nextflow sends data around a workflow and connect processes via thei input and outputs.
- Can store multiple items like files or values, and number of items determines the how many times a processes wil run (n of tasks) using the channel as input.

## Tips and Tricks
- *Maps*: are the Groovy way of doing named lists
- *Closures*: block of code that can be passed as an argument to a function. 
```
example = { it * it}
```
`it` is an implicit variable provided inside closures, available when there's no explicity declared parameter and represents the value passed to the function when invoked. For a different name use variable -> syntax
```
example_2 = { num -> num * num}
```
- Store parameters to pass to a script in a *Parameter file* either in *JSON* or *YAML*
## Common Errors
- item

## Questions to be solved
- Item

## Material
- [Nextflow carpentries](https://carpentries-incubator.github.io/workflows-nextflow/index.html)
- [Learning Nextflow in 2022](https://www.nextflow.io/blog/2022/learn-nextflow-in-2022.html)
- [nf-core tutorials](https://nf-co.re/docs/usage/nextflow)
- Sequera labs tutorial [1](https://sateeshperi.github.io/nextflow_varcal/nextflow/)and [2](https://training.seqera.io/)
- [nf-core paper](https://www.nature.com/articles/s41587-020-0439-x)
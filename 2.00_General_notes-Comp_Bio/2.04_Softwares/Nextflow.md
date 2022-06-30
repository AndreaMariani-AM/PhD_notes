
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
- Two Channel types: *Queue* and *value*. In *queue* channels data is consumed to make input for a process/operator. Can be created in two ways: 
	-  As results of of a process (output)
	- Explicitly using channel factory methods `Channel.of` or `Channel.fromPath`
	In *value* channels the channels are bound to a single value, it's content it's not consumed. Useful for processes that need to reuse input form a channel, like a process that reuse a reference genome for different samples, or the same file multiple times inside the same process. Created with `Channel.value`
- Queue channels affects the termination of processes while value channels they do not.



## Processes
- How nextflow executes commands. Starts with the keyword *process* followed by the name of the process:
```
process INDEX {
	script:
	"""
	salmon index -t ${projectDir}../*.fa.gz \
	-i ../salmon_index \
	--kmerLen 38 \
	samtools index .bam
	myscript.py
	"""
}
```
This process would run once.
- To add the process inside a *workflow*, add a *worflow block* and call the process like a function
```
workflow {
	INDEX()
}
```
- *Definition Block* is the backbone of every process
```
process TEST{
	[ directives ] 
	input:
	< process input >
	output:
	< process output >
	when:
	< condition >
	Script/shell/exec:
	< script to be executed >
}
``` 
where directives are optional parameters that control the process (e.g ncpus).
- Nextflow uses the same syntax for variable substitutions *$variable*, however they need to be escaped with a `\` .
``` 
process VARIABLE{
	script:
	"""
	myvariable=$params.kmer
	salmon index ..... --kmer \$myvariable
	"""
}

params.kmer = 31

workflow{
	VARIABLE()
}
```
Remember that the *params.name* is the way to assign values form command line.
- If i use the *shell* instead of *script* then bash variables are referenced in the normal way *${variable}* and do not need to be escaped, while nextflow variable needs *!{projectDir}* for variable substitutions

## Inputs
- *Input block* defines which channels the process expects to received input from 
- It requires two declarations: input qualifier and name
```
input:
	<input qualifier> <input name>
```
Qualifier is the type of data to be received, read [here](https://carpentries-incubator.github.io/workflows-nextflow/05-processes-part1/index.html#input-qualifiers)
- Multiple input channels are allowd, and they match elements based on th position, like element `a` from A with `1` from B, and `b` from A with `2` form B and so on, where *A = [a,b]* and *B = [1, 2]*.
- In case of mulitple input channels, the number times a processes run is defined by the queue channel with the fewest items.

## Outputs
- *Output block* requires the same the same two declarations and allows us to declare channels used by the process to send out files.
```
output:
	<output qualifier> <output name>
```
-*Multiple output* files contains either `*` or `?` as a pattern match and this allows us to capture multiple output files into a list and output them as one item channel.
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
- Channel factory methods has  convenient `Channel.fromFilePairs`, creates a queue channel containing a tuplefor every set of files matching a glob.
- *Implicit variables* (e.g ${projectDir}) are useful, in this case, this one specifies the directory where the main script is located , it's important as nextflow scripts are executed in a separate workDir.
- *-process.echo* prints the output of some processes to the stoudt of the terminal, add it after *netxflow run -process.echo*
- When giving *associated scripts* to processes (e.g myscript.py), store them in a *bin* folder at the same directory level as the nextflow workflow script that invokes them and given execute permissions, nextfow will automatically add it to the *PATH* environment variable.

## Common Errors
- 

## Questions to be solved
- Item

## Material
- [Nextflow carpentries](https://carpentries-incubator.github.io/workflows-nextflow/index.html)
- [Learning Nextflow in 2022](https://www.nextflow.io/blog/2022/learn-nextflow-in-2022.html)
- [nf-core tutorials](https://nf-co.re/docs/usage/nextflow)
- Sequera labs tutorial [1](https://sateeshperi.github.io/nextflow_varcal/nextflow/)and [2](https://training.seqera.io/)
- [nf-core paper](https://www.nature.com/articles/s41587-020-0439-x)
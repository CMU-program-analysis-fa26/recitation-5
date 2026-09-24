09/27/24 Recitation
==================

17-355/17-665/17-819: Program Analysis (Fall 2026)
----------------------------------------------------

In this recitation, you will get hands-on experience on how to use Soot to analyze Java code.

The code presented in this repository uses Soot to perform Definitions Analysis, keeping a list of all variable definitions with their line numbers. In this recitation, we will consider how to extend it to keep track of just the most recent assignment of a variable (i.e., Reaching Definitions) by modifying the `flowThrough` method in `IntraDefsAnalysis`.

## Running the Code

1. Create a **fork** of this repository.
2. Open this repository using **GitHub Codespaces with the 4-core VM option**. 

Whenever you wish to run your implementation to see the results of your analysis on an example code, run `./gradlew test`.

## File Structure

`inputs.DefsTest` is the code we are analyzing.

`IntraDefsAnalysis`, extending Soot's `ForwardFlowAnalysis`, contains the code we're 
interested in changing.

## Tasks

First, **look through the `IntraDefsAnalysis` class**. What are the **ingredients of the analysis**? Look for the lattice, the definition of `sigma`, the definition of things like `Top` and `Bot`, and the flow function. 

Then, **modify the `IntraDefsAnalysis` class to instead perform Reaching Definitions analysis**. Recall the ingredients for the Reaching Definitions analysis (the `GEN`/`KILL` functions, the flow function, etc.)

## Dependencies

As of Feb 2022, the latest Soot release that works is v4.2.1, which depends on ASM 8.0.1
and uses a hard-coded ASM API version 8. This restricts analysis of class files that
are compiled with JDK 15 or earlier. So, we cannot do whole program analysis with Java 16
or higher, because the JDK library classes would be in a format that is unsupported by
ASM 8.0.1 and in turn Soot v4.2.1. Simply upgrading the ASM version to ASM 9.1 does not
fix this, because Soot v4.2.1 has hard-coded the use of ASM API version 8 in its use
of ASM ClassVisitor. 

## Resources

[Soot](http://soot-oss.github.io/soot/)

[ForwardFlowAnalysis Javadoc](https://www.sable.mcgill.ca/soot/doc/soot/toolkits/scalar/ForwardFlowAnalysis.html)

[A Survivor's Guide to Java Program Analysis with Soot](https://www.brics.dk/SootGuide/)

# Apache Spark SQL: An Introductory Workshop

![image](http://spark.apache.org/docs/1.0.1/img/spark-logo-100x40px.png)

Dean Wampler, Ph.D.<br/>
Typesafe<br/>
[dean.wampler@typesafe.com](mailto:dean.wampler@typesafe.com)<br/>
[@deanwampler](https://twitter.com/deanwampler)

## Introduction

This workshop focuses on the new [Spark SQL](http://spark.apache.org/docs/latest/sql-programming-guide.html) API, which integrates structured data and embedded SQL queries with normal Spark code. It even has a Hive integration module so you can query existing Hive tables, even create and delete them.

We pick up where my [Apache Spark: An Introductory Workshop](https://github.com/deanwampler/spark-workshop) left off, including the numbering used for the examples.

I'll assume you've already worked through that workshop and not repeat details about Spark basics.

## About Spark SQL

TBD. For now, see the [Spark SQL description](http://spark.apache.org/docs/latest/sql-programming-guide.html).

## Building and Testing

If you're using the [Typesafe Activator UI](http://typesafe.com/activator), search for `activator-spark` and install it in the UI. The code is built automatically. 

If you grabbed this workshop from [Github](https://github.com/deanwampler/activator-spark), you'll need to install `sbt` and use a command line to build and run the applications. In that case, see the [sbt website](http://www.scala-sbt.org/) for instructions on installing `sbt`.

To compile the code and run the tests, either use the Activator UI <a class="shortcut" href="#test">test</a> link or start `sbt` and enter `test` at the prompt.

Either way, the code is compiled and the tests are executed. They should pass without error. Note that tests are provided for all the exercises, except the *Spark Streaming* exercise, which uses multiple processes.

## Running the Exercises

Next, let's try running one of the exercises.

In Activator, use the <a class="shortcut" href="#run">run</a> panel, select the first exercise, `SparkSQL9`, in the bullet items under "Main Class", and click the "Start" button. The "Logs" panel shows some information. Note the `output` directories listed in the output. Use a file browser to find those directories to view the output written in those locations.

In `sbt`, enter `run`. It will present the same list of main classes. Enter the number for `SparkSQL9` to run it.

Note that the some exercises have package names with the word `solns`. They are solutions to the exercises.

## The Exercises

Here is a list of the exercises. In subsequent sections, we'll dive into the details for each one. Note that each name ends with a number, indicating the order in which we'll discuss and try them:

* **SparkSQL9:** Uses the SQL API to run basic queries over structured data, in this case, the same King James Version (KJV) of the Bible used in the previous workshop. (The `data` directory has a [README](data/README.html) that discusses the sources of the data files.) This script ends by writing data in the de-facto standard [Parquet](http://parquet.io) format that is increasingly popular in *Big Data* applications.
* **SparkSQLParquet10:** Demonstrates reading Parquet-formatted data, namely the data written in the previous example.
* **HiveSQL10:** A script that demonstrates interacting with Hive tables (we actually create one) in the Scala REPL!

Let's now work through these exercises...

## SparkSQL9

<a class="shortcut" href="#code/src/main/scala/spark/SparkSQL9.scala">SparkSQL9.scala</a> 

TODO

Reads and parses the King James Bible text, `kjvdat.txt`.

As in the previous *Spark Workshop*, command line options can be used to override the defaults. We'll have to use `sbt` from a command window to use this feature (rather than the *Activator UI*), and we'll have to use the `run-main` task, which lets us specify a particular `main` to run and optional arguments. 

The "\" characters in the following and subsequent command descriptions are used to indicate long lines that I wrapped to fit. Enter the commands on a single line without the "\". I use `[...]` to indicate optional arguments, and `|` to indicate alternative flags:

```
run-main spark.SparkSQL9 [ -h | --help] \ 
  [-i | --in | --inpath input] \ 
  [-o | --out | --outpath output] \ 
  [-m | --master master] \ 
  [-q | --quiet]
```

Where the options have the following meanings:

```
-h | --help     Show help and exit.
-i ... input    Read this input source (default: data/kjvdat.txt).
-o ... output   Write to this output location (default: output/verses.parquet).
-m ... master   local, local[k], etc. as discussed previously.
-q | --quiet    Suppress some informational output.
```

The options work the same as before, except we don't append a timestamp to the output path, because its contents will be read by the next exercise.

**NOTE:** Because we don't append a timestamp to the output path, you'll get a runtime error if the directory already exists. Just delete or rename the existing directory, or specify a different output path.

Code description TODO.

As before, there are suggested exercises at the end of the source file. Some solutions are provided in the `solns` source package.

## SparkSQLParquet10

<a class="shortcut" href="#code/src/main/scala/spark/SparkSQLParquet10.scala">SparkSQLParquet10.scala</a> 

TODO

Reads the Parquet output of the previous example and works with the data using the SQL API.

The command-line options are similar, but there is no output option as all results are printed to the console:

```
run-main spark.SparkSQLParquet10 [ -h | --help] \ 
  [-i | --in | --inpath input] \ 
  [-m | --master master] \ 
  [-q | --quiet]
```

Code description TODO.


## HiveSQL11

<a class="shortcut" href="#code/src/main/scala/spark/HiveSQL11.scala">HiveSQL11.scala</a> 

TODO

This is actually a script file, but you'll find it most useful if you start the `console` in SBT, then copy and paste the statements, to see what each one does. Then you can experiment with the API, especially if you already know Hive!.

Note that the Hive "metadata" is stored in a `megastore` directory created in the current working directory. This is written and managed by Hive's embedded [Derby SQL](http://db.apache.org/derby/) store, but is not a production configuration.

Code description TODO.


## Going Forward from Here

This template is not a complete Apache Spark SQL tutorial and the API is evolving rapidly. For example, built-in support for JSON-formatted data is being added in a subsequent release. To learn more, see the following:

* The Apache Spark [website](http://spark.apache.org/). 
* The Apache Spark SQL [Programming Guide](http://spark.apache.org/docs/latest/sql-programming-guide.html) API* [Talks from Spark Summit 2013](http://spark-summit.org/2013).
* ... and other references in my other *Spark Workshop*.

## For more about Typesafe:

* See [Typesafe Activator](http://typesafe.com/activator) to find other Activator templates.
* See [Typesafe](http://typesafe.com) for more information about our products and services. 


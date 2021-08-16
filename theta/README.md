# Installing

To install the required packages, run the following command.

```
./install.sh
```

You can change the version of MoNA installed by editing [spack.yaml](spack.yaml).
You can change where the required software is installed as well as
the name of the spack environment used by editing [settings.sh](settings.sh).

This command will clone [spack](https://github.com/spack/spack) and
[mochi-spack-packages](https://github.com/mochi-hpc/mochi-spack-packages),
create a spack environment using the [spack.yaml](spack.yaml) file,
then install all the necessary software.

# Running

```
qsub -n 128 ./job.qsub
```

You can change the number of nodes on which to run the experiments.
This number should be at least 128, though the `job.qsub` file can
be edited to use the debug-flat-quad queue instead and run on up to
8 nodes in this queue.

This command will submit a job that will produce a directory named
`logs-<jobid>` containing the results.

# Parsing results

The results can be parsed to produce either CSV data or a Markdown table
by calling the following command.

```
../util/parse-results --csv logs-<jobid> algorithm
```

For instance:

```
../util/parse-results --csv logs-123456789 bcast
```

or

```
../util/parse-results --md logs-123456789 bcast
```

# Make Files

A basic demonstration that creates files based on a list of sample ID's, then passes them to another process which prints the file contents to the terminal.

## Usage

Pipeline can be run using the included `Makefile` with the command:

```
make run
```

## Output

The terminal output should look like this:

```
$ make run
export NXF_VER="0.28.0" && \
	curl -fsSL get.nextflow.io | bash

      N E X T F L O W
      version 0.28.0 build 4779
      last modified 10-03-2018 12:13 UTC (07:13 EDT)
      cite doi:10.1038/nbt.3820
      http://nextflow.io


Nextflow installation completed. Please note:
- the executable file `nextflow` has been created in the folder: /Users/kellys04/projects/nextflow-demos/make-files
- you may complete the installation by moving it to a directory in your $PATH

./nextflow run main.nf
N E X T F L O W  ~  version 0.28.0
Launching `main.nf` [soggy_bardeen] - revision: 378236bf36
[warm up] executor > local
[fa/ab7fb7] Submitted process > make_file (Sample3)
[79/2f5a1d] Submitted process > make_file (Sample4)
[de/497a87] Submitted process > make_file (Sample1)
[a9/5c39f7] Submitted process > make_file (Sample2)
[44/f6c37f] Submitted process > print_file (Sample3.txt)
[ca/801394] Submitted process > print_file (Sample1.txt)
[3c/ab42ae] Submitted process > print_file (Sample2.txt)
[e9/b0be40] Submitted process > print_file (Sample4.txt)
[print_file] contents of Sample3.txt: [print_sample] Sample3
[print_file] contents of Sample1.txt: [print_sample] Sample1
[print_file] contents of Sample2.txt: [print_sample] Sample2
[print_file] contents of Sample4.txt: [print_sample] Sample4
```

The files created are stored in the `work` directory generated by Nextflow:

```
$ tree work/
work/
|-- 3c
|   `-- ab42ae76f57b34d4145d632a8b29a9
|       `-- Sample2.txt -> /Users/kellys04/projects/nextflow-demos/make-files/work/a9/5c39f7eb3148d524f3b8c54f54a702/Sample2.txt
|-- 44
|   `-- f6c37ff80857163b49175330810911
|       `-- Sample3.txt -> /Users/kellys04/projects/nextflow-demos/make-files/work/fa/ab7fb7a962496400ac211346d08fef/Sample3.txt
|-- 79
|   `-- 2f5a1de8657e358c49235223f9375c
|       `-- Sample4.txt
|-- a9
|   `-- 5c39f7eb3148d524f3b8c54f54a702
|       `-- Sample2.txt
|-- ca
|   `-- 801394ef14224a7aee541fb4eae522
|       `-- Sample1.txt -> /Users/kellys04/projects/nextflow-demos/make-files/work/de/497a87eae301c140fa8742acbd2dd7/Sample1.txt
|-- de
|   `-- 497a87eae301c140fa8742acbd2dd7
|       `-- Sample1.txt
|-- e9
|   `-- b0be40d95df263947ca30dc9ed28fe
|       `-- Sample4.txt -> /Users/kellys04/projects/nextflow-demos/make-files/work/79/2f5a1de8657e358c49235223f9375c/Sample4.txt
`-- fa
    `-- ab7fb7a962496400ac211346d08fef
        `-- Sample3.txt

16 directories, 8 files
```
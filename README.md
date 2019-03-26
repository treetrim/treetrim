# treetrim
This is a command line tool that trims your source code tree. It removes debug files, source control bindings, and temporary files.

An example would be:

`treetrim.console.exe c:\my\tree -deletefromdisk`

This would delete the debug files and folders in `c:\my\tree`

---

This tool is based on the excellent [CleanSourcesPlus](https://blog.codinghorror.com/clean-sources-plus/) project.

It can compress, email, or copy the output. The tool is plugin based so can be extended to include whatever functionality you wish. It can be included as a task in your CI environment.

## Examples of the command line

Here are some examples of the command line:

`treetrim.console c:\my\tree -deletefromdisk`

This removes the debug files and folders found in your source tree

`treetrim.console c:\my\tree -workingcopy -deletefromdisk`

This makes a working copy and removes the debug files and folders _from the working copy_.

`treetrim.console c:\my\tree -workingcopy -deletefromdisk -zip:writeTo:c:\out.zip`

This makes a working copy, removes the debug stuff, and writes the output to zipped file.

`treetrim.console c:\my\tree -workingcopy -deletefromdisk -zip -email`

This makes a working copy, removes the debug stuff, zips it up in a temporary file, and emails it.

---

The order of the _tasks_ on the command line dictates the order in which the items are run. _workingcopy_ is a _task_ - it makes a working copy. _zip_ is a task - it compresses the output of the previous task.

The output from one task is the input to the next task. In the example above, it went: 

```
* make a working copy * remove the debug -- in the temporary folder that the previous task created * zip it -- zips the contents of that folder * email it -- emails the content of the previous task, which is a zip file
```

Please also take a look at [Tree Trim discussion group](http://groups.google.com/group/treetrim).

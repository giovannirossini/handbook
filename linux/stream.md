# Stream Flow

In Linux, `stdin` is the default input stream. It accepts text as input. Text output from the delivered command to the shell through `stdout` flow (standard output). Error messages from the given command via the `stderr` flow (standard error).

The standard terminal channels in Linux are 3: stdin, stdout, and stderr where the first is for input stream and the latters for output and error streams.
By default the successful command results are outputted to stdout (equivalent to >). You can explicity redirect to stdout or stderr as follows:
```shel
$ echo "hi there!" 1> error_log.txt
$ cat ~/incorrect-path 2> error_log.txt
## To both:
$ (echo "hi" && cat ~/wrong) >> log.txt 2>&1
```
To discard output stream, redirect it to the special directory `/dev/null`.

-  : stdin
- 1 : stdout
- 2 : stderr

## Examples


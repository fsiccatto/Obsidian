# File Descriptors and Redirections
By default, the first three file descriptors in Linux are:

1. Data Stream for Input
    - `STDIN – 0`
2. Data Stream for Output
    - `STDOUT – 1`
3. Data Stream for Output that relates to an error occurring.
    - `STDERR – 2`
#### STDIN and STDOUT
When running `cat`, we give the running program our standard input (`STDIN - FD 0`). As soon as we have confirmed our input with `[ENTER]`, it is returned to the terminal as standard output (`STDOUT - FD 1`).
#### STDOUT and STDERR
By using the `find` command, we will see the standard output (`STDOUT - FD 1`) marked in `green` and standard error (`STDERR - FD 2`) marked in red.

We can check this by redirecting the file descriptor for the errors (`FD 2 - STDERR`) to "`/dev/null`." This way, we redirect the resulting errors to the "null device," which discards all data.
#### Redirect STDOUT to a File
```bash
fsiccatto@htb[/htb]$ find /etc/ -name shadow 2>/dev/null > results.txt
```
#### Redirect STDOUT and STDERR to Separate Files
We should have noticed that we did not use a number before the greater-than sign (`>`) in the last example. That is because we redirected all the standard errors to the "`null device`" before, and the only output we get is the standard output (`FD 1 - STDOUT`). To make this more precise, we will redirect standard error (`FD 2 - STDERR`) and standard output (`FD 1 - STDOUT`) to different files.
```bash
fsiccatto@htb[/htb]$ find /etc/ -name shadow 2> stderr.txt 1> stdout.txt
```
#### Pipes
Another way to redirect `STDOUT` is to use pipes (`|`). These are useful when we want to use the `STDOUT` from one program to be processed by another. One of the most commonly used tools is `grep`, which we will use in the next example. Grep is used to filter `STDOUT` according to the pattern we define. In the next example, we use the `find` command to search for all files in the "`/etc/`" directory with a "`.conf`" extension. Any errors are redirected to the "`null device`" (`/dev/null`). Using `grep`, we filter out the results and specify that only the lines containing the pattern "`systemd`" should be displayed.
```bash
fsiccatto@htb[/htb]$ find /etc/ -name *.conf 2>/dev/null | grep systemd
```
we can add `| wc -l` which should count the total number of obtained results
```bash
fsiccatto@htb[/htb]$ find /etc/ -name *.conf 2>/dev/null | grep systemd | wc -l
```
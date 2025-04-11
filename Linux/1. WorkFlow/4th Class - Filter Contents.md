# Filter Contents
## More
```bash
fsiccatto@htb[/htb]$ cat /etc/passwd | more
```

The `/etc/passwd` file in Linux is like a phone directory for users on the system. It includes details such as the username, user ID, group ID, home directory, and the default shell they use.

After we read the content using `cat` and redirected it to `more`, the already mentioned `pager` opens, and we will automatically start at the beginning of the file.
With the `[Q]` key, we can leave this `pager`. We will notice that the output remains in the terminal.

## Less
If we now take a look at the tool `less`, we will notice on the man page that it contains many more features than `more`.
```bash
fsiccatto@htb[/htb]$ less /etc/passwd
```

## Head
Sometimes we will only be interested in specific issues either at the beginning of the file or the end. If we only want to get the `first` lines of the file, we can use the tool `head`. By default, `head` prints the first 10 lines of the given file or input, if not specified otherwise.
```bash
fsiccatto@htb[/htb]$ head /etc/passwd
```

## Tail
If we only want to see the last parts of a file or results, we can use the counterpart of `head` called `tail`, which returns the `last` ten lines.
```bash
fsiccatto@htb[/htb]$ tail /etc/passwd
```

## Sort
Often it is necessary to sort the desired results alphabetically or numerically to get a better overview. For this, we can use a tool called `sort`.
```bash
fsiccatto@htb[/htb]$ cat /etc/passwd | sort
```

## Grep
In many cases, we will need to search for specific results that match patterns we define. Grep provides a wide range of powerful features for pattern searching.
```bash
fsiccatto@htb[/htb]$ cat /etc/passwd | grep "/bin/bash"

root:x:0:0:root:/root:/bin/bash
mrb3n:x:1000:1000:mrb3n:/home/mrb3n:/bin/bash
cry0l1t3:x:1001:1001::/home/cry0l1t3:/bin/bash
htb-student:x:1002:1002::/home/htb-student:/bin/bash
```

This is just one example of how grep can be applied to efficiently filter data based on predefined patterns. Another possibility is to exclude specific results. For this, the option "`-v`" is used with `grep`. In the next example, we exclude all users who have disabled the standard shell with the name "`/bin/false`" or "`/usr/bin/nologin`"
```bash
fsiccatto@htb[/htb]$ cat /etc/passwd | grep -v "false\|nologin"

root:x:0:0:root:/root:/bin/bash
sync:x:4:65534:sync:/bin:/bin/sync
postgres:x:111:117:PostgreSQL administrator,,,:/var/lib/postgresql:/bin/bash
user6:x:1000:1000:,,,:/home/user6:/bin/bash
```
La barra `\` significa que `|` no es un caracter como tal, sino que hace alusión a 'o'.

## Cut
Specific results with different characters may be separated as delimiters. Here it is handy to know how to remove specific delimiters and show the words on a line in a specified position. One of the tools that can be used for this is `cut`. Therefore we use the option "`-d`" and set the delimiter to the colon character (`:`) and define with the option "`-f`" the position in the line we want to output.
```bash
fsiccatto@htb[/htb]$ cat /etc/passwd | grep -v "false\|nologin" | cut -d":" -f1

root
sync
postgres
mrb3n
cry0l1t3
htb-student
```

## Tr
Another possibility to replace certain characters from a line with characters defined by us is the tool `tr`. As the first option, we define which character we want to replace, and as a second option, we define the character we want to replace it with. In the next example, we replace the colon character with space.
```bash
fsiccatto@htb[/htb]$ cat /etc/passwd | grep -v "false\|nologin" | tr ":" " "

root x 0 0 root /root /bin/bash
sync x 4 65534 sync /bin /bin/sync
postgres x 111 117 PostgreSQL administrator,,, /var/lib/postgresql /bin/bash
mrb3n x 1000 1000 mrb3n /home/mrb3n /bin/bash
cry0l1t3 x 1001 1001  /home/cry0l1t3 /bin/bash
htb-student x 1002 1002  /home/htb-student /bin/bash
```

## Column
Since search results can often have an unclear representation, the tool `column` is well suited to display such results in tabular form using the "`-t`."
```bash
fsiccatto@htb[/htb]$ cat /etc/passwd | grep -v "false\|nologin" | tr ":" " " | column -t

root         x  0     0      root               /root        		 /bin/bash
sync         x  4     65534  sync               /bin         		 /bin/sync
postgres     x  111   117    PostgreSQL         administrator,,,    /var/lib/postgresql		/bin/bash
mrb3n        x  1000  1000   mrb3n              /home/mrb3n  	     /bin/bash
cry0l1t3     x  1001  1001   /home/cry0l1t3     /bin/bash
htb-student  x  1002  1002   /home/htb-student  /bin/bash
```

## Awk
As we may have noticed, the line for the user "`postgres`" has one column too many. To keep it as simple as possible to sort out such results, the (`g`)`awk` programming is beneficial, which allows us to display the first (`$1`) and last (`$NF`) result of the line.
```bash
fsiccatto@htb[/htb]$ cat /etc/passwd | grep -v "false\|nologin" | tr ":" " " | awk '{print $1, $NF}'

root /bin/bash
sync /bin/sync
postgres /bin/bash
mrb3n /bin/bash
cry0l1t3 /bin/bash
htb-student /bin/bash
```

## Sed
There will come moments when we want to change specific names in the whole file or standard input. One of the tools we can use for this is the stream editor called `sed`. One of the most common uses of this is substituting text. Here, `sed` looks for patterns we have defined in the form of regular expressions (regex) and replaces them with another pattern that we have also defined. Let us stick to the last results and say we want to replace the word "`bin`" with "`HTB`."

The "`s`" flag at the beginning stands for the substitute command. Then we specify the pattern we want to replace. After the slash (`/`), we enter the pattern we want to use as a replacement in the third position. Finally, we use the "`g`" flag, which stands for replacing all matches.
```bash
fsiccatto@htb[/htb]$ cat /etc/passwd | grep -v "false\|nologin" | tr ":" " " | awk '{print $1, $NF}' | sed 's/bin/HTB/g'

root /HTB/bash
sync /HTB/sync
postgres /HTB/bash
mrb3n /HTB/bash
cry0l1t3 /HTB/bash
htb-student /HTB/bash
```


## Wc
To avoid counting the lines or characters manually, we can use the tool `wc`. With the "`-l`" option, we specify that only the lines are counted.
```bash
fsiccatto@htb[/htb]$ cat /etc/passwd | grep -v "false\|nologin" | tr ":" " " | awk '{print $1, $NF}' | wc -l

6
```

## Ejemplo
```bash
ss -l -4 | grep -v "127\.0\.0" | grep "LISTEN"
```
1. **`ss -l -4`**: Muestra sockets **escuchando** (`-l`) usando **IPv4** (`-4`).
2. **`grep -v "127\.0\.0"`**:
	- `grep -v`: excluye las líneas que coincidan.
	- `"127\.0\.0"`: busca direcciones en el **loopback local** (localhost).
	- El **`\.`** es necesario para que `.` no se interprete como _cualquier carácter_ en la expresión regular. Es decir, `127.0.0` literalmente.
##### Localhost
- **`localhost`** es un nombre que apunta a la IP **`127.0.0.1`**.
- Es la forma en que una máquina se refiere a **sí misma**.
- Solo puede ser accedido **desde la misma máquina**, **no desde otras computadoras**.
Significa que un servicio (como una base de datos, un servidor web, etc.) está **escuchando solo en `127.0.0.1`**, por lo tanto:
✅ Puede ser accedido desde esa misma máquina.  
❌ No puede ser accedido desde otra PC en la red o desde internet.

Supongamos que tenés un servidor MySQL.
- Si está escuchando en `127.0.0.1:3306`, solo podés conectarte **desde tu propia máquina**.
- Si está en `0.0.0.0:3306`, acepta conexiones desde **cualquier IP**, incluso otras máquinas en tu red o desde internet (si está permitido por firewall).
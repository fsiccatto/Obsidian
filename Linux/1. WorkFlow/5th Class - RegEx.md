## Grouping

Among other things, regex offers us the possibility to group the desired search patterns. Basically, regex follows three different concepts, which are distinguished by the three different brackets:

| **Operators** | **Description**                                                                                                                                                             |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `(a)`         | The round brackets are used to group parts of a regex. Within the brackets, you can define further patterns which should be processed together.                             |
| `[a-z]`       | The square brackets are used to define character classes. Inside the brackets, you can specify a list of characters to search for.                                          |
| `{1,10}`      | The curly brackets are used to define quantifiers. Inside the brackets, you can specify a number or a range that indicates how often a previous pattern should be repeated. |
| `\|`          | Also called the OR operator and shows results when one of the two expressions matches                                                                                       |
| `.*`          | Operates similarly to an AND operator by displaying results only when both expressions are present and match in the specified order                                         |
 In the next example, we search for lines containing the word `my` or `false`. To use these operators, you need to apply the extended regex using the `-E` option in grep.
### OR operator
```bash
cry0l1t3@htb:~$ grep -E "(my|false)" /etc/passwd

lxd:x:105:65534::/var/lib/lxd/:/bin/false
pollinate:x:109:1::/var/cache/pollinate:/bin/false
mysql:x:116:120:MySQL Server,,:/nonexistent:/bin/false
```
#### AND operator

```bash
cry0l1t3@htb:~$ grep -E "(my.*false)" /etc/passwd

mysql:x:116:120:MySQL Server,,:/nonexistent:/bin/false
```
Basically, what we are saying with this command is that we are looking for a line where we want to see both `my` and `false`. A simplified example would also be to use `grep` twice and look like this:

```bash
cry0l1t3@htb:~$ grep -E "my" /etc/passwd | grep -E "false"

mysql:x:116:120:MySQL Server,,:/nonexistent:/bin/false
```

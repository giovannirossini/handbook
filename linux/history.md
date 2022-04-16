# History 

History is able to keep track of any written lines and utilize information from previous lines in composing new ones.

## References

We can reference to a command line entry in the history list from the last typed to the first one.  
A `!` start a history reference:

- `!! `: Refer to the previous command.  This is the same as `!1`.

```shell
$ echo "1st command"
1st command
$ !!
$ echo "1st command"
```

- `!n`: Refer to command line n.

```shell
$ history
  1  echo "1st command"
  2  watch free -h
  3  df -h
$ !2
$ watch free -h
```

- `!-n`: Refer to the current command minus n.

```shell
$ history
  1  echo "1st command"
  2  watch free -h
  3  df -h
$ !-2
$ echo "1st command"
```

- `!string`: Refer to the most recent command preceding the current position in the history list starting with string.

```shell
$ history
  1  echo "1st command"
  2  watch free -h
  3  df -h
$ !watch
$ watch free -h
```

- `!*`: Refer to the most recent command getting all the arguments from the previous command.

```shell
$ car .bash_history | grep -v 'history'
bash: car: command not found
$ cat !*
$ cat .bash_history | grep -v 'history'
```

- `!str:n`: Refer to the most recent command that contains str and get the nth argument. You can use $ to get the last argument.

```shell
             1      2   3   4     5     6   7   8   9
$ cat .bash_history | grep -v 'history' | grep -o [0-9]
  1
  2
  3
$ history | grep !cat:8 !cat:9 or !cat:$
$ history | grep -o [0-9]
```

## Quick Substitution

We also can use the history substitution feature to replace the last command with the one before it.


- `^str1^str2^`   Repeat the last command, replacing `str1` with `str2`.
  
```shell
$ if [[ $PDW ]]; then echo "$PWD"; fi
$ ^PDW^PWD^
$ if [[ $PWD ]]; then echo "$PWD"; fi
/
```
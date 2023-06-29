# Requirements 

- python 3.10.6 (perhaps it works with older versions too)
- tested on ubuntu 22.04

# Usage
```bash 
python3 ./cli.py [--debug] [-d,--decode]
```
This scripts reads alle text from **stdin** and outputs the invisible unicode ecoded text to **stdout**.

# Example script 

```console
foo@bar:~$ invisible=$(echo "This should be invisible!" | python3 ./cli.py)
foo@bar:~$ echo "$invisible"

foo@bar:~$ echo "$invisible" | python3 ./cli.py -d
This should be invisible!
```

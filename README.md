# Hide your messages 

This command line tool allows encoding text into an invisible and zero width subset of Unicode characters.
Specific Unicode symbols may be rendered inconsistently by different programs or platforms.
The set of invisible unicode characters can be adjusted in the source code.
The default set has been tested at `PopOS 22.04`.

# How the encoding works
1. First, we convert the input text into base `n-1` representation.
2. Then we map each digit `d` to the `d-th` character inside the list of invisible characters.
3. Finally, we insert between each base `n-1` number the `n-th` invisible character as separator.

Decoding can be achieved by following these steps in reverse.

Using the `n-th` base instead of just `2` allows a compacter representation.

# Requirements 

- python 3.10.6
- tested on Ubuntu 22.04
- Bash scripts require `xclip`, on Ubuntu you can install it by `sudo apt install xclip`

# setup 
- `git clone https://github.com/DerBrunoIR/Translator`
- `cd ./Translator`

# encode/decode messages via bash script


```console 
foo@bar:~$ ./write
Some hidden text
❯ stdout copied to clipboard!
foo@bar:~$ ./read 
[Ctrl-V]⁥⁠͏​‏͏​‍͏​⁤­͏‎﻿͏​𝅶͏​⁤͏
❯ Some hidden text
```

# encode/decode messages via python script 
> [!warning]
> In certain environment, like windows, unicode stdin and stdout might not work.

```console
foo@bar:~$ echo "This should be invisible!" | python3 ./cli.py > out.txt
foo@bar:~$ cat out.txt
❯ Start:͏‌‌‏​⁠؜⁠​⁠﻿⁠​‏‌​‌‏؜​⁠؜⁠​⁠﻿⁠​⁠؜‌​‌‍‍​‏‌​‌‍﻿​‏‌​⁠﻿﻿​‌‍‏​‌‍⁠​⁠﻿؜​‌‍‏​⁠﻿‌​‌‍‏​﻿‍‎:End # Try to move your cursor through this output.
foo@bar:~$ cat out.txt | python3 ./cli.py -d
>>> This should be invisible!
```

# known issues

Text rendering is application specific.

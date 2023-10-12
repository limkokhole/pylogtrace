# PyLogTrace
Tracing a Python Program from a Log Perspective  

This is a modified version of the `trace` module from Python3.  

Sometimes, we need to determine which source code line (file + line) produced a particular output log. This helps in understanding, learning, and debugging a program quickly and accurately. This script displays the code stacks associated with the output log, minimizing noise.  

The script only prints stacks related to the output (e.g., `.write`, `logging`, `print`, `cprint`) of the program, rather than a full, noisy trace.  

Low-level logging and trace logs are also omitted to reduce noise.  

Each log is associated with a stack, termed "a round," labeled with an index `#1-N`. The script marks a line with `[ EQU ]` if it duplicates the previous round (where `#` represents the specific line of that stack). Conversely, lines are marked as `[ NEW ]`.  

### Example Usage:

    $ python3 -u /tmp/pylogtrace.py --trace -g -t hello.py
    $ python3 -u /tmp/pylogtrace.py --trace -g -t --module pip install non_exist_package_name -vvv
    $ python3 -u /tmp/pylogtrace.py --trace -g -t /home/xiaobai/.local/bin/you-get 'https://www.youtube.com/watch?v=4vQ8If7f374'
    $ python3 -u /tmp/pylogtrace.py --trace -g -t ~/Downloads/youtube-dl/3/bin/youtube-dl -i -c --no-mtime -o './%(title)s-%(upload_date)s-%(id)s.%(ext)s' 'https://www.youtube.com/watch?v=4vQ8If7f374'

If you encounter a `No module named` error, ensure that you resolve the script path. For example, you should run `/usr/share/streamlink/streamlink` instead of `/usr/bin/streamlink`:  

    $ type -a streamlink
    streamlink is /usr/bin/streamlink
    $ realpath /usr/bin/streamlink
    /usr/share/streamlink/streamlink

### Demo Screenshot  
##### (Attempting to install a non-existent package with pip will result in an error. This script lets you quickly pinpoint the exact source code file and line responsible, helping you understand why the pip installation failed. Btw, if you want more detailed output from pip itself, use the `-vvv` flag.)  

 ![Trace pip error](https://1.bp.blogspot.com/-Mg9YUbUClEM/YCBLU4TMfdI/AAAAAAAAv9Y/QqXphACEQggtU6zVI8fcJvk693sJWrdvwCLcBGAsYHQ/s1366/1612729092_2021-02-08_FsUeEqfhGE.png "Trace pip error")

...

 ![Trace pip error 2](https://1.bp.blogspot.com/-e_7CnkHSkZ0/YCBLiKqeP5I/AAAAAAAAv9c/lZxNQJks4rAyokuzjkGotEela1XVYBOnACLcBGAsYHQ/s1006/1612729104_2021-02-08_nMwiCVGIsl.png "Trace pip error 2")

`#2 [ EQU] == Previous #8 - #10` indicates that the current log stack range from `#2` to `#4` is equivalent to the previous log stack range from `#8` to `#10`. Above this, the `[ NEW ]` label denotes new log stacks in this round compared to the previous round. This labeling makes it easier to discern the variations between each log entry.  

### Demo video (Click image to play at YouTube):

[![watch in youtube](https://i.ytimg.com/vi/LjOyqPW4p8U/hqdefault.jpg)](https://www.youtube.com/watch?v=LjOyqPW4p8U "PyLogTrace")

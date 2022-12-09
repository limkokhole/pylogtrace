# PyLogTrace
Trace python program from log perspective.

This is modified version of trace module of python3.

Sometime we need to know the log from which line of the source code in order to learn and debug a program quickly. This script show the code stacks tied with the output log with minimized noisiness.

This script only print stack related to output(i.e. `.write`, `logging`, `print`, `cprint`) of program
, instead of whole bunch of noisiness trace.

It also skips low level of logging and trace log to reduce noise.

It also mark [ EQU ] if specific line is duplicated with the previous round (# is the number of line of specific stack). Mark line as [ NEW ] conversely.

### Example Usage:

    $ python3 -u /tmp/pylogtrace.py --trace -g -t hello.py
    $ python3 -u /tmp/pylogtrace.py --trace -g -t --module pip install non_exist_package_name -vvv
    $ python3 -u /tmp/pylogtrace.py --trace -g -t /home/xiaobai/.local/bin/you-get 'https://www.youtube.com/watch?v=4vQ8If7f374'
    $ python3 -u /tmp/pylogtrace.py --trace -g -t ~/Downloads/youtube-dl/3/bin/youtube-dl -i -c --no-mtime -o './%(title)s-%(upload_date)s-%(id)s.%(ext)s' 'https://www.youtube.com/watch?v=4vQ8If7f374'

And ensure resolve the script path if you get `No module named` error, e.g. you should run with `/usr/share/streamlink/streamlink` instead of `/usr/bin/streamlink`:  

    $ type -a streamlink
    streamlink is /usr/bin/streamlink
    $ realpath /usr/bin/streamlink
    /usr/share/streamlink/streamlink

### Demo Screenshot 
##### (pip install non existent package will throws error, with the help of this script, we can quickly know the error in which source code file+line to know the reason of pip installation failed. Btw, you can use pip -vvv to get verbose output):

 ![Trace pip error](https://1.bp.blogspot.com/-Mg9YUbUClEM/YCBLU4TMfdI/AAAAAAAAv9Y/QqXphACEQggtU6zVI8fcJvk693sJWrdvwCLcBGAsYHQ/s1366/1612729092_2021-02-08_FsUeEqfhGE.png "Trace pip error")

...

 ![Trace pip error 2](https://1.bp.blogspot.com/-e_7CnkHSkZ0/YCBLiKqeP5I/AAAAAAAAv9c/lZxNQJks4rAyokuzjkGotEela1XVYBOnACLcBGAsYHQ/s1006/1612729104_2021-02-08_nMwiCVGIsl.png "Trace pip error 2")

### Demo video (Click image to play at YouTube):

[![watch in youtube](https://i.ytimg.com/vi/LjOyqPW4p8U/hqdefault.jpg)](https://www.youtube.com/watch?v=LjOyqPW4p8U "PyLogTrace")

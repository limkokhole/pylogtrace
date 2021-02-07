# PyLogTrace
Trace python program from log perspective.

This is modified version of trace module of python3.

Log alone itself provide little value, we need to know where the log come from. 

This script only print stack related to output(i.e. `.write`, `logging`, `print`, `cprint`) of program
, instead of whole bunch of useless trace.

It also skips low level of logging and trace log to reduce noise.

It also mark [ EQU ] if specific line is duplicated with the previous round (# is the number of line of specific stack). Mark line as [ NEW ] conversely.

### Example Usage:

    $ python3 -u /tmp/pylogtrace.py --trace -g -t hello.py
    $ python3 -u /tmp/pylogtrace.py --trace -g -t --module pip install non_exist_package_name -vvv
    $ python3 -u /tmp/pylogtrace.py --trace -g -t /home/xiaobai/.local/bin/you-get 'https://www.youtube.com/watch?v=4vQ8If7f374'
    $ python3 -u /tmp/pylogtrace.py --trace -g -t ~/Downloads/youtube-dl/3/bin/youtube-dl -i -c --no-mtime -o './%(title)s-%(upload_date)s-%(id)s.%(ext)s' 'https://www.youtube.com/watch?v=4vQ8If7f374'

### Demo video (Click image to play at YouTube):

[![watch in youtube](https://i.ytimg.com/vi/LjOyqPW4p8U/hqdefault.jpg)](https://www.youtube.com/watch?v=LjOyqPW4p8U "PyLogTrace")

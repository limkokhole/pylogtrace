# pylogtrace
Trace python program from log perspective.

This is modified version of trace module of python3.

### Example Usage:

    $ python3 -u /tmp/pylogtrace.py --trace -g -t hello.py
    $ python3 -u /tmp/pylogtrace.py --trace -g -t --module pip install non_exist_package_name -vvv
    $ python3 -u /tmp/pylogtrace.py --trace -g -t /home/xiaobai/.local/bin/you-get 'https://www.youtube.com/watch?v=4vQ8If7f374'
    $ python3 -u /tmp/pylogtrace.py --trace -g -t ~/Downloads/youtube-dl/3/bin/youtube-dl -i -c --no-mtime -o './%(title)s-%(upload_date)s-%(id)s.%(ext)s' 'https://www.youtube.com/watch?v=4vQ8If7f374'

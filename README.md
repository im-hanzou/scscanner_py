# scscanner_py
scscanner_py is tool to read website status code response from the lists. This tool is reworked from bash version of [scscanner](https://github.com/yuyudhn/scscanner).

## Requirements
- requests
- urllib3
- datetime
- argparse

Tested on **Debian** with **Python 3.10.8**

## How to use
Help menu.
```
┌──(miku㉿nakano)-[~/scscanner]
└─$ python3 scscanner.py --help

┏━━┳━━┳━━┳━━┳━━┳━┓┏━┓┏━━┳━┓
┃━━┫┏━┫━━┫┏━┫┏┓┃┏┓┫┏┓┫┃━┫┏┛
┣━━┃┗━╋━━┃┗━┫┏┓┃┃┃┃┃┃┃┃━┫┃
┗━━┻━━┻━━┻━━┻┛┗┻┛┗┻┛┗┻━━┻┛
    scscanner - Massive HTTP Status Code Scanner
    
usage: scscanner.py [-h] [-T list.txt] [-w [15]] [-t google.com] [-f 200] [-s]

options:
  -h, --help            show this help message and exit
  -T list.txt           File contain lists of domain
  -w [15], --workers [15]
                        Thread value. Default value is 4
  -t google.com, --target google.com
                        Single domain check
  -f 200, --filter 200  Status code filter
  -s, --silent          Silent mode option. Don't print status code output
```
Scan domain lists.
```
┌──(miku㉿nakano)-[~/scscanner]
└─$ python3 scscanner.py -T lists.txt -w 20

2022-11-23 22:08:47 - Start program

[301] - https://linuxsec.org --> https://www.linuxsec.org/
[200] - https://www.trustpilot.com/review/linuxsec.org
[200] - https://praktikum-posa.github.io/praktikum-satu/
[200] - https://randomsarl.com
[404] - https://baliuagu.edu.ph/sss
[302] - https://www.webtools.link --> https://www.webtools.link/en
......
2022-11-23 22:08:47 - Run complete
```
Scan domain list with status code filtering
```
┌──(miku㉿nakano)-[~/scscanner]
└─$ python3 scscanner.py -T lists.txt -w 20 -f 200

2022-11-23 22:11:34 - Start program

[200] - https://www.trustpilot.com/review/linuxsec.org
[200] - https://urlwebsite.com/id/cost/linuxsec.org
[200] - https://vymaps.com/ID/Linuxsec-1188705737924736/
[200] - https://praktikum-posa.github.io/praktikum-satu/
......
[200] - https://id.pinterest.com/linuxsec/
[200] - http://www.xentaos.com/p/review.html

2022-11-23 22:11:34 - Run complete
```
Silent option, just print url with match status code filter.
```
┌──(miku㉿nakano)-[~/scscanner]
└─$ python3 scscanner.py -T lists.txt -s --filter 200 --worker 20
https://praktikum-posa.github.io/praktikum-satu/
https://www.trustpilot.com/review/linuxsec.org
https://id.scribd.com/document/328681525/Www-Linuxsec-Org-2016-05-Routersploit-HTML
https://vymaps.com/ID/Linuxsec-1188705737924736/
http://www.xentaos.com/p/review.html
...
```

## Screenshot
![scscanner](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg8vq_xnWyaZT-RB5gbdbsuiI7yd5DtDXlsNr2J51htqvtOkWc92y_TA9TF73t4fb0lUoq7srKOKwnKrPdlZmbx5ZCLeW3zeO_yE-cuOTE1hNLgpd2Al9uraODHv_0pv1H6-pG7oeHZi3WhvBBWgBPqTpa4AYCYbBLllNnVKGzdW4OLvD__5jrHL7Tzcw/s917/scscanner.png "scscanner")

## Disclaimer
I am just learning **ThreadPoolExecutor** so maybe this tool is dirty implementation of python threading. Feel free to contribute for better code quality.

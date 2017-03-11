# MrRAT

This is a cross-platform Python 2.x Remote Access Trojan (RAT), MrRAT was created to maintain a clean design full-featured Python RAT. Currently a work in progress and still being actively hacked on.

**Disclaimer: This RAT is for research purposes only, and should only be used on authorized systems. Accessing a computer system or network without authorization or explicit permission is illegal.**

## Features
* Cross-platform (Windows, Linux, and macOS)
* AES GCM encrypted C2 with D-H exchange
* Accepts connection from multiple clients
* Command execution
* File upload/download (a bit buggy since crypto change)
* Standard utilities (wget, unzip)
* System survey

## Usage
```
$ python MrRAT_server.py --port 1337

 /$$      /$$           /$$$$$$$   /$$$$$$  /$$$$$$$$
| $$$    /$$$          | $$__  $$ /$$__  $$|__  $$__/
| $$$$  /$$$$  /$$$$$$ | $$  \ $$| $$  \ $$   | $$
| $$ $$/$$ $$ /$$__  $$| $$$$$$$/| $$$$$$$$   | $$
| $$  $$$| $$| $$  \__/| $$__  $$| $$__  $$   | $$
| $$\  $ | $$| $$      | $$  \ $$| $$  | $$   | $$
| $$ \/  | $$| $$      | $$  | $$| $$  | $$   | $$
|__/     |__/|__/      |__/  |__/|__/  |__/   |__/

                  ,     .
                  (\,;,/)
                   (o o)\//,
                    \ /     \,
                    `+'(  (   \    )
                       //  \   |_./
                     '~' '~----'
        https://github.com/user696/MrRAT

MrRAT server listening for connections on port 1337.

[?] MrRAT> help

client <id>         - Connect to a client.
clients             - List connected clients.
download <files>    - Download file(s).
execute <command>   - Execute a command on the target.
help                - Show this help menu.
kill                - Kill the client connection.
persistence         - Apply persistence mechanism.
quit                - Exit the server and end all client connections.
scan <ip>           - Scan top 25 ports on a single host.
selfdestruct        - Remove all traces of the RAT from the target system.
survey              - Run a system survey.
unzip <file>        - Unzip a file.
upload <files>      - Upload files(s).
wget <url>          - Download a file from the web.

[?] MrRAT> clients
ID - Client Address
 1 - 127.0.0.1

[?] MrRAT> client 1

[1] MrRAT> execute uname -a
Linux sandbox3 4.8.13-1-ARCH #1 SMP PREEMPT Fri Dec 9 07:24:34 CET 2016 x86_64 GNU/Linux
```

## Build a stand-alone executable
Keep in mind that before building you will likely want to modify both the `HOST` and `PORT` variables located at the top of `MrRAT_client.py` to fit your needs.

On Linux you will need Python 2.x, [PyInstaller](http://www.pyinstaller.org/), and pycrypto. Then run something like `pyinstaller2 --onefile MrRAT_client.py` and it should generate a `dist/` folder that contains a stand-alone ELF executable.

On Windows you will need Python 2.x, PyInstaller, pycrypto, pywin32, and pefile. Then run something like `C:\path\to\PyInstaller-3.2\PyInstaller-3.2\pyinstaller.py --onefile MrRAT_client.py` and it should generate a `dist/` folder that contains a stand-alone PE (portable executable).

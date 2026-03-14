# python-networking-lab

A small lab of networking demos in Python and C: reverse shell, packet sniffer, website scanner, and basic socket clients/servers.

**Safety note:** Some tools are dual-use. Only run them on systems and networks you own or have explicit permission to test.

## Contents
- `Reverse-Shell/` (Python): reverse shell server/client
- `Network-Sniffer/` (Python): raw packet sniffer (Linux only)
- `Website-Scanner/` (Python + OS tools): gathers domain/IP/ports/robots/whois
- `Sockets/` (C): echo and time client/server examples

## Requirements
- Python 3.x
- C compiler (for `Sockets/`), e.g. `gcc`
- Linux or WSL for `Network-Sniffer/` (uses `AF_PACKET`)
- System tools for `Website-Scanner/`:
  - `host`, `nmap`, `whois`

Python package:
```
tld
```

## Setup
Install the Python dependency:
```
pip install -r requirements.txt
```

## Reverse-Shell
**Server (on your machine):**
```
python Reverse-Shell/server.py
```

**Client (on the target machine you own/control):**
```
python Reverse-Shell/client.py <server_ip>
```

## Network-Sniffer (Linux/WSL only)
Run as root/admin:
```
sudo python Network-Sniffer/sniffer.py
```

## Website-Scanner
Edit the list in `Website-Scanner/website.py`, then run:
```
python Website-Scanner/main.py
```
Results are written to `Website-Scanner/websites/<site>/`.

## Sockets (C)
### Echo
```
gcc Sockets/echo/echoServer.c -o echoServer
./echoServer 5000
```
In another terminal:
```
gcc Sockets/echo/echoClient.c -o echoClient
./echoClient 127.0.0.1 5000
```

### Time
```
gcc Sockets/time/timeServer.c -o timeServer
./timeServer
```
In another terminal:
```
gcc Sockets/time/timeClient.c -o timeClient
./timeClient 127.0.0.1
```

## Known Issues
- `Sockets/time/timeServer.c` has a syntax error and will not compile as-is. It needs a missing `)` on the `snprintf` line.

## License
No license is specified yet.
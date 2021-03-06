## TCPProbe

[![Github Actions](https://github.com/mehrdadrad/tcpprobe/workflows/build/badge.svg)](https://github.com/mehrdadrad/tcpprobe/actions?query=workflow%3Abuild) [![Go report](https://goreportcard.com/badge/github.com/mehrdadrad/tcpprobe)](https://goreportcard.com/report/github.com/mehrdadrad/tcpprobe)  [![Coverage Status](https://coveralls.io/repos/github/mehrdadrad/tcpprobe/badge.svg?branch=main)](https://coveralls.io/github/mehrdadrad/tcpprobe?branch=main)

TCPProbe is a tool for network path and service monitoring. It exposes information about socket’s underlying TCP session, TLS and HTTP (more than 60 metrics). the request is highly customizable.

![tcpprobe](/docs/imgs/tcpprobe.png)

## Features
- TCP socket statistics
- TCP/IP customization
- Prometheus exporter
- Probing multiple hosts

#### Options
```
usage: tcpprobe options target(s)

options:
   --ipv6, -6                           connect only to IPv6 address (default: false)
   --ipv4, -4                           connect only to IPv4 address (default: false)
   --http2                              force to use HTTP version 2 (default: false)
   --prom-disabled                      disable prometheus (default: false)
   --insecure, -i                       don't validate the server's certificate (default: false)
   --server-name value, -n value        server name is used to verify the hostname (TLS)
   --source-addr value, -S value        source address in outgoing request
   --prom-addr value, -p value          specify prometheus exporter IP and port (default: ":8081")
   --filter value, -f value             given metric(s) with semicolon delimited
   --count value, -c value              stop after sending count requests [0 is unlimited] (default: 0)
   --timeout value, -t value            specify a timeout for dialing to targets (default: 5s)
   --http-timeout value                 specify a timeout for HTTP (default: 30s)
   --wait value, -w value               time to wait after each request (default: 1s)
   --tos value, -z value                set the IP type of service (default: depends on the OS)
   --ttl value, -m value                set the IP time to live (default: depends on the OS)
   --socket-priority value, -r value    set queuing discipline (default: depends on the OS)
   --mss value, -M value                TCP max segment size (default: depends on the OS)
   --congestion-alg value               TCP congestion control algorithm (default: depends on the OS)
   --send-buffer value                  maximum socket send buffer in bytes (default: depends on the OS)
   --rcvd-buffer value                  maximum socket receive buffer in bytes (default: depends on the OS)
   --tcp-nodelay-disabled, -o           disable Nagle's algorithm (default: false)
   --tcp-quickack-disabled, -k          disable quickack mode (default: false)
   --quiet, -q                          turn off tcpprobe output (default: false)
   --json                               print in json format (default: false)
   --json-pretty                        pretty print in json format (default: false)
   --metrics                            show metric's descriptions (default: false)
   --help, -h                           show help (default: false)
```
#### Command line ([download Linux binary](https://github.com/mehrdadrad/tcpprobe/releases/latest/download/tcpprobe)) 
```
tcpprobe -json https://www.google.com
```
```json
{"Target":"https://www.google.com","IP":"142.250.72.196","Timestamp":1607567390,"Seq":0,"State":1,"CaState":0,"Retransmits":0,"Probes":0,"Backoff":0,"Options":7,"Rto":204000,"Ato":40000,"SndMss":1418,"RcvMss":1418,"Unacked":0,"Sacked":0,"Lost":0,"Retrans":0,"Fackets":0,"LastDataSent":56,"LastAckSent":0,"LastDataRecv":0,"LastAckRecv":0,"Pmtu":9001,"RcvSsthresh":56587,"Rtt":1365,"Rttvar":446,"SndSsthresh":2147483647,"SndCwnd":10,"Advmss":8949,"Reordering":3,"RcvRtt":0,"RcvSpace":62727,"TotalRetrans":0,"PacingRate":20765147,"BytesAcked":448,"BytesReceived":10332,"SegsOut":10,"SegsIn":11,"NotsentBytes":0,"MinRtt":1305,"DataSegsIn":8,"DataSegsOut":3,"DeliveryRate":1785894,"BusyTime":4000,"RwndLimited":0,"SndbufLimited":0,"Delivered":4,"DeliveredCe":0,"BytesSent":447,"BytesRetrans":0,"DsackDups":0,"ReordSeen":0,"RcvOoopack":0,"SndWnd":66816,"TCPCongesAlg":"cubic","HTTPStatusCode":200,"HTTPRcvdBytes":14683,"HTTPRequest":113038,"HTTPResponse":293,"DNSResolve":2318,"TCPConnect":1421,"TLSHandshake":57036,"TCPConnectError":0,"DNSResolveError":0}
```
#### Docker
```
docker run --rm mehrdadrad/tcpprobe 54.153.75.189:22
```

#### Docker Compose
Run TCPProbe and Prometheus
```
docker-compose up -d
```
Open your browser and try http://localhost:9090
You can edit the docker-compose.yml to customize the options and target(s).

## License
This project is licensed under MIT license. Please read the LICENSE file.

## Contribute
Welcomes any kind of contribution, please follow the next steps:

- Fork the project on github.com.
- Create a new branch.
- Commit changes to the new branch.
- Send a pull request.

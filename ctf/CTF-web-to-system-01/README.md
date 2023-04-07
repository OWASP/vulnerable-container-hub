# CTF-web-to-system-01

A CTF challenge: Web hacking into the linux system and get R00T!!

There are three flags found during the journey.

## Challenge right away

```
$ docker run -d -p 9090:9090 quay.io/jechoisec/ctf-web-to-system-01
```

Access http://`<ip>`:9090 with your browser.

## How to build yourself and run

```
$ docker build . -t jechoisec/ctf1
$ docker run -d -p 9090:9090 jechoisec/ctf-web-to-system-01
```

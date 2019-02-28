# slapper

__Simple load testing tool with real-time updated histogram of request timings__

![slapper](https://raw.githubusercontent.com/ikruglov/slapper/master/img/example.gif)

## Interface

![interface](https://raw.githubusercontent.com/ikruglov/slapper/master/img/interface.png)

## Usage
```bash
$ ./slapper -help
Usage of ./slapper:
  -H value
    	HTTP header 'key: value' set on all requests. Repeat for more than one header.
  -base64body
    	Bodies in targets file are base64-encoded
  -maxY duration
    	max on Y axe (default 100ms)
  -minY duration
    	min on Y axe (default 0ms)
  -rate uint
    	Requests per second (default 50)
  -targets string
    	Targets file
  -timeout duration
    	Requests timeout (default 30s)
  -workers uint
    	Number of workers (default 8)
  -proxy string
    	proxy to use (example: http://proxy.foobar.com:3128)

```

## Key bindings
* q, ctrl-c - quit
* r - reset stats
* k - increase rate by 100 RPS
* j - decrease rate by 100 RPS

## Targets syntax

The targets file is line-based. Its syntax is:

	HTTP_METHOD url
	$ body

The body line is optional. The rules for what is considered to be a body
line are:

1. If something starts with `$ ` (dollar-sign and space), it's a body
2. If the line is literally `{}`, it's an empty body

A missing body line is taken to mean an empty request body. Point (2) is there
for backwards-compatibility.

## Acknowledgement
* Idea and initial implementation is by @sparky
* This module was originally developed for Booking.com.

# groktunnel

Expose localhost HTTP servers with a public URL.

This is the 5th or 6th implementation of this system since the original
[localtunnel](https://github.com/progrium/localtunnel) in 2010, which was then
cloned many times. It was then commercialized by [Ngrok](https://ngrok.com/).

This is a standalone fork of the demo in https://github.com/progrium/qmux

## Try it out

First we run the groktunnel server. Normally this would be run on a server, but
by default uses `vcap.me` for a hostname which resolves all of its subdomains to
localhost.

```
$ ./groktunnel
2021/04/29 16:10:35 groktunnel server [vcap.me] ready!
```

Now run a local web server. Here is how to run a server listing a file directory
with Python:

```
$ python -m SimpleHTTPServer
Serving HTTP on 0.0.0.0 port 8000 ...
```

Then we run groktunnel as a client by giving it the local port to expose.

```
$ ./groktunnel 8000
port 8000 http available at:
http://y8eyshnpol.vcap.me:9999
```

That address should serve the same content as the local web server on 8000. For
added effect, run both client and server with `-p 80`, which will require root
to run the server.

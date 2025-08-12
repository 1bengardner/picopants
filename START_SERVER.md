# Starting a server to host PicoPants

You can start a server in any number of ways.

The way I did it was using a Python 2 [[download]](https://www.python.org/downloads/release/python-276/) `SimpleHTTPServer`.

Save this Python 2 script adapted from [a StackOverflow question](https://stackoverflow.com/questions/59908927/failed-to-load-module-script-the-server-responded-with-a-non-javascript-mime-ty):

```python2
import SimpleHTTPServer
import SocketServer

PORT = 8000

Handler = SimpleHTTPServer.SimpleHTTPRequestHandler
Handler.extensions_map.update({
    ".js": "text/javascript",
    ".mjs": "text/javascript",
    ".wasm": "application/wasm",
});

httpd = SocketServer.TCPServer(("", PORT), Handler)

print ("Serving at port", PORT)
httpd.serve_forever()
```

and run it with `python -m <script_file_name>` in `picopants`.

<sub>I don't include this script in the repo because I consider it to be too "auxiliary".</sub>

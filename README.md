# flask_jsonrpc

> **WARNING:** This repository may be unstable or non-functional. Use at your own risk.

`flask_jsonrpc` is a small Flask extension that provides basic JSON-RPC server/client helpers.

## What It Does

- Exposes a JSON-RPC endpoint in a Flask app
- Registers handler methods via decorator
- Parses positional and keyword params
- Includes a minimal JSON-RPC client for outgoing calls

## Quick Start

```bash
pip install -r requirements.txt
```

```python
from flask import Flask
from flask_jsonrpc import SimpleJsonRpcServer

app = Flask(__name__)
rpc = SimpleJsonRpcServer(app, service_url="/json-rpc/", show_api=True)

@rpc.register("math.add")
def add(a, b):
    return a + b

if __name__ == "__main__":
    app.run(host="127.0.0.1", port=5000, debug=True)
```

Send a JSON-RPC request to `POST /json-rpc/` with `Content-Type: application/json`.

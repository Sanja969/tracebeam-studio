# Tracebeam Studio ⚡

Local-first realtime observability dashboard for Tracebeam SDK.

Tracebeam Studio helps developers inspect events, traces, sessions, fetch requests, errors, latency and throughput locally — without cloud setup.

![Tracebeam Demo](./demo.gif)

## What it includes

- Go ingestion server
- SQLite persistence
- WebSocket realtime streaming
- React dashboard
- Fetch request monitoring
- Error clustering
- Session and trace views
- Latency and throughput charts

## Architecture

```txt
Application + tracebeam SDK
        ↓ HTTP POST /events
Tracebeam Studio Server
        ↓ SQLite + WebSocket
Tracebeam Studio Web Dashboard
```

## Run locally

```bash
git clone --recurse-submodules https://github.com/Sanja969/tracebeam-studio.git
cd tracebeam-studio
docker compose up --build
```

Open:
```txt
http://localhost:5173
```

Server runs on:
```txt
http://localhost:8080
```

## Connect your app

Install the SDK:

```bash
 npm install tracebeam
```

```ts
import {
  configure,
  enableFetchInstrumentation,
  enableGlobalErrorCapture,
} from "tracebeam";

configure({
  transport: async (event) => {
    await fetch("http://localhost:8080/events", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify(event),
    });
  },
});

enableFetchInstrumentation();
enableGlobalErrorCapture();
```

## Repositories

* SDK: https://github.com/Sanja969/tracebeam
* Studio Server: https://github.com/Sanja969/tracebeam-studio-server
* Studio Web: https://github.com/Sanja969/tracebeam-studio-web

## Status

Tracebeam Studio is under active development.

## License

MIT
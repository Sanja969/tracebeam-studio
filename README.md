# Tracebeam Studio ⚡

Tracebeam Studio is a local-first realtime observability platform for frontend applications built with a custom TypeScript SDK, Go websocket backend, and SQLite event persistence.

Tracebeam Studio helps developers inspect events, traces, sessions, fetch requests, errors, latency and throughput locally — without cloud setup.

![Tracebeam Demo](./demo.gif)
Realtime trace visualization, fetch instrumentation, error tracking, and session monitoring in action.


## Platform components

- Go ingestion server
- SQLite persistence
- WebSocket realtime streaming
- React dashboard
- Fetch request monitoring
- Error clustering
- Session and trace views
- Latency and throughput charts

## Features

- Realtime frontend observability dashboard
- Custom TypeScript SDK
- Runtime error tracking
- Automatic fetch instrumentation
- Performance measurements
- Trace and session grouping
- Realtime WebSocket streaming
- SQLite event persistence
- Local-first architecture
- Docker Compose setup
- Overlay debugging widget
- Network request inspection
- Trace waterfall visualization

## Architecture

```txt
Frontend Application + Tracebeam SDK
            ↓ HTTP /events
Tracebeam Studio Server (Go + SQLite)
            ↓ WebSocket streaming
Tracebeam Studio Dashboard (React)
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

## Current status

Tracebeam Studio is actively being developed and expanded with additional observability tooling features.

## License

MIT
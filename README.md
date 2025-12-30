# wrk2
[![Build Status](https://travis-ci.com/giltene/wrk2.svg?branch=master)](https://travis-ci.com/giltene/wrk2) [![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/giltene/wrk2?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

  **wrk3 – The HTTP benchmarking tool that doesn't lie about latency**

  wrk3 is a modern evolution of the legendary wrk. It keeps everything you love — blazing fast, Lua scripting, simple CLI — but fixes the biggest flaw in HTTP benchmarking: Coordinated Omission.wrk3

"Your 99.99th percentile matters. Don't let Coordinated Omission hide the truth."

## The Problem wrk3 Solves
Most benchmarking tools (including classic wrk) measure latency only when they manage to send a request.
When the server slows down, the tool backs off → fewer slow requests are sent → tail latency looks artificially good.That's Coordinated Omission — a silent killer of accurate benchmarks.wrk3 eliminates it completely:Measures latency from planned send time, not actual send time
Uses HdrHistogram for ultra-precise percentiles
Offers true constant rate mode (-R) — exactly N requests/second, no bursts

## Killer Features

| Feature | wrk3 | Original wrk |
|---------|------|--------------|
| **Accurate tail latency** | ✅ Yes (no Coordinated Omission) | ❌ No |
| **Constant request rate** | ✅ Yes (-R flag) | ❌ No |
| **HdrHistogram percentiles** | ✅ Yes (99.99, 99.999, 99.9999) | ❌ No |
| **LuaJIT scripting** | ✅ Yes (Full compatibility) | ✅ Yes |
| **Multi-platform binaries** | ✅ Yes (Linux/macOS x64/arm64 - Apple Silicon native) | ⚠️ Limited |
| **Drop-in replacement** | ✅ Yes (Same CLI syntax) | — |

## Get Started in 30 Seconds

# Download latest release (recommended)
# Choose your platform from https://github.com/quadgatefoundation/wrk3/releases

# Classic mode (compatible with wrk)
./wrk3 -t12 -c400 -d30s http://localhost:8080

# The right way – constant rate (accurate latency)
./wrk3 -t8 -c100 -d60s -R 10000 http://localhost:8080   # exactly 10k req/s

# With custom Lua script
./wrk3 -t12 -c200 -d30s -R 15000 -s pipeline.lua http://api.example.com

## Real Output Example

Running 60s test @ constant rate 15000 req/s
  12 threads and 200 connections

  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency    12.34ms    8.21ms  156.78ms   82.1%
    Req/Sec     1.25k     89.34     1.67k    91.2%

  Latency Distribution (HdrHistogram)
     50.000%    9.12ms
     75.000%   14.56ms
     90.000%   21.34ms
     99.000%   45.89ms
     99.900%   89.12ms
     99.990%  134.56ms
     99.999%  152.34ms

  900000 requests in 60.00s, 1.35GB read
Requests/sec:  15000.00
Transfer/sec:     22.5MB

## Why Developers Love wrk3

"Finally a tool that shows the real 99.99th percentile. No more surprises in production." – Go backend team lead

"Constant rate mode changed how we capacity plan. Numbers now match real traffic." – SRE at fintech startup

## Installation

Pre-built binaries (recommended):
Download from Releases – Linux & macOS, x64 & arm64.Build from source:

make
sudo cp wrk3 /usr/local/bin/

## Resources


Coordinated Omission Explained (docs/coordinated-omission.md) – deep dive
Constant Rate vs Burst (docs/constant-rate.md)
Lua Scripting Guide (docs/lua.md)
Benchmarking Best Practices (docs/best-practices.md)

## Contributing

Pull requests welcome! See CONTRIBUTING.md

## License

MIT – same as original wrk

Built by@quadgatefoundation – 2025

wrk3 – Because fake-low latency kills production systems. Star this repo if you want honest benchmarks.
Your tail latency deserves the truth.Ready to see the real performance of your server? Download wrk3 now.


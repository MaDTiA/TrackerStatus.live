# TrackerStatus.live

> Real-time BitTorrent tracker validation and monitoring service

[![Status](https://img.shields.io/badge/Status-Active-success.svg)](https://trackerstatus.live)

## What is TrackerStatus.live?

**TrackerStatus.live** is a real-time service designed to validate and monitor BitTorrent tracker health. It helps users and torrent clients identify which trackers are actually working, eliminating dead, expired, or parked domains from tracker lists.

Visit the live service at **[https://trackerstatus.live](https://trackerstatus.live)**

## The Problem

Many torrent tracker lists contain:
- Dead trackers (offline servers)
- Expired domains (no longer hosting trackers)
- Parked domains (advertising pages)
- Invalid URLs (syntax errors, wrong protocols)

This wastes bandwidth and slows down torrent discovery.

## The Solution

TrackerStatus.live performs **deep validation** using the actual BitTorrent protocol:

- **Protocol Validation** - Verifies proper BitTorrent announce responses (bencoded data)
- **Multi-Protocol Support** - Tests HTTP, HTTPS, and UDP trackers
- **Parked Domain Detection** - Identifies expired/advertising domains
- **Real Response Analysis** - Distinguishes real trackers from fake HTML pages
- **Fast Parallel Checking** - Validates hundreds of trackers in seconds

## Features

### Core Validation
- **HTTP/HTTPS Tracker Validation** - Sends proper announce requests and validates bencoded responses
- **UDP Tracker Protocol** - Implements BitTorrent UDP tracker handshake
- **Smart Detection** - Identifies parked domains, expired domains, and advertising pages
- **Protocol Compliance** - Checks for proper tracker response keys (`interval`, `peers`, `failure reason`)

### Real-Time Monitoring
- **Live Status Updates** - Continuous monitoring of tracker availability
- **Historical Data** - Track uptime and reliability over time
- **API Access** - Programmatic access to tracker status data
- **Community Lists** - Curated lists of verified working trackers

## How It Works

### HTTP/HTTPS Validation
1. Constructs proper BitTorrent announce request with required parameters
2. Sends request to tracker
3. Validates response is bencoded (not HTML)
4. Checks for tracker-specific keys (`interval`, `peers`)
5. Detects parked/expired domains using pattern matching

### UDP Validation
1. Resolves tracker hostname to IP
2. Sends BitTorrent UDP connect request
3. Validates protocol handshake response
4. Confirms transaction ID matches

### Invalid Detection
- HTML page detection (trackers return binary data, not HTML)
- Parked domain keywords (e.g., "domain for sale", "expired")
- Known parking services (GoDaddy, Namecheap, Sedo, etc.)
- Response size validation
- DNS resolution failures

## Key Advantages

| Feature | TrackerStatus.live | Basic Ping/HTTP Check |
|---------|-------------------|----------------------|
| Protocol Validation | Full BitTorrent protocol | Only HTTP status |
| Bencoded Response Check | Yes | No |
| Parked Domain Detection | Yes | No |
| UDP Tracker Support | Yes | No |
| False Positive Rate | Very Low | High |
| Real-Time Updates | Yes | No |

## Why This Matters

Clean tracker lists mean:
- Faster torrent peer discovery
- Reduced bandwidth waste
- Better privacy (no accidental connections to ad servers)
- Improved torrent client performance

## Use Cases

- **Torrent Client Users** - Maintain clean, working tracker lists
- **Content Distributors** - Ensure reliable tracker availability
- **Developers** - Integrate tracker validation into applications
- **Network Administrators** - Monitor tracker infrastructure

## Contributing

Contributions are welcome! Areas for improvement:

- Additional parked domain patterns
- WebSocket tracker support (wss://)
- Enhanced web interface features
- Historical tracker statistics
- Additional API endpoints

## License

MIT License - feel free to use in your projects.

## Links

- **Website:** [https://trackerstatus.live](https://trackerstatus.live)
- **Issues:** [GitHub Issues](https://github.com/yourusername/trackerstatus-live/issues)
- **Discussions:** [GitHub Discussions](https://github.com/yourusername/trackerstatus-live/discussions)

---

<p align="center">Made for the BitTorrent community</p>
<p align="center">Star this repo if you find it useful</p>

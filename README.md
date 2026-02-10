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


---

<p align="center">Made for the BitTorrent community</p>
<p align="center">Star this repo if you find it useful</p>

# TrackerStatus Tracker Checker Manual Script

> Python script for validating BitTorrent tracker health with deep protocol validation

[![Python](https://img.shields.io/badge/Python-3.6+-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## Overview

A standalone Python script that validates BitTorrent trackers using actual protocol validation. Unlike simple ping or HTTP status checks, this script performs deep validation by analyzing tracker responses, detecting parked domains, and filtering out fake trackers.

Part of the [TrackerStatus.live](https://trackerstatus.live) project.

## Features

### Deep Protocol Validation
- **HTTP/HTTPS Trackers** - Sends proper BitTorrent announce requests and validates bencoded responses
- **UDP Trackers** - Implements full BitTorrent UDP tracker protocol handshake
- **Response Analysis** - Checks for proper tracker keys (`interval`, `peers`, `failure reason`)
- **Bencoded Data Validation** - Ensures responses are in correct BitTorrent format

### Smart Detection
- **Parked Domain Detection** - Identifies expired domains and advertising pages
- **HTML Page Filtering** - Rejects trackers returning HTML instead of bencoded data
- **Parking Service Detection** - Recognizes GoDaddy, Namecheap, Sedo, Bodis, and other parking services
- **Size Validation** - Filters responses that are too large to be legitimate tracker data

### Performance & Usability
- **Multi-threaded Processing** - Validates 20 trackers concurrently by default
- **Progress Tracking** - Real-time progress updates during validation
- **Dual Usage Modes** - Works via command line or double-click
- **Cross-Platform** - Works on Windows, Linux, and macOS
- **Zero Dependencies** - Uses only Python standard library

## Installation

```bash
# Clone the repository
git clone https://github.com/MaDTiA/TrackerStatus.live.git
cd TrackerStatus.live
```
## Requirements

Python 3.6 or higher (no external dependencies)

## Usage

### Method 1: Double-Click Mode (Windows/Easy)

1. Create `trackers.txt` in the same folder as `TrackerStatus - Checker.py`
2. Add your tracker URLs (one per line)
3. Double-click `TrackerStatus - Checker.py`
4. Results will be saved to `filtered.txt`
5. Press Enter when complete

### Method 2: Command Line

```bash
# Basic usage
python "TrackerStatus - Checker.py" trackers.txt filtered.txt
```
# Custom input/output files
python "TrackerStatus - Checker.py" my_trackers.txt results.txt

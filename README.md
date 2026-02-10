# TrackerStatus.live

> Real-time BitTorrent tracker validation and monitoring service

[![Python](https://img.shields.io/badge/Python-3.6+-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Active-success.svg)](https://trackerstatus.live)

## What is TrackerStatus.live?

**TrackerStatus.live** is a powerful tool designed to validate and monitor BitTorrent tracker health in real-time. It helps users and torrent clients identify which trackers are actually working, eliminating dead, expired, or parked domains from your tracker lists.

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

### Output & Reporting
- **Categorized Results** - Separates trackers into: Alive, Dead, Invalid
- **Protocol Grouping** - Organizes results by HTTP/HTTPS/UDP
- **Detailed Reasons** - Explains why each tracker failed validation
- **Clean Export** - Generates filtered lists ready for use

### Performance
- **Parallel Processing** - Multi-threaded checking (default: 20 concurrent connections)
- **Configurable Timeouts** - Adjustable for network conditions
- **Progress Tracking** - Real-time progress updates during validation

## Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/trackerstatus-live.git
cd trackerstatus-live

# No dependencies required - uses Python standard library only

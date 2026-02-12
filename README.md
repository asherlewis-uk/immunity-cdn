# Immunity Security CDN

A static Content Delivery Network (CDN) repository for the Immunity security platform.

## Overview

This repository serves as a centralized data source for Immunity security components, providing:
- System status information
- Security blocklists
- Certificate data

## Structure

```
data/
├── status.json      # System operational status
├── blocklist.json   # Security blocklist data
└── certs.json       # Certificate information
```

## Data Files

### status.json
Contains the current operational status of the Immunity platform.

### blocklist.json
Maintains a list of blocked entities for security purposes.

### certs.json
Stores certificate information used by the Immunity platform.

## Usage

All data files are accessible via the repository and can be consumed by Immunity clients.

## Validation

All JSON files are automatically validated on each commit to ensure data integrity. 

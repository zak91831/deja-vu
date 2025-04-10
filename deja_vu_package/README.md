# Deja Vu

A next-generation adaptive vulnerability scanner that builds upon Nuclei's foundation while incorporating advanced features for intelligent, context-aware security testing.

## Overview

Deja Vu extends the capabilities of traditional vulnerability scanners by incorporating:

1. **Time-Travel Scanning** - Analyze historical versions of targets to identify vulnerabilities that may have been present in the past or reintroduced
2. **Personality-Driven Scanning** - Emulate different attacker personas with specific scanning behaviors and techniques
3. **Adaptive Learning** - Intelligently prioritize templates based on target technology stack and previous scan results

## Features

- **Modular Architecture** - Plugin-based design allows features to be enabled/disabled independently
- **Nuclei Compatibility** - Maintains compatibility with existing Nuclei templates
- **Historical Analysis** - Integrates with Wayback Machine and historical certificate data
- **Attacker Emulation** - Configurable personas with specific scanning behaviors
- **Intelligent Template Selection** - Prioritizes templates based on target characteristics

## Getting Started

### Prerequisites

- Go 1.18+
- Python 3.9+ (for ML components)

### Installation

```bash
# Clone the repository
git clone https://github.com/dejavu/scanner.git
cd scanner

# Build the binary
go build -o dejavu ./cmd/deja_vu

# Run a basic scan
./dejavu -target example.com
```

### Basic Usage

```bash
# Run a scan with default settings
./dejavu -target example.com

# Enable time-travel scanning
./dejavu -target example.com -time-travel

# Use a specific persona
./dejavu -target example.com -persona apt37

# Enable adaptive learning
./dejavu -target example.com -adaptive
```

## Architecture

Deja Vu follows a modular, plugin-based architecture:

- **Core Engine** - Handles fundamental scanning functionality
- **Feature Modules** - Implement advanced capabilities as plugins
- **Plugin System** - Enables dynamic loading and management of features
- **Configuration System** - Manages user preferences and feature settings

For more details, see the [Architecture Documentation](docs/architecture.md).

## Development

### Project Structure

```
deja_vu/
├── cmd/                # Command-line interfaces
│   └── deja_vu/        # Main CLI application
├── pkg/                # Public packages
│   ├── core/           # Core engine components
│   ├── plugins/        # Plugin system
│   ├── timetravel/     # Time-travel scanning
│   ├── persona/        # Personality-driven scanning
│   └── adaptive/       # Adaptive learning engine
├── internal/           # Private packages
│   ├── config/         # Configuration management
│   ├── utils/          # Utility functions
│   └── logger/         # Logging system
├── docs/               # Documentation
├── scripts/            # Build and utility scripts
└── templates/          # Default templates
```

### Building from Source

```bash
# Clone the repository
git clone https://github.com/dejavu/scanner.git
cd scanner

# Install dependencies
go mod download

# Build the binary
go build -o dejavu ./cmd/deja_vu
```

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Based on the [Nuclei](https://github.com/projectdiscovery/nuclei) vulnerability scanner
- Inspired by advanced concepts in security testing and machine learning

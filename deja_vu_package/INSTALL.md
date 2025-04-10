# Deja Vu Installation Guide

This document provides instructions for installing and running the Deja Vu vulnerability scanner.

## Prerequisites

- Go 1.18+
- Python 3.9+ (for ML components)
- Git

## Installation Steps

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/deja-vu.git
cd deja-vu
```

### 2. Install Dependencies

```bash
# Install Go dependencies
go mod download

# Install Python dependencies (for future ML components)
pip3 install -r requirements.txt  # Note: This file will be created in future versions
```

### 3. Build the Binary

```bash
go build -o dejavu ./cmd/deja_vu
```

### 4. Create Templates Directory

```bash
mkdir -p templates
```

### 5. Verify Installation

```bash
./dejavu -h
```

You should see the help output displaying available commands and options.

## Running Deja Vu

### Basic Scan

```bash
./dejavu -target example.com
```

### Enabling Features

```bash
# Enable time-travel scanning
./dejavu -target example.com -time-travel

# Use a specific persona
./dejavu -target example.com -persona stealthy

# Enable adaptive learning
./dejavu -target example.com -adaptive

# Combine features
./dejavu -target example.com -time-travel -persona apt -adaptive
```

### Configuration

You can customize Deja Vu by editing the `config.yaml` file. See the README.md for more details on configuration options.

## Troubleshooting

If you encounter any issues during installation or running Deja Vu, please check the following:

1. Ensure Go 1.18+ is installed and properly configured
2. Verify that all dependencies are installed
3. Check that the templates directory exists and contains valid templates
4. Ensure you have proper permissions to execute the binary

For more detailed information, please refer to the README.md file.

# deja-vu
Using the Deja Vu Vulnerability Scanner
This guide provides detailed instructions on how to use the Deja Vu vulnerability
scanner, including installation, basic scanning, and utilizing its advanced features.
Installation
Prerequisites
• Go 1.18+
• Python 3.9+ (for ML components)
• Git
Steps
1. Extract the package bash unzip deja_vu_prototype.zip cd deja_vu_package
2. Build the binary bash go build -o dejavu ./cmd/deja_vu
3. Create templates directory bash mkdir -p templates
4. Verify installation bash ./dejavu -h This should display the help output with
available commands and options.
Basic Usage
Running a Basic Scan
To run a basic scan against a target:
./dejavu -target example.com
This will: 1. Load the default configuration from config.yaml 2. Scan the target using
default settings 3. Display results in the console
Specifying Output Format
You can specify the output format:
./dejavu -target example.com -output json
Supported formats: - cli (default): Human-readable console output - json : JSON format
for programmatic processing - yaml : YAML format
Using Custom Templates
To use custom templates:
./dejavu -target example.com -templates /path/to/templates
Advanced Features
Deja Vu includes three advanced features that set it apart from traditional vulnerability
scanners:
1. Time-Travel Scanning
Time-Travel scanning analyzes historical versions of targets to identify vulnerabilities
that may have been present in the past or reintroduced.
To enable Time-Travel scanning:
./dejavu -target example.com -time-travel
This will: 1. Query the Wayback Machine for historical snapshots of the target 2. Analyze
certificate transparency logs for historical domains 3. Scan both current and historical
versions of the target
Configuration options (in config.yaml ):
features:
timetravel:
enabled: true
wayback_machine:
enabled: true
max_snapshots: 10
max_age_days: 365
cert_history:
enabled: true
max_certs: 5
2. Personality-Driven Scanning
Personality-Driven scanning emulates different attacker personas with specific scanning
behaviors and techniques.
To use a specific persona:
./dejavu -target example.com -persona stealthy
Available personas: - standard : Balanced scanning approach (default) - stealthy : Slow,
cautious scanning to avoid detection - aggressive : Fast, thorough scanning without
evasion - apt : Emulates Advanced Persistent Threat behaviors
Configuration options (in config.yaml ):
features:
persona:
enabled: true
default_persona: "standard"
personas:
- name: "standard"
delay: "0ms-100ms"
rate_limit: 150
user_agent: "Deja Vu Scanner v1.0"
- name: "stealthy"
delay: "1s-3s"
rate_limit: 10
user_agent: "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36"
You can add custom personas by editing the configuration file.
3. Adaptive Learning
Adaptive Learning intelligently prioritizes templates based on target technology stack
and previous scan results.
To enable Adaptive Learning:
./dejavu -target example.com -adaptive
This will: 1. Detect the target's technology stack 2. Prioritize templates based on the
detected technologies 3. Collect feedback from scan results to improve future scans
Configuration options (in config.yaml ):
features:
adaptive:
enabled: true
tech_detection:
enabled: true
template_prioritization:
enabled: true
feedback_collection:
enabled: true
Combining Features
You can combine multiple features for more powerful scanning:
./dejavu -target example.com -time-travel -persona apt -adaptive
This command will: 1. Enable Time-Travel scanning to analyze historical versions 2. Use
the APT persona for stealthy, targeted scanning 3. Enable Adaptive Learning to prioritize
templates based on the target
Example Workflows
Basic Security Assessment
./dejavu -target example.com -output json > results.json
Thorough Security Audit
./dejavu -target example.com -time-travel -persona aggressive -adaptive
Stealthy Penetration Test
./dejavu -target example.com -persona stealthy -adaptive
Historical Vulnerability Analysis
./dejavu -target example.com -time-travel
Troubleshooting
Common Issues
1. No templates found
2. Ensure the templates directory exists and contains valid templates
3. Check the path specified with the -templates flag
4. Connection errors
5. Verify network connectivity
6. Check if the target is accessible
7. Slow scanning
8. Adjust rate limiting in the configuration
9. Consider using the aggressive persona for faster scanning
Logs
Logs are written to stdout by default. To save logs to a file, modify the logging
configuration in config.yaml :
logging:
level: "info" # debug, info, warn, error
file: "deja_vu.log"
format: "text" # text, json
Advanced Configuration
For more detailed configuration options, refer to the config.yaml file. This file contains
settings for all features and components of Deja Vu.
Next Steps
After becoming familiar with the basic usage, consider:
1. Creating custom templates for specific vulnerabilities
2. Developing custom personas for specialized scanning scenarios
3. Extending Deja Vu with additional features as described in the developer guide
For more information on extending Deja Vu, refer to the DEVELOPER.md file included in
the package.

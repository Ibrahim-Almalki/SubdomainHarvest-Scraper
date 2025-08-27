# SubdomainHarvest-Scraper
An automated subdomain enumeration and reconnaissance project designed to discover, catalog, and analyze subdomains and API endpoints. This tool leverages and builds upon utilities like iBeHarvester to map a target's external attack surface, handling real-world toolchain errors and integrating external security data.

Features
Massive Subdomain Discovery: Utilizes wordlist-based scanning to uncover hundreds of subdomains, including those with dynamic and obscure naming conventions.

API Endpoint Enumeration: Attempts to discover and scan for common and hidden API endpoints, crucial for modern web application security.

External API Integration: Configurable to pull data from external security platforms like SecurityScorecard and DNS databases.

Error-Resilient Workflow: Built to handle common tooling errors (e.g., missing wordlists, API keys) and continue the scanning process.

Results Parsing: Processes raw, messy output from reconnaissance tools into a more structured format for analysis.

Output Example
The tool generates extensive lists of discovered subdomains, which can include various record types and associated IP addresses.

text
#widgets.example.com
#idls.victim.example.com
#dynamic.example.com
#home.example.com
#yangfan.tec.03.example.com:45.80.215.175
#yourwebsite.example.com
#party.example.com
#ubutor.example.com
...
Installation & Setup
Clone the Repository:

bash
git clone https://github.com/your-username/SubdomainHarvest-Scraper.git
cd SubdomainHarvest-Scraper
Install Dependencies: (Example - may vary)
The project may rely on tools like iBeHarvester. Ensure Python 3 and pip are installed.

bash
# Install pip dependencies from a requirements.txt file (if available)
pip install -r requirements.txt

# You may need to install or configure other reconnaissance tools
# git clone https://github.com/example/iBeHarvester.git
Configure API Keys (Optional):
For full functionality with services like SecurityScorecard, create a configuration file.

bash
# Example: Edit or create an API keys file
mkdir -p /etc/ibeharvester/
nano /etc/ibeharvester/api-keys.yaml
Add your keys in YAML format:

yaml
securityscorecard_api_key: 'your_api_key_here'
# dulluntil_api_key: 'your_other_key_here'
Usage
Run the main scraper script. The tool will automatically attempt to build necessary resources if default wordlists are missing.

bash
python3 subdomain_harvester.py -d example.com
Typical Workflow Output:

text
[1] WordList not found: /path/to/wordlists/api_endpoints.txt
Creating a basic API wordlist for scanning...
[2] An exception has occurred... Continuing with the rest of the scan...
[*] Performing SecurityScorecard scan...
Read api-keys.yaml from /etc/ibeharvester/api-keys.yaml
[*] Performing additional scan...
[*] Scan complete. Results saved to output.txt.
Project Structure
text
SubdomainHarvest-Scraper/
│
├── src/
│   ├── harvester.py          # Main scraping and enumeration logic
│   ├── output_parser.py      # Parses raw tool output into clean lists
│   └── error_handler.py      # Manages common tool errors and exceptions
│
├── wordlists/                # Custom and generated wordlists
│   ├── subdomains.txt
│   └── api_endpoints.txt
│
├── outputs/                  # Directory for scan results
├── config/                   # Configuration files
├── requirements.txt
└── README.md
Common Errors & Handling
This project is designed to be resilient. Common issues that are automatically handled include:

WordList not found: The tool will generate a basic wordlist to continue the scan.

No such file or directory: Errors with temporary files are caught and logged, allowing the main scan to proceed.

'securityscorecard': Errors related to missing API keys or external services are managed gracefully.

Disclaimer
This project is intended for educational purposes, security research, and authorized testing only. The developers assume no liability and are not responsible for any misuse or damage caused by this program.

Always ensure you have explicit permission to scan the target domain. Unauthorized scanning and enumeration is illegal and unethical.

It is the end user's responsibility to obey all applicable local, state, and federal laws.

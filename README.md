## Overview

This repository demonstrates a proof-of-concept integration of the popular MCP (Model Context Protocol) with a FHIR (Fast Healthcare Interoperability Resources) API. Inspired by a post about MCP and AIdbox integration, this project explores the feasibility of setting up a test system to enable such interoperability. The outcome here is a demonstration that it's possible to spin off a process in this regard using Python.

## Motivation

After reading about how AIdbox was able to integrate MCP with a FHIR API, I was motivated to quickly experiment with a similar setup. This repository serves as a demonstration of that concept.

Special thanks to [jcafazzo](https://github.com/jcafazzo), whose project [fhir-mcp](https://github.com/jcafazzo/fhir-mcp) provided a solid foundation and made the process much easier.

## Prerequisites

To reproduce or extend this demonstration, you will need the following installed on your system:

- [Docker](https://www.docker.com/)
- [PostgreSQL](https://www.postgresql.org/)
- [Visual Studio Code (VS Code)](https://code.visualstudio.com/)
- [Claude Desktop](https://www.anthropic.com/claude) (Download and install)

All code in this repository is written in **Python**.

## Getting Started

1. **Clone the Repository**

   ```bash
   git clone https://github.com/EthelEz/mcp_fhir_integration.git
   cd mcp_fhir_integration
   ```

2. **Install Requirements**

   Create a virtual environment and install dependencies (see `requirements.txt`):

   ```bash
   python3 -m venv venv
   source venv/bin/activate
   pip install -r requirements.txt
   ```

3. **Set Up Docker and PostgreSQL**

   Ensure Docker is running. Use Docker Compose or your own scripts to spin up a FHIR server (e.g., HAPI FHIR or similar) and a PostgreSQL database.

4. **Configure Environment**

   Copy `.env.example` to `.env` and fill in the required environment variables.

5. **Run the Integration**

   Launch the integration process:

   ```bash
   python main.py
   ```
6. **Connect to Claude Desktop**
   
     Use the JSON file in the folder for the connections
      ```bash
      claude_desktop_config.json
      ```

## Reference Implementation

Much of the architectural inspiration and practical implementation is based on [jcafazzo/fhir-mcp](https://github.com/jcafazzo/fhir-mcp). Review that repository for a detailed look at typical MCP query systems with FHIR.

## Project Structure

```
mcp_fhir_integration/
├── main.py
├── requirements.txt
├── Dockerfile
├── docker-compose.yml
├── .env.example
└── README.md
```

- `main.py` – Entry point for the integration demo (Python).
- `requirements.txt` – List of Python dependencies.
- `Dockerfile`/`docker-compose.yml` – For containerized setup.
- `post_data_fhir.http` / `get_data.http` - To load or read sample FHIR data.
- `.env.example` – Example environment configuration.

## Notes

- This is a demonstration project. It is not production-ready.
- Claude Desktop is optional but can assist with AI-driven development workflows.

## License

See `LICENSE` file for details.

---

*Inspired by community projects and the potential for healthcare data interoperability with FHIR and MCP.*
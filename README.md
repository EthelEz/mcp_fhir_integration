## Overview

This repository demonstrates a proof-of-concept integration of the popular MCP (Model Context Protocol) with a FHIR (Fast Healthcare Interoperability Resources) API. Inspired by a post about MCP and AIdbox integration, this project explores the feasibility of setting up a test system to enable such interoperability. The outcome here is a demonstration that it's possible to spin off a process in this regard using Python.

## Motivation

After reading about how AIdbox was able to integrate MCP with a FHIR API, I was motivated to quickly experiment with a similar setup. This repository serves as a demonstration of that concept.

Special thanks to [jcafazzo](https://github.com/jcafazzo), whose project [fhir-mcp](https://github.com/jcafazzo/fhir-mcp) provided a solid foundation and made the process much easier.

## Prerequisites

To reproduce or extend this demonstration, you will need the following installed on system:

- [Docker](https://www.docker.com/)
- [PostgreSQL](https://www.postgresql.org/)
- [Visual Studio Code (VS Code)](https://code.visualstudio.com/)
- [Claude Desktop](https://www.anthropic.com/claude) (Download and install)

All code in this repository is written in **Python**.

## Getting Started

1. **Clone the Repositories and Install Requirements**

   ```bash
   git clone https://github.com/EthelEz/mcp_fhir_integration.git
   cd mcp_fhir_integration

   run docker compose up

   Test that the server is working by going to the browser and paste server URL. In my own,
   http://localhost:8001/fhir/metadata
   ```

   Also 

   ```bash 
   git clone https://github.com/jcafazzo/fhir-mcp
   cd fhir_mcp
   pip install -r requirements.txt
   ```

   In line 794 of **fhir-mcp_server.py**, replace **https://hapi.fhir.org/baseR4** with FHIR API (in my case, **http://localhost:8001/fhir**)

   Add token if you have or ignore it

   In command line, run 
   
   ```bash
   python fhir-mcp_server.py
   ```

3. **Set Up Docker and PostgreSQL**

   Ensure Docker is running. Use Docker Compose or own scripts to spin up a FHIR server (e.g., HAPI FHIR or similar) and a PostgreSQL database.

4. **Configure Environment**

   Copy `.env.example` to `.env` and fill in the required environment variables.

5. **Install Claude Desktop**

   Install from :
  
   - [Claude Desktop](https://www.anthropic.com/claude)
   
6. **Connect to Claude Desktop**
   
     - Go to Claude Desktop Settings 
     - Then Developers and Edit the JSON config
     - Use the JSON file in the folder for the connections


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
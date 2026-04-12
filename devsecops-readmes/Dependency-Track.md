# Dependency-Track
SBOM / Supply-Chain Analysis Platform

A Software Bill of Materials platform helps organizations ingest, analyze, track, and continuously monitor software component inventories. Instead of only storing a BOM file, such platforms correlate included components with vulnerability intelligence, license data, and policy violations.

Why organizations use SBOM platforms:

Improve visibility into third-party and open-source components
Identify known vulnerable components in software products
Support supply-chain security and compliance requirements
Track component risk over time as new advisories emerge
Evaluate CycloneDX or SPDX BOMs centrally
OWASP Dependency-Track

## [Dependency-Track](https://owasp.org/www-project-dependency-track/)
Dependency-Track is an open-source platform focused on continuous SBOM analysis. It is designed to ingest CycloneDX or SPDX BOMs, correlate them with vulnerability intelligence, and provide project-based visibility into software supply-chain risk. The official project describes it as an intelligent platform that leverages SBOMs directly and offers capabilities that traditional SCA alone cannot provide.

Dependency-Track provides a centralized place to:

Upload and analyze CycloneDX or SPDX SBOM files
Track projects and versions based on BOM submissions
Correlate BOM components with vulnerability intelligence
Evaluate operational, security, and license risk
Use policy-based assessment for components and projects
Integrate with CI/CD pipelines through a REST API


### Setup
#### 1. Create a local project directory
```
user@demo[/]$ mkdir dependency-track-demo
```
```
user@demo[/]$ cd dependency-track-demo
```
#### 2. Downloads the latest Docker Compose file
```
user@demo[/dependency-track-demo]$ curl -LO https://dependencytrack.org/docker-compose.yml
```
#### 3. Start the stack using Docker Compose
```
user@demo[/dependency-track-demo]$ docker compose up -d
```
#### 4. Watch the startup
```
user@demo[/dependency-track-demo]$ docker compose logs -f dtrack-apiserver
```

After the setup you should be able to access the dashboard

-> [localhost:8080](http://localhost:8080/dashboard)

### Importing SBOM Results

#### 1. Generate your SBOM artifact in GitHub Actions
For example:
- bom-backend.json
- bom-backend.xml
- bom-frontend.json

#### 2. Download the artifact locally
From the GitHub Actions run, download sbom-cyclonedx.zip and extract it.

#### 3. Create a project in Dependency-Track
In the UI:
1. Go to Projects
2. Create a new project, for example:
3. Name: OWASP Juice Shop
4. Version: demo

### 4. Upload the BOM
In the project view:
- Choose BOM upload / upload SBOM
- Select your CycloneDX file, for example:
    - bom-backend.json
    - bom-frontend.json

Dependency-Track supports manual BOM upload through the UI, and also supports API-based BOM publishing for CI/CD use cases.

#### 5. Review the evaluated BOM
After upload, Dependency-Track will:
- parse the BOM
- create/update the project inventory
- correlate components against vulnerability intelligence
- show project and component risk in the UI
# IaC Scanning
Infrastructure scanning is the automated assessment of hosts, servers, services, network components, and exposed interfaces for security weaknesses such as outdated software, misconfigurations, unnecessary open ports, weak TLS settings, or known vulnerabilities. In a DevSecOps context, it complements application-focused security checks by addressing risks in the underlying runtime and deployment environment.

Why organizations should include infrastructure scanning in their DevSecOps strategy:
- Identifies vulnerabilities in servers, containers, network services, and exposed environments early
- Detects misconfigurations that are not covered by source code or dependency scanning
- Reduces attack surface by revealing unnecessary open ports and insecure services
- Supports continuous monitoring of productive and pre-productive environments
- Helps prioritize remediation based on real infrastructure exposure
- Improves compliance and audit readiness through documented scan results
- Complements SAST, SCA, IaC scanning, and container scanning for a more complete security posture
- Strengthens defense-in-depth by securing not only the application, but also the platform it runs on

## [OpenVAS / Greenbone Community Edition (Local via Docker)](https://greenbone.github.io/docs/latest/22.4/container/index.html)
This guide describes how to run OpenVAS / Greenbone Community Edition locally with Docker for demonstration purposes.
In this project, infrastructure scanning is operated as an external infrastructure scanning service and is therefore intentionally decoupled from GitHub Actions. Scan results can be exported from the local OpenVAS instance and imported into DefectDojo during the showcase.

This approach is appropriate for a prototype because OpenVAS requires persistent feed data, initialization time, and noticeably more runtime and storage than lightweight CI-native scanners. Greenbone’s own container documentation also notes that the initial feed synchronization and loading process can take a long time.

### Why OpenVAS is not run inside GitHub Actions
OpenVAS is not a lightweight single-binary scanner. The Greenbone Community Edition container setup consists of multiple services and requires vulnerability tests, SCAP data, CERT data, port lists, scan configurations, and database-backed state. Greenbone documents that the data must first be pulled and then loaded by daemons, and that this can take several minutes up to hours, especially on first setup.

For this reason, OpenVAS is operated locally as a persistent service and used as an external scanning component in the prototype.

### Setup
#### 1. Create a local project directory
```
user@demo[/]$ mkdir greenbone-community-container
```
```
user@demo[/]$ cd greenbone-community-container
```
#### 2. Downloads the latest Docker Compose file
```
user@demo[/greenbone-community-container]$ curl -f -L https://greenbone.github.io/docs/latest/_static/docker-compose.yml -o compose.yaml
```
#### 3. Start the stack using Docker Compose
```
user@demo[/greenbone-community-container]$ docker compose -f compose.yaml up -d
```
#### 4. Update all images
```
user@demo[/greenbone-community-container]$ docker compose -f compose.yaml pull
```
```
user@demo[/greenbone-community-container]$ docker compose -f compose.yaml up -d
```
#### Optional: trigger a manual feed synchronization
```
user@demo[/greenbone-community-container]$ docker compose -f compose.yaml pull notus-data vulnerability-tests scap-data dfn-cert-data cert-bund-data report-formats data-objects
```
```
user@demo[/greenbone-community-container]$ docker compose -f compose.yaml up -d notus-data vulnerability-tests scap-data dfn-cert-data cert-bund-data report-formats data-objects
```
#### 5. Wait for the initial setup
Greenbone documents that feed synchronization has two parts:

1. pulling the feed-related images
2. loading the data into memory and the database by running daemons

They explicitly note that both parts may take several minutes up to hours, especially during the initial synchronization.
```
user@demo[/greenbone-community-container]$ docker compose -f compose.yaml ps
```
```
user@demo[/greenbone-community-container]$ docker compose -f compose.yaml logs -f
```
After the setup you should be able to access the dashboard

-> [localhost:9392](http://localhost:9392/dashboard)

### Setting up a Target and running Scan

#### 1. Run a first scan
In the Greenbone UI, create:
1. a target
2. a task
3. a scan configuration
4. then start the task

Avoid scanning anything you do not own or administer.

### 2. Export results for DefectDojo
After the scan completes, export the report from the Greenbone UI in a format your showcase workflow can use.

For your thesis demo flow, the intended process is:

Run infrastructure scan locally in OpenVAS
Export the report
Import the report manually into DefectDojo
Present OpenVAS as an external infrastructure scanning service

That keeps your CI pipeline lean while still integrating the results into the central vulnerability management view.
## CouchDB Cluster Configuration Taskfile

This repository contains a **Taskfile** for automating the configuration of a **CouchDB Obsidian-sync** running in Kubernetes.
The Taskfile creates a databad and applies authentication, enables CORS, increases request limits, and verifies settings across all nodes.

### Prerequisites
- **Taskfile Installed** ([Installation Guide](https://taskfile.dev/installation/))
- **CouchDB Cluster Running** in Kubernetes
- **Admin Credentials** for CouchDB

### Configuration Details
- **Database:** Creates a database
- **Authentication Enforcement:** Requires valid user authentication for all requests.
- **CORS Configuration:** Allows Obsidian LiveSync and web access.
- **Request & Document Size Limits:** Adjusts max request size to 4GB and document size to 50MB.
- **Runs on All Cluster Nodes:** Ensures consistency across all CouchDB instances.

### Usage


#### **1. Edit the Taskfile Variables (If Needed)**
Modify `Taskfile.yaml` with your **CouchDB URL** and **admin credentials**:
```yaml
vars:
  COUCHDB_URL: "https://cdb.homelab.pk"
  COUCHDB_ADMIN: "your_admin_username"
  COUCHDB_PASSWORD: "your_admin_password"
  DB_NAME: "database-name"
```

#### **2. Run the Full Setup**
This will apply all configurations across all nodes.
```sh
task full-setup
```
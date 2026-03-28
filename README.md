# SAP BTP Integration Suite — Enterprise Integration

This repository demonstrates an **end-to-end SAP BTP Integration Suite implementation** that connects enterprise systems using SAP Cloud Integration (CPI), API Management, and event-driven architecture.

The project simulates how modern SAP integration teams design, build, monitor, and manage integrations across hybrid landscapes.

---

# Project Goal

The objective of this project is to implement a **complete SAP integration lifecycle**, including:

* iFlow design and development
* Adapter configuration (REST, OData, SFTP, SOAP)
* Data transformation using Message Mapping and Groovy
* Error handling and retry patterns
* API Management — proxy, policies, security
* Monitoring and observability
* End-to-end S/4HANA to Salesforce integration

---

# Architecture Overview

```
Sender System (Salesforce / External API)
   ↓
HTTPS Adapter (Sender)
   ↓
SAP Integration Suite — Cloud Integration
   ↓  Message Mapping + Groovy Transformation
   ↓  Error Handling + Retry Logic
OData Adapter (Receiver)
   ↓
SAP S/4HANA
   ↓
API Management — Proxy + Policies
   ↓
External Consumer
```

---

# Technology Stack

| Category | Tools |
| --- | --- |
| Integration Platform | SAP BTP Integration Suite |
| Core Component | SAP Cloud Integration (CPI) |
| API Layer | SAP API Management |
| Sender Adapters | HTTPS, SFTP, SOAP |
| Receiver Adapters | OData, HTTPS, SFTP, Mail |
| Scripting | Groovy, XSLT |
| Data Formats | JSON, XML, CSV |
| SAP Backend | SAP S/4HANA (OData APIs) |
| External Systems | Salesforce, REST APIs |
| Security | OAuth2, Certificate-based, Basic Auth |

---

# Repository Structure

```
sap-btp-integration-suite
│
├── 01-api-fundamentals
│   ├── JSON and XML structure samples
│   ├── Postman collections for CRUD operations
│   └── REST API exercises
│
├── 02-iflows
│   └── Exported iFlow configurations with documentation
│
├── 03-groovy-scripts
│   └── Reusable Groovy scripts for payload, headers, logging
│
├── 04-message-mapping
│   └── JSON to XML and XML to JSON transformation samples
│
├── 05-error-handling
│   └── Exception subprocess, retry, dead letter queue patterns
│
├── 06-api-management
│   └── API proxy configs and policy templates
│
└── 07-capstone
    └── End-to-end S/4HANA to Salesforce integration
```

---

# Integration Workflow

1. External system sends data via REST API to Integration Suite endpoint.
2. HTTPS sender adapter receives the incoming message.
3. Content modifier sets required headers and properties.
4. Message mapping transforms JSON payload to SAP XML structure.
5. Groovy script applies custom business logic and validation.
6. OData receiver adapter sends transformed data to SAP S/4HANA.
7. Exception subprocess handles errors and triggers retry.
8. Mail adapter sends failure notification on unrecoverable error.
9. API Management layer exposes iFlow as a managed, secured API.
10. Monitoring dashboard tracks message processing logs and alerts.

---

# API Management

The API layer includes:

* **API Proxy** — Exposes integration endpoints as managed APIs
* **Spike Arrest** — Protects backend from traffic spikes
* **Rate Limiting** — Controls consumer request quotas
* **OAuth2 Verification** — Validates access tokens on incoming calls
* **Mediation Policies** — Request/response transformation at gateway level

---

# Key Integration Concepts Demonstrated

* Sender and receiver adapter configuration
* Synchronous and asynchronous message processing
* Content-based routing
* Splitter and aggregator patterns
* Idempotent receiver pattern
* Exception subprocess with retry
* Security material management
* iFlow versioning and transport

---

# Final Outcome

This project simulates a **real enterprise SAP integration workflow**:

```
External System → Integration Suite → SAP S/4HANA → API Management → Consumer
```

It demonstrates how modern SAP integration pipelines are designed and implemented using cloud-native SAP BTP capabilities and is built to be explainable and reproducible.

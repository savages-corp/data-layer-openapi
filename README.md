# European Financial Data Layer (EFDL) OpenAPI specifications

This repository contains the OpenAPI specifications for the European Financial Data Layer (EFDL) integrations.

## EFDL Generic HTTP Service API

### Overview

The EFDL Generic HTTP Service API is a crucial component of the EFDL (European Financial Data Layer) system, designed to streamline data synchronization across various services. EFDL acts as an intermediary data layer that facilitates the pulling and pushing of data between different sources and destinations, such as CRM systems like Salesforce and HubSpot, as well as custom internal systems.

### Goals

The primary goals of this API specification are:

1. **Data Synchronization**: Enable seamless data synchronization between diverse services to eliminate data silos and enhance data consistency across organizational tools.

2. **Interoperability**: Provide a flexible interface that supports both standard and custom integrations, allowing organizations to tailor the data flow according to their specific needs.

3. **Scalability**: Support large-scale data operations for enterprise environments, ensuring efficient handling of data migrations, integrations, and analytics.

4. **Customization**: Allow customers to set up their own HTTP servers using this specification, offering granular control over data exposure and integration with EFDL.

### Key Features

- **Service Integration**: EFDL provides basic implementations for popular services such as Salesforce. It also supports custom integrations for unique customer environments.

- **Generic HTTP Service**: This specification enables customers with internal systems to set up HTTP endpoints that EFDL can connect to, facilitating data exchange.

- **Data Translation**: As data is retrieved from one service and sent to another, EFDL translates data formats to ensure compatibility and integrity.

- **Data Mapping**: EFDL allows customers to map data fields between different services, ensuring that data is correctly aligned and synchronized in a meaningful way, even across disparate systems.

### API Structure

The API is structured around the following key resources:

- **Accounts**: Manage personal and business accounts, including contact and billing information.
- **Contracts**: Handle contracts for devices and vehicles, with details on compliance, identification, and payment.
- **Claims**: Process insurance claims, tracking details from filing to resolution.
- **Financial Transactions**: Record and retrieve financial transactions related to accounts.

### Endpoints

#### Accounts

- `GET /accounts`: Retrieve a list of accounts.
- `POST /accounts`: Upsert (create or update) an account.

#### Contracts

- `GET /contracts`: Retrieve a list of contracts.
- `POST /contracts`: Upsert (create or update) a contract.

#### Claims

- `GET /claims`: Retrieve a list of claims.
- `POST /claims`: Upsert (create or update) a claim.

#### Transactions

- `GET /transactions`: Retrieve a list of financial transactions.
- `POST /transactions`: Upsert (create or update) a transaction.

### Error Handling

The API provides detailed error messages and uses standard HTTP status codes to indicate the success or failure of an operation. Common statuses include:

- `200 OK`: Successful retrieval or update.
- `201 Created`: Successful creation of a new resource.
- `400 Bad Request`: Invalid request parameters or data.
- `500 Internal Server Error`: An unexpected error occurred on the server.

### Contact

For more information or support, please contact:

- **Name**: Andrew Lake
- **Email**: <a.lake@savagescorp.com>

---

This specification is part of Savages Corp's commitment to providing robust and flexible data integration solutions that empower organizations to manage their data effectively across diverse systems and platforms.

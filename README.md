# Data Layer OpenAPI Specification

<https://data-layer.com>

Data Layer acts as an intermediary data layer that facilitates the pulling and pushing of data between different sources and destinations, such as CRM systems like Salesforce and HubSpot, as well as custom internal systems.

The core concepts of Data Layer are:

- **Deterministic Data Flow**: Data Layer ensures that data flows in a deterministic manner, maintaining consistency and integrity across different systems.

- **Error Handling**: Data Layer halts data flow in case of errors, ensuring that data is not lost or corrupted during synchronization.

- **Data Normalization**: Data Layer comes with predefined data models that represent common entities such as accounts, contracts, claims, and financial transactions.

- **Data Warehouse**: Data Layer has the capability to store normalized data in a data warehouse layer, creating a single source of truth for data across different systems.

- **Connectors**: Data Layer provides pre-built connectors to popular services, allowing customers to easily integrate various systems.

A service in Data Layer is a logical entity that represents a data source or destination. Services can be external systems like Salesforce or internal systems like a custom CRM. A service provides pulling and pushing capabilities for data, allowing Data Layer to synchronize data between different services seamlessly.

The **Data Layer Generic HTTP Service** is a crucial component of the Data Layer system, designed to allow customers and integration partners to set up their own HTTP servers that Data Layer can connect to. This enables data exchange between Data Layer and internal systems, providing a flexible and customizable solution for data synchronization at scale.

## Goals

The primary goals of this API specification are:

1. **Data Synchronization**: Enable seamless data synchronization between diverse services to eliminate data silos and enhance data consistency across organizational tools.

2. **Interoperability**: Provide a flexible interface that supports both standard and custom integrations, allowing organizations to tailor the data flow according to their specific needs.

3. **Scalability**: Support large-scale data operations for enterprise environments, ensuring efficient handling of data migrations, integrations, and analytics.

4. **Customization**: Allow customers to set up their own HTTP servers using this specification, offering granular control over data exposure and integration with Data Layer.

## Key Features

- **Service Integration**: Data Layer provides basic implementations for popular services such as Salesforce. It also supports custom integrations for unique customer environments.

- **Generic HTTP Service**: This specification enables customers with internal systems to set up HTTP endpoints that Data Layer can connect to, facilitating data exchange.

- **Data Translation**: As data is retrieved from one service and sent to another, Data Layer translates data formats to ensure compatibility and integrity.

- **Data Mapping**: Data Layer allows customers to map data fields between different services, ensuring that data is correctly aligned and synchronized in a meaningful way, even across disparate systems.

- **Data Expulsion**: Data Layer provides mechanisms to expel data from the system, ensuring compliance with data privacy regulations and organizational policies.

## API Structure

The API is structured around the following key resources:

- **Accounts**: Manage personal and business accounts, including contact and billing information.
- **Contracts**: Handle contracts for devices and vehicles, with details on compliance, identification, and payment.
- **Claims**: Process insurance claims, tracking details from filing to resolution.
- **Financial Transactions**: Record and retrieve financial transactions related to accounts.

## Endpoints

### Accounts

- `GET /accounts`: Retrieve a list of accounts.
- `PUT /accounts`: Upsert (create or update) an account.

### Contracts

- `GET /contracts`: Retrieve a list of contracts.
- `PUT /contracts`: Upsert (create or update) a contract.

### Claims

- `GET /claims`: Retrieve a list of claims.
- `PUT /claims`: Upsert (create or update) a claim.

### Transactions

- `GET /transactions`: Retrieve a list of financial transactions.
- `PUT /transactions`: Upsert (create or update) a transaction.

## Error Handling

The API provides detailed error messages and uses standard HTTP status codes to indicate the success or failure of an operation. Common statuses include:

- `200 OK`: Successful retrieval or update.
- `201 Created`: Successful creation of a new resource.
- `400 Bad Request`: Invalid request parameters or data.
- `500 Internal Server Error`: An unexpected error occurred on the server.

## Anonymizing / Expunging Data

To remove data from any downstream systems, the API provides the `_anonymized` and `_expunged` fields in the request payload. Setting these field to `true` will mark the corresponding record as anonymized or expunged for transport into downstream systems and optionally the data warehouse. Both variations will cause the record to not be physically deleted. Depending on the flag, either personally identifiable information (PII) is removed (anonymized) or all data except for data identifiers is cleared (expunged). This ensures that the record's data is not accessible in any downstream systems, while still maintaining data integrity as well as a record referencing the original data for audit purposes.

## Contact

For more information or support, please contact:

- **Name**: Andrew Lake
- **Email**: <a.lake@savagescorp.com>

- **Name**: Robert Konarskis
- **Email**: <rk@savagescorp.com>

## Validate the Specification

```
npx @redocly/cli lint ./openapi.yaml --extends recommended-strict
```

---

This specification is part of Savages Corp's commitment to providing robust and flexible data integration solutions that empower organizations to manage their data effectively across diverse systems and platforms.

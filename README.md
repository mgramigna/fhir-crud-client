# FHIR CRUD Client

A lightweight Promise-based JavaScript FHIR client for CRUD operations

* `read`
* `create`
* `update`
* `delete`
* `search`
* `transaction`

Additionally, the client exposes `FHIRClient.metadata()` function for triggering a metadata request, and `FHIRClient.setAuthToken()` for setting an Authorization token

## Installation

``` bash
npm install --save fhir-crud-client
```

``` bash
yarn add fhir-crud-client
```

## Usage

``` JavaScript
const { FHIRClient } = require('fhir-crud-client');

const BASE_URL = 'http://your-server-url';
const HEADERS = {
  Accept: 'application/json',
};

const client = new FHIRClient(BASE_URL, HEADERS);
```

### read

``` JavaScript
// Read a resource

// With async/await
const resource = await client.read({ resourceType: 'Patient', id: 'my-patient' });
console.log(resource);

// With Promises
client.read({ resourceType: 'Patient', id: 'my-patient' })
  .then((resource) => {
    console.log(resource);
  });
```

### create

``` JavaScript
// Create a resource

// With async/await
const resource = await client.create({ resourceType: 'Patient', body: myPatientJson });
console.log(resource);

// With Promises
client.create({ resourceType: 'Patient', body: myPatientJson })
  .then((resource) => {
    console.log(resource);
  });
```

### update

``` JavaScript
// Update a resource

// With async/await
const resource = await client.update({ resourceType: 'Patient', id: 'my-patient', body: myModifiedPatient });
console.log(resource); // resource is the updated Patient

// With Promises
client.update({ resourceType: 'Patient', id: 'my-patient', body: myModifiedPatient })
  .then((resource) => {
    console.log(resource); // resource is the updated Patient
  });
```

### delete

``` JavaScript
// Delete a resource

// With async/await
const resource = await client.delete({ resourceType: 'Patient', id: 'my-patient' });
console.log(resource); // resource is an OperationOutcome

// With Promises
client.delete({ resourceType: 'Patient', id: 'my-patient' })
  .then((resource) => {
    console.log(resource); // resource is an OperationOutcome
  });
```

### search

``` JavaScript
// Search for resources

// With async/await
const bundle = await client.search({ resourceType: 'Patient', params: { family: 'test' } });
console.log(bundle);

// With Promises
client.search({ resourceType: 'Patient', params: { family: 'test' } })
  .then((bundle) => {
    console.log(bundle);
  });
```

### transaction

``` JavaScript
// Upload a transaction Bundle

// With async/await
const bundle = await client.transaction({ body: aTransactionBundle });
console.log(bundle);

// With Promises
client.search({ body: aTransactionBundle })
  .then((bundle) => {
    console.log(bundle);
  });
```

### metadata

``` JavaScript
// Make a get request to `BASE_URL/metadata`

// With async/await
const response = await client.metadata();
console.log(response);

// With Promises
client.metadata()
  .then((response) => {
    console.log(response);
  });
```

### setAuthToken

``` JavaScript
// Set an authorization token on the HTTP Client

client.setAuthToken(TOKEN_GOES_HERE)
```

### updateRequestHeaders

``` JavaScript
// Update the request headers of our HTTP Client

client.updateRequestHeaders(NEW_HEADERS)
```

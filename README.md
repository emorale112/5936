# api.gusto.dev

The Open API specification for the Gusto API lives here.
The developer documentation is generated from this specification by [ReDoc](https://github.com/Rebilly/ReDoc).

## OpenAPI (OAI) Specification
- The openapi specification for the Gusto API lives in `swagger-spec/swagger.yaml` and contains references to many YAML files in the `swagger-spec` directory.

### Editing the OAI Specification

- As a general rule, the `swagger.yaml` file should be kept **as minimal as possible**, meaning `$refs` to other YAML files should be utilized over inline endpoint and model definitions.
- Each collection of related endpoints is contained in it's own folder in the `swagger-spec` directory (i.e., `swagger-spec/employees/`), with each unique API endpoint having it's own YAML file (i.e., `detail.yaml` and `list.yaml` for `/employees/` and `/employees/{employee_id}/`, respectively).
- The specification should *always* conform to the official OpenAPI specification (v2.0), described in detail [here](http://swagger.io/specification/).

## Development

- `yarn`
- `yarn run build` (spec validation)
- `yarn run serve` (serves at localhost:8080)
  - OR `yarn run watch` (serves at localhost:8080 with livereload)
- `yarn run sass` (compile and watch sass changes)

## Spec validation

```
yarn run build
```

## Starting a local server

```
yarn run serve
```

## TODO 
- [ ] Updating payrolls example 

- [X] Syncing employees

- [X] Authentication

- [X] Versioning

- [ ] Current user 

- [X] GET company 

- [X] GET company locations
- [X] POST company locations

- [X] GET single EE
- [X] GET EEs for a company 
- [X] PUT EE
- [X] POST EE

- [X] GET EE's home address
- [X] PUT EE's home address

- [X] GET time off requests 

- [X] GET a single job
- [X] GET jobs for an EE
- [ ] PUT update a job 
- [ ] POST create a job 

- [ ] GET a single compensation
- [ ] GET compensations for a job
- [ ] PUT update a compensation 
- [ ] POST create a compensation

- [ ] GET a single garnishment
- [ ] GET garnishments for an EE
- [ ] PUT update a garnishment 
- [ ] POST create a garnishment

- [ ] GET a single termination
- [ ] GET terminations for an EE
- [ ] PUT update a termination 
- [ ] POST create a termination

- [ ] GET pay schedule
- [ ] GET pay schedules for a company 

- [ ] GET pay periods for a company 

- [ ] GET a specific payroll
- [ ] GET a compnay's payrolls
- [ ] PUT update a payroll

- [ ] GET supported benefits 

- [ ] GET a single company benefit
- [ ] GET company benefits for a company
- [ ] PUT update a company benefit 
- [ ] POST create a company benefit

- [ ] GET a single EE benefit
- [ ] GET benefits for an EE
- [ ] PUT update an EE benefit 
- [ ] POST create an EE benefit
- [ ] DELETE delete an EE benefit

- [ ] GET a location by ID
- [ ] PUT update a location by ID

- [X] State endpoint

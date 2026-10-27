# ODA Components and Canvas

## Component definition (IG1171)
A component declares four parts:
| Part | Content |
|---|---|
| Core function | Exposed Open APIs, dependent Open APIs, published and subscribed events |
| Management function | Observability and management interfaces (metrics, configuration) |
| Security function | Party role exposure (TMF669) and identity integration |
| Metadata | Component name, ID, version, functional block |

## Component manifest skeleton (illustrative)
Field names follow the public design guidelines in `tmforum-oda/oda-ca-docs`. The `apiVersion` evolves. Check the current Canvas release before use.

```yaml
apiVersion: oda.tmforum.org/v1beta2   # verify current version
kind: component
metadata:
  name: acme-productcatalog
  labels:
    oda.tmforum.org/componentName: acme-productcatalog
    oda.tmforum.org/functionalBlockName: CoreCommerce
spec:
  type: productcatalog
  version: 1.0.0
  description: "Product catalog component"
  coreFunction:
    exposedAPIs:
      - name: productcatalogmanagement
        specification: TMF620 OAS file URL
        implementation: acme-productcatalog-svc
        path: /acme-productcatalog/tmf-api/productCatalogManagement/v4
        port: 8080
    dependentAPIs:
      - name: party
        specification: TMF632 OAS file URL
  managementFunction:
    exposedAPIs: []
  securityFunction:
    controllerRole: Admin
    exposedAPIs:
      - name: partyrole
        specification: TMF669 OAS file URL
```

## Canvas
- Kubernetes environment with operators that read component custom resources.
- Operators configure API gateway exposure, identity provider roles, and observability.
- Component CTK validates that declared APIs exist and conform.

## Readiness labels
- Ready for ODA and Running on ODA are TM Forum programs. Verify a vendor's listing in the ODA Component Directory.

## Sources
- Component design guidelines: https://github.com/tmforum-oda/oda-ca-docs
- ODA Component Directory: https://www.tmforum.org/oda/directory/

# 3rd-Party Integrations

## AWS Icons

Three versions of AWS icon wrappers are provided, each pulling sprites from the [aws-icons-for-plantuml](https://github.com/awslabs/aws-icons-for-plantuml) repository.

### AWS v14 (Recommended)

**Entry point:** `dist/3rdParty/aws14/AwsCommon.iuml`
**Upstream:** `awslabs/aws-icons-for-plantuml` v14.0

```plantuml
!define $COMPONENTS_PUML https://raw.githubusercontent.com/segFallt/plantUML-components/v2.0.1/dist
!include $COMPONENTS_PUML/3rdParty/aws14/AwsCommon.iuml

EC2(myInstance, "Web Server", "t3.micro")
```

Includes:
- `AwsCommon.iuml` - Base configuration, entity macros, and upstream AWSCommon.puml
- `AwsReferences.iuml` - Sprite includes for AWS services
- `AwsContainer.iuml` - Container elements (Cloud, VPC, Subnets, DataCenter)
- `AwsSimplified.iuml` - Simplified styling with hidden stereotypes

Pre-configured container macros: `CorporateDataCenter`, `Cloud`, `VirtualPrivateCloudVPC`, `ElasticKubernetesService`, `VPCSubnetPrivate`, `VPCSubnetPublic`.

### AWS v11

**Entry point:** `dist/3rdParty/aws/AwsCommon.iuml` or `dist/3rdParty/aws11/AwsCommon.iuml`
**Upstream:** `awslabs/aws-icons-for-plantuml` v11.1

Same structure as v14 but pulls from the v11.1 release. The `aws/` and `aws11/` directories contain the same library version.

---

## Azure 2.1

**Entry point:** `dist/3rdParty/azure2.1/azureCommon.iuml`
**Upstream:** [Azure-PlantUML](https://github.com/plantuml-stdlib/Azure-PlantUML) release/2-1

```plantuml
!define $COMPONENTS_PUML https://raw.githubusercontent.com/segFallt/plantUML-components/v2.0.1/dist
!include $COMPONENTS_PUML/3rdParty/azure2.1/azureCommon.iuml

AzureFunction(fn, "My Function", "Node.js")
AzureEventHub(hub, "Event Hub", "Standard")
```

Pre-includes: `AzureCommon.puml`, `AzureFunction.puml`, `AzureEventHub.puml`.

---

## Kubernetes

**Entry point:** `dist/3rdParty/kubernetes/KubernetesCommon.iuml`
**Upstream:** Custom sprites bundled in `KubernetesBase.iuml`

```plantuml
!define $COMPONENTS_PUML https://raw.githubusercontent.com/segFallt/plantUML-components/v2.0.1/dist
!include $COMPONENTS_PUML/3rdParty/kubernetes/KubernetesCommon.iuml

Deploy(myDeploy, "API", "v1.2")
Secret(mySecret, "DB Credentials", "Opaque")
StatefulSet(mySts, "Database", "PostgreSQL")
CustomResourceDefinition(myCrd, "MyResource", "v1alpha1")
```

Available entity macros: `Deploy`, `Secret`, `StatefulSet`, `CustomResourceDefinition`.

Additional files:
- `KubernetesRaw.iuml` - Transparent borders, simplified styling
- `KubernetesSimplified.iuml` - Hidden stereotypes, icon-only display

---

## PingIdentity

**Entry point:** `dist/3rdParty/pingIdentity/pingIdentityStyleAndComponents.iuml`

```plantuml
!define $COMPONENTS_PUML https://raw.githubusercontent.com/segFallt/plantUML-components/v2.0.1/dist
!include $COMPONENTS_PUML/3rdParty/pingIdentity/pingIdentityStyleAndComponents.iuml

PingContainer(ping, "PingFederate", "Authentication Server")
PingAdapterContainer(adapter, "HTML Form Adapter", "Login")
PingSelectorContainer(selector, "IdP Selector", "Routing")
```

Provides PingIdentity and PingFedAdapter sprites with styled containers.

---

## OAuth2 Auth Flows

**Entry point:** `dist/3rdParty/auth.iuml`

Provides sequence diagram procedures for common OAuth2/OIDC authentication flows.

```plantuml
!define $COMPONENTS_PUML https://raw.githubusercontent.com/segFallt/plantUML-components/v2.0.1/dist
!include $COMPONENTS_PUML/3rdParty/auth.iuml

$internalClientCredentialAuth(Client, AuthServer, "Service Auth", "scope=api")
$introspectToken(ResourceServer, AuthServer, "Token Validation", "")
```

### Available Procedures

| Procedure | Description |
|-----------|-------------|
| `$internalClientCredentialAuth($client, $server, $context, $requestNote)` | Client credentials grant flow |
| `$validateBearerToken($client, $server, $context, $requestNote)` | Token validation via `/oauth2/token/validate` |
| `$introspectToken($client, $server, $context, $requestNote)` | Token introspection via `/oauth2/as/introspect.oauth2` |
| `$jwksLocalValidateToken($client, $server, $context, $requestNote)` | Local JWT validation using JWKS public keys |
| `$tokenExchange($client, $server, $context, $requestNote)` | OAuth2 token exchange (RFC 8693) |
| `$PrintPingAuthorizeRequestDataContractNote($participant)` | Adds a link note to PingAuthorize data contract docs |

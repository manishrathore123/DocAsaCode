<h1 align="center"><strong>Design REST API </strong></h1>

## [![](../../../images/pin.svg)](#table-of-contents) Table of contents

- [ Table of contents](#-table-of-contents)
- [ Design API](#-design-api)
- [ Validate API specification](#-validate-api-specification)
  - [Github action:](#github-action)
  - [CLI:](#cli)
  - [npm package:](#npm-package)
- [ FAQ](#-faq)

## [![](./../../../images/pin.svg)](#design-api) Design API

While designing follow [Ingka API Standards](https://github.com/ingka-group-digital/api-standards) to understand REST API design principle for Ingka. There are few additional rules to consider which is specific to Managed API gateway which can be found here
[managed gateway rules](https://github.com/ingka-group-digital/api-standards/blob/main/docs/WebAPI/manage-api-gw.md)

## [![](./../../../images/pin.svg)](#validate-api-specification) Validate API specification

There is [lint-openapi tool](https://github.com/ingka-group-digital/lint-openapi/blob/main/README.md) available to validate the API specification file. It can be used as:

- Github Action
- CLI command
- npm package

\*\*\* Note: You can validate the API specification document with or without specific gateway rules. These gateway rules are unique and are applied to ensure that the API specification adheres to the standards required for the Central Gateway (Kong).

To facilitate this validation process, we've introduced a boolean flag that can be set to either 'true' or 'false.' When this flag is set to 'true,' the special gateway rules will be applied during validation. It is highly recommended to set this flag to 'true' when deploying your API on the Central Gateway, as it ensures compliance with the required standards.

### Github action:

You can validate your API specification file with below github actions.

- Without applying gateway specific rules

```bash
- uses: ingka-group-digital/lint-openapi@v1.0.1
    with:
      files: |
        <file-1-path>
        <file-2-path>

```

- Apply gateway specific rules

```bash
- uses: ingka-group-digital/lint-openapi@v1.0.1
    with:
      files: |
        <file-1-path>
        <file-2-path>
      shouldApplyGatewayRules: true

```

Please refer <a href="https://github.com/ingka-group-digital/lint-openapi/blob/main/README.md">lint-openapi</a> to know more.

### CLI:

You can simply use the CLI command also to validate your API Specification file. Below is the sample CLI command to use it.

- Without applying gateway specific rules

```bash
lint-openapi <file-path>
```

- Apply gateway specific rules

```bash
lint-openapi <file-path> true
```

Please refer <a href="https://github.com/ingka-group-digital/lint-openapi/blob/main/README.md">lint-openapi</a> to know more.

### npm package:

The latest npm package is uploaded in JFrog repository

- (https://artifactory.build.ingka.ikea.com/artifactory/api/npm/ingka-npm-shared-local///artifactory.build.ingka.ikea.com/artifactory/api/npm/ingka-npm-shared-local) .

- This can be used in code using the authentication token.

- Below is the code snippet which you can use in your code with the npm package

- Without applying gateway specific rules

```bash
import { lintFromString } from '@ingka-group-digital/lint-openapi';
const stringifiedOpenApiSpec = 'stringified-openapi-spec';
const linterOutput = await lintFromString(stringifiedOpenApiSpec);
```

- Apply gateway specific rules

```bash
import { lintFromString } from '@ingka-group-digital/lint-openapi';
const stringifiedOpenApiSpec = 'stringified-openapi-spec';
const linterOutput = await lintFromString(stringifiedOpenApiSpec,true);
```

Please refer <a href="https://github.com/ingka-group-digital/lint-openapi/blob/main/README.md">lint-openapi</a> to know more.

## [![](./../../../images/pin.svg)](#faq) FAQ

coming soon...

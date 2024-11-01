# API Lifecycle
API Lifecycle is a machine-readable definition of the agreed upon stages of the lifecycle for an API from start to finish, providing an agreed upon set of terms for describing the API lifecycle, what order the stages occur, but also which API policies matter at each stage, helping teams producing and consuming APIs understand what is next.

The API lifecycle for delivering APIs.io is available as a single YAML file, which uses the [API Commons lifecycle schema](https://github.com/api-commons/lifecycle) to automate governance at different stages. This schema provides a common way to communicate and automate across all stages of the API lifecycle across many different teams.

## API Commons
API Lifecycle is a new [API Commons](https://apicommons.org) schema which is associated with API policies at the stage level, allowing for a bridge to experience, rules, and guidance in a specific order for each stage of the API lifecycle, providing a flexible, yet strongly typed approach to agreeing upon what gets done in what order, and what comes next with delivering APIs

## Example ([lifecycle-example-1](lifecycle-example-1.yml))

```
define:
  name: Define
  description: This stage is where you define the business requirements for the API.
  image: /images/define.png
  policies:
    - github-organization
    - github-repository
    - postman-workspace 
    - teams
    - standards   
    - use-cases
    - contract-metadata
    - api-metadata
    - road-map
    - change-log 
    - questions   
    - governance
  guidance: lifecycle/define
design:
  name: Design
  description: This stage is where you design the schema and OpenAPI for the API.
  image: /images/design.png
  policies:
    - openapi
    - openapi-components 
    - openapi-path-names
    - openapi-operation-identifiers
    - openapi-operation-summary
    - openapi-operation-description
    - openapi-operation-request-bodies
    - openapi-operation-request-bodies-media-types
    - openapi-operation-request-bodies-schema
    - openapi-operation-parameters
    - openapi-operation-parameter-in
    - openapi-operation-parameter-names
    - openapi-operation-parameter-descriptions
    - openapi-operation-parameter-types
    - openapi-operation-parameter-schema
    - openapi-operation-parameter-enum
    - openapi-operation-tags
    - openapi-operation-security
    - openapi-operation-response-2xx
    - openapi-operation-response-2xx-media-types
    - openapi-operation-response-2xx-schema
    - openapi-operation-response-2xx-examples
    - openapi-operation-response-4xx
    - openapi-operation-response-4xx-media-types
    - openapi-operation-response-4xx-schema
    - openapi-operation-response-4xx-examples
    - openapi-operation-response-5xx
    - openapi-operation-response-5xx-media-types
    - openapi-operation-response-5xx-schema
    - openapi-operation-response-5xx-examples
    - openapi-schema-type
    - openapi-schema-names
    - openapi-schema-descriptions
    - openapi-schema-property-names
    - openapi-schema-property-descriptions
    - openapi-schema-property-types
    - openapi-schema-property-enums
    - openapi-schema-property-required
    - openapi-schema-property-shapes
    - postman-collection
    - documentation   
  guidance: lifecycle/design    
develop:
  name: Develop
  description: This stage is where you develop the code and database for the API.
  image: /images/develop.png
  policies:
    - openapi-security  
    - source-of-truth-actions
    - base-url
    - sdks
  guidance: lifecycle/develop
staging:
  name: Staging
  description: This stage is where you deploy the code for the API to staging.
  image: /images/staging.png
  policies:
    - human-url
    - portals
    - getting-started
    - plans    
    - status
    - performance 
  guidance: lifecycle/staging    
production:
  name: Production
  description: This stage is where you deploy the code for the API to production.
  image: /images/production.png
  policies:
    - support 
    - feedback 
    - blogs
    - blog-feeds
    - videos
    - terms-of-service
    - privacy-policy 
    - licensing      
  guidance: lifecycle/production      
```

## JSON Schema ([lifecycle-json-schema](lifecycle-json-schema.yml))

```
"$schema": http://json-schema.org/2020-12/schema
type: object
description: A machine-readable scaffolding for the API lifecycle.
properties:
  "^(label_name_[0-9]+)+$"":
    "$ref": "#/$defs/Stage"

"$defs":

  Stage:
    type: object
    description: A representation of an individual lifecycle stage.
    properties:
      name:
        type: string
        description: The name of the stage being defined.
      description:
        type: string
        description: A more detailed overview of the stage.
      image:
        type: string
        description: An image to represent the stage.
      policies:
        type: array
        description: The policies that apply to the stage.
        items:
          - type: string
      guidance:
        type: string
        description: The guidance that applies to this stage.
    required:
    - name
    - description
    - image
    - policies
    - guidance
```

# API Policies, Rules, Experience, and Guidance
API Lifecycle schema are associated with policies, which then can also provide the bridge to the rules used to lint the business and technical contracts in place for APIs, offering another dimension to view API governance, helping build more awareness with teams about what is expected of them at any given stage in a consistent way across teams.

<img src="https://kinlane-productions2.s3.us-east-1.amazonaws.com/policies-rules-guidance-experience-lifecycle.jpg">

This work acknowledges that services, tooling, and the general approach of API governance is only using rules applied to OpenAPI, which is beginning to expand to AsyncAPI, GraphQL, and Arazzo workflows, but is proposing the first schema for aligning this work with business objectives, when teams are ready for it.

## Support
This work is in early stage of development and rapidly moving as they are being applied in a variety of user interfaces and approaches to the automation and reporting of API governance. If you would like to contribute, have any questions, or would like to inform the work happening, please submit a GitHub issue on the repository or email kin@apievangelist.com.

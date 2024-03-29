# API Guidelines

- [API Guidelines](#api-guidelines)
  - [General Guidelines](#general-guidelines)
  - [API Design](#api-design)
  - [Meta information](#meta-information)
  - [Security](#security)
  - [Data formats](#data-formats)
  - [URLs](#urls)
  - [JSON payload](#json-payload)
  - [HTTP requests](#http-requests)
  - [HTTP status codes](#http-status-codes)
  - [HTTP headers](#http-headers)
  - [Hypermedia](#hypermedia)
  - [Pagination](#pagination)
  - [Compatibility](#compatibility)
  - [Deprecation](#deprecation)
  - [REST Operation](#rest-operation)

Our API Guidelines are based on the Zalando
[RESTful API and Event Scheme Guidelines](https://opensource.zalando.com/restful-api-guidelines).

If you are not familiar with the Zalando API Guidelines, we recommend you to read them first.

Here you can find the main rules and differences between our API Guidelines and the
Zalando API Guidelines.

## General Guidelines

The first read our [Principles](./principles.md).

There you find all the general rules and conventions for API design.

**MUST** follow the API-First principle:

- Define APIs first, before coding its implementation, using a standard specification language.
- Design APIs using our [API Guidelines](./guidelines.md).
- Use [Spectral](https://github.com/stoplightio/spectral) to validate your API design.
- Call for early review feedback from peers and client developers.

**MUST** provide API specification using [OpenAPI Specification 3.0](
https://spec.openapis.org/oas/v3.0.3.html).

*SHOULD* use the [Stoplight Studio](https://stoplight.io/studio/) to design and document our APIs.

**MUST** write APIs using U.S. English

*SHOULD* don't repeat yourself (The DRY principle).

>There's no need to specify the same property in different places in the     specification.
>
>Instead, move it to the `components` section and reference it from other places using `$ref.`

*SHOULD* split the document into several files.

>A good rule of thumb is to use the natural hierarchy present in URLs to build your file structure.
>
>For example, put all routes starting with /users (like /users and /users/{id}) in the same file
>(think of it as a “sub-API”).

## API Design

## Meta information

**MUST** contain API meta information
[218](https://opensource.zalando.com/restful-api-guidelines/#218).

**MUST** use semantic versioning
[116](https://opensource.zalando.com/restful-api-guidelines/#116).

## Security

**MUST** secure endpoints
[104](https://opensource.zalando.com/restful-api-guidelines/#104).

## Data formats

**MUST** use standard data formats
[238](https://opensource.zalando.com/restful-api-guidelines/#238).

**MUST** define a format for number and integer types
[171](https://opensource.zalando.com/restful-api-guidelines/#171).

**MUST** encode binary data in base64url

**MUST** use standard formats for date and time properties
[169](https://opensource.zalando.com/restful-api-guidelines/#169).

**MUST** use standard formats for country, language and currency properties
[170](https://opensource.zalando.com/restful-api-guidelines/#170).

*SHOULD* only use UUIDs if necessary
[144](https://opensource.zalando.com/restful-api-guidelines/#144).

## URLs

SHOULD not use /api as base path
[135](https://opensource.zalando.com/restful-api-guidelines/#135).

MUST pluralize resource names
[134](https://opensource.zalando.com/restful-api-guidelines/#134).

MUST use URL-friendly resource identifiers
[228](https://opensource.zalando.com/restful-api-guidelines/#228).

MUST use kebab-case for path segments 
[129](https://opensource.zalando.com/restful-api-guidelines/#129).

MUST use normalized paths without empty path segments and trailing slashes
[136](https://opensource.zalando.com/restful-api-guidelines/#136).

MUST keep URLs verb-free
[141](https://opensource.zalando.com/restful-api-guidelines/#141).

MUST avoid actions — think about resources
[138](https://opensource.zalando.com/restful-api-guidelines/#138).

> PUT /article-locks/{article-id}

SHOULD define useful resources
[140](https://opensource.zalando.com/restful-api-guidelines/#140).

**MUST** use domain-specific resource names
[142](https://opensource.zalando.com/restful-api-guidelines/#142).

> For example: "sales-order-items" is superior to "order-items" in that it clearly
> indicates which business object it represents.

**MUST** identify resources and sub-resources via path segments
[143](https://opensource.zalando.com/restful-api-guidelines/#143).

**MUST** use snake_case (never camelCase) for query parameters
[130](https://opensource.zalando.com/restful-api-guidelines/#130).

**MUST** stick to conventional query parameters
[137](https://opensource.zalando.com/restful-api-guidelines/#137).

## JSON payload

**MUST** use JSON as payload data interchange format
[167](https://opensource.zalando.com/restful-api-guidelines/#167).

SHOULD use standard media types
[172](https://opensource.zalando.com/restful-api-guidelines/#172).

SHOULD pluralize array names
[120](https://opensource.zalando.com/restful-api-guidelines/#120).

**MUST** property names must be snake_case (and never camelCase)
[118](https://opensource.zalando.com/restful-api-guidelines/#118).

> Rationale: No established industry standard exists, but many popular Internet
> companies prefer snake_case: e.g. GitHub, Stack Exchange, Twitter. Others, like
> Google and Amazon, use both - but not only camelCase. It’s essential to establish
> a consistent look and feel such that JSON looks as if it came from the same hand.

SHOULD declare enum values using UPPER_SNAKE_CASE string
[240](https://opensource.zalando.com/restful-api-guidelines/#240).

SHOULD name date/time properties with _at suffix
[235](https://opensource.zalando.com/restful-api-guidelines/#235).

MUST use same semantics for null and absent properties
[123](https://opensource.zalando.com/restful-api-guidelines/#123).

MUST not use null for boolean properties
[122](https://opensource.zalando.com/restful-api-guidelines/#122).

MUST use common field names and semantics
[174](https://opensource.zalando.com/restful-api-guidelines/#174).

MUST use the common address fields
[249](https://opensource.zalando.com/restful-api-guidelines/#249).

MUST use the common money object
[173](https://opensource.zalando.com/restful-api-guidelines/#173).

## HTTP requests

**MUST** use HTTP methods correctly
[148](https://opensource.zalando.com/restful-api-guidelines/#148).

**MUST** fulfill common method properties
[149](https://opensource.zalando.com/restful-api-guidelines/#149).

*SHOULD* consider to design POST and PATCH idempotent
[229](https://opensource.zalando.com/restful-api-guidelines/#229).

**MUST** define collection format of header and query parameters
[154](https://opensource.zalando.com/restful-api-guidelines/#154).

*SHOULD* design simple query languages using query parameters
[236](https://opensource.zalando.com/restful-api-guidelines/#236).

*SHOULD* design complex query languages using JSON or GraphQL
[237](https://opensource.zalando.com/restful-api-guidelines/#237).

**MUST** document implicit response filtering
[226](https://opensource.zalando.com/restful-api-guidelines/#226).

## HTTP status codes

**MUST** use official HTTP status codes
[243](https://opensource.zalando.com/restful-api-guidelines/#243).

**MUST** specify success and error responses
[151](https://opensource.zalando.com/restful-api-guidelines/#151).

*SHOULD* only use most common HTTP status codes
[150](https://opensource.zalando.com/restful-api-guidelines/#150).

**MUST** use most specific HTTP status codes
[220](https://opensource.zalando.com/restful-api-guidelines/#220).

**MUST** use code 207 for batch or bulk requests
[152](https://opensource.zalando.com/restful-api-guidelines/#152).

**MUST** use code 429 with headers for rate limits
[153](https://opensource.zalando.com/restful-api-guidelines/#153).

**MUST** support problem JSON
[176](https://opensource.zalando.com/restful-api-guidelines/#176).

**MUST** not expose stack traces
[177](https://opensource.zalando.com/restful-api-guidelines/#177).

## HTTP headers

MAY use standard headers
[133](https://opensource.zalando.com/restful-api-guidelines/#133).

*SHOULD* use kebab-case with uppercase separate words for HTTP headers
[132](https://opensource.zalando.com/restful-api-guidelines/#132).

**MUST** use Content-* headers correctly
[178](https://opensource.zalando.com/restful-api-guidelines/#178).

## Hypermedia

MUST use REST maturity level 2
[162](https://opensource.zalando.com/restful-api-guidelines/#162).

MUST use common hypertext controls
[164](https://opensource.zalando.com/restful-api-guidelines/#164).

MUST use full, absolute URI for resource identification
[217](https://opensource.zalando.com/restful-api-guidelines/#217).

MUST not use link headers with JSON entities
[166](https://opensource.zalando.com/restful-api-guidelines/#166).

## Pagination

**MUST** support pagination
[159](https://opensource.zalando.com/restful-api-guidelines/#159).

*SHOULD* prefer cursor-based pagination, avoid offset-based pagination
[160](https://opensource.zalando.com/restful-api-guidelines/#160).

*SHOULD* use pagination response page object
[248](https://opensource.zalando.com/restful-api-guidelines/#248).

*SHOULD* use pagination links where applicable
[161](https://opensource.zalando.com/restful-api-guidelines/#161).

## Compatibility

**MUST** not break backward compatibility
[106](https://opensource.zalando.com/restful-api-guidelines/#106).

**MUST** prepare clients to accept compatible API extensions
[108](https://opensource.zalando.com/restful-api-guidelines/#108).

*SHOULD* avoid versioning
[113](https://opensource.zalando.com/restful-api-guidelines/#113).

**MUST** use media type versioning
[114](https://opensource.zalando.com/restful-api-guidelines/#114).

```html
Content-Type: application/x.<custom-media-type>+json;version=<version>
```

**MUST** not use URL versioning
[115](https://opensource.zalando.com/restful-api-guidelines/#115).

**MUST** always return JSON objects as top-level data structures
[110](https://opensource.zalando.com/restful-api-guidelines/#110).

## Deprecation

**MUST** reflect deprecation in API specifications
[187](https://opensource.zalando.com/restful-api-guidelines/#187).

**MUST** obtain approval of clients before API shut down
[185](https://opensource.zalando.com/restful-api-guidelines/#185).

**MUST** monitor usage of deprecated API scheduled for sunset
[188](https://opensource.zalando.com/restful-api-guidelines/#188).

*SHOULD* add Deprecation and Sunset header to responses
[189](https://opensource.zalando.com/restful-api-guidelines/#189).

*SHOULD* add monitoring for Deprecation and Sunset header
[190](https://opensource.zalando.com/restful-api-guidelines/#190).

**MUST** not start using deprecated APIs
[191](https://opensource.zalando.com/restful-api-guidelines/#191).

## REST Operation

**MUST** publish OpenAPI specification
[192](https://opensource.zalando.com/restful-api-guidelines/#192).

*SHOULD* monitor API usage
[193](https://opensource.zalando.com/restful-api-guidelines/#193).

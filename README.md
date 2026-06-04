# CoCart OpenAPI Specifications

This repository contains the [OpenAPI 3.0.3](https://www.openapis.org/) specifications for the [CoCart](https://cocartapi.com/) REST API

Specifications are organized by plugin and API version. Each plugin directory contains either a **collection file** (all endpoints in one spec) or **endpoint-specific files**.

## Plugins

The core CoCart plugin provides cart management, product browsing, session administration, authentication, and store information endpoints.

### CoCart Basic Edition — API v2 (Latest)

The latest specifications, reflecting CoCart Basic **v5.0.0**.

| File | Description | Endpoints |
|------|-------------|-----------|
| [Collection](basic/v2/openapi-cocart-v2-collection.yaml) | All v2 endpoints in a single spec | All below |
| [Cart](basic/v2/openapi-cocart-cart-v2.yaml) | Cart operations — create, add/update/remove items, totals, calculate | 10 paths |
| [Products](basic/v2/openapi-cocart-products-v2.yaml) | Products, variations, categories, tags, attributes, brands, reviews | 22 paths |
| [Sessions](basic/v2/openapi-cocart-sessions-v2.yaml) | Admin cart session management | 3 paths |
| [Others](basic/v2/openapi-cocart-others-v2.yaml) | Login, logout, and store information | 3 paths |

### CoCart Community Edition — API v2

Stable community release specifications, reflecting CoCart **v4.9.0**.

| File | Description | Endpoints |
|------|-------------|-----------|
| [Collection](community/v2/openapi-cocart-v2-stable.yaml) | All v2 endpoints in a single spec | All below |
| [Cart](community/v2/openapi-cocart-cart-v2.yaml) | Cart operations | 10 paths |
| [Products](community/v2/openapi-cocart-products-v2.yaml) | Products, variations, categories, tags, attributes, reviews | 14 paths |
| [Sessions](community/v2/openapi-cocart-sessions-v2.yaml) | Admin cart session management | 2 paths |
| [Others](community/v2/openapi-cocart-others-v2.yaml) | Login, logout, and store information | 3 paths |

### CoCart Community Edition — API v1

> [!IMPORTANT]
> No longer supported. Legacy v1 API specifications, reflecting CoCart **v4.9.0**.

| File | Description | Endpoints |
|------|-------------|-----------|
| [Cart](community/v1/openapi-cocart-cart-v1.yaml) | Cart operations — get cart, add/update/remove items, count, clear, totals | 10 paths |
| [Products](community/v1/openapi-cocart-products-v1.yaml) | Products, variations, categories, tags, attributes, reviews | 14 paths |

### CoCart Plus

An add-on plugin that extends CoCart with support for coupons, fees, shipping methods, payment methods, granular totals breakdowns, and more.

#### Plus — API v1

Reflects CoCart Plus **v1.6.0**.

| File | Description | Endpoints |
|------|-------------|-----------|
| [Collection](plus/v1/openapi-cocart-plus-v1-collection.yaml) | All Plus v1 endpoints | 22 paths |

Covers: coupons, fees, shipping methods, payment methods, weight, removed items, quantities, cross-sells, fee/shipping calculations, and detailed totals (discount, fee, shipping, subtotal, tax, total).

### CoCart JWT Authentication

A companion plugin that adds JWT (JSON Web Token) authentication to CoCart. Tokens are issued during login and managed via dedicated endpoints.

Reflects CoCart JWT Authentication **v3.0.2**.

| File | Description | Endpoints |
|------|-------------|-----------|
| [JWT Auth](jwt-authentication/openapi-cocart-jwt-auth.yaml) | Token refresh and validation | 2 paths |

Covers: `POST /refresh-token` and `POST /validate-token` with rate limiting, Bearer token security, and PAT (Personal Access Token) session management.

---

## Importing into an API Client

These specs are designed to give you a head start when working with the CoCart API in your preferred client. Here's what to expect.

### What you get

- Pre-configured requests for every endpoint, organized into folders by tag
- Query, path, and header parameters already set up
- JSON request body templates based on the schema definitions
- Authentication schemes (Basic Auth, Bearer Token) ready to configure with your credentials
- Server URL with variables for protocol and domain — update the `host` variable to point to your store

### Placeholder values

Some parameters may display type placeholders (e.g. `<string>`, `<integer>`) instead of real values. This is normal — the spec defines the parameter type and description, but not every field includes a sample value. Replace these with real values for your store before sending requests.

### After importing

1. **Set your store URL** — Update the `host` server variable from `example-store.com` to your actual store domain.
2. **Configure authentication** — Add your credentials under the auth settings for endpoints that require it.
3. **Replace placeholders** — Fill in parameter values like product IDs, item keys, and session keys with real data from your store.

> [!TIP]
> For detailed parameter descriptions, expected values, and full response examples, refer to the [CoCart API Reference](https://docs.cocartapi.com).

---

## Specification Format

All specifications follow **OpenAPI 3.0.3** and are written in **YAML**. They can be used with any OpenAPI-compatible tool, including:

- [Yaak](https://yaak.app) (import via Settings > Import)
- [Swagger UI](https://swagger.io/tools/swagger-ui/) / [Swagger Editor](https://editor.swagger.io/)
- [Redoc](https://redocly.com/redoc)
- [Postman](https://www.postman.com/) (import directly)
- Code generators ([OpenAPI Generator](https://openapi-generator.tech/), [Kiota](https://learn.microsoft.com/en-us/openapi/kiota/), etc.)

## License

These specifications are licensed under the [GNU General Public License v3.0](http://www.gnu.org/licenses/gpl-3.0.html).

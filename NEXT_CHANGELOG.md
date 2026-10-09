# Next Changelog for CoCart OpenAPI <!-- omit in toc -->

> [!WARNING]
> This changelog is **NOT** final. It lists the spec changes waiting to be committed, for CoCart Starter 5.0, CoCart Plus 2.0 and CoCart 4.9.8.

## CoCart Starter (API v2)

### Corrected to match the API

The response schemas were checked against live responses from CoCart Starter 5 and corrected where they differed: 7 of 17 recorded responses matched the spec before, and all 17 match now.

* Component schemas for carts, items, products, variations, categories, the store and sessions now describe the fields CoCart sends, with the right types and required lists. Customer address fields are prefixed (`billing_first_name`), `shipping` is an object, and image `src` is a map of sizes.
* `attributes` and `default_attributes` are objects keyed by attribute name, not lists. A variation's selected `option` and a product attribute's `options` are `{ slug: name }`. New components: `ProductAttributes`, `ProductAttributeDetail`, `ProductVariationSummary`, `ProductPriceRange`, `PurchaseQuantity`, `ProductCategoryDetail`.
* `GET /sessions` returns session summaries: new `SessionSummary` component.
* Empty maps are `{}`: the `[]` alternative was removed from map fields (`notices`, `extensions`, `fees`, `cart_item_data`, `price_range`, `attributes`…).
* Money: `GET /cart/totals` returns minor-unit strings (new `CartTotalsBreakdown` component), formatted with `formatted` or `html`. Shipping rate `cost` and `taxes` follow `formatted`. Cart `fees` are keyed by fee ID, each `{ name, fee }`.
* Examples were corrected to the real shapes, including product `variations` and the attributes of `/products/{id}/variations`.

### Newly documented

* Cart and session response headers: new header components (`CartKeyHeader`, `CartHashHeader`, `CartExpiresHeader`, `CartExpiringHeader`, `CartExpirationHeader`, `SessionCacheControlHeader`, `SessionVaryHeader`) on every `2xx` response of the `/cart*` routes, and `Cache-Control` and `Vary` on `/login` and `/logout`.
* Every cart route returns `404 cocart_invalid_cart` for a cart key with no cart session (except `POST /cart`, which creates a cart).
* Adding or updating an item with a quantity above the most allowed reduces it and returns a `notice` saying so.
* An unknown item key on `GET`, `POST` and `DELETE` `/cart/item/{item_key}` returns `404 cocart_item_not_in_cart` with the current cart in `data.cart` (new `ItemNotInCartError` component). The examples named the code `cocart_item_not_found`, which isn't sent.

## CoCart Plus (API v2)

* New path `POST /order-received/{order_id}/confirm` to finish a payment after an off-site step, with the `ConfirmOrderPaymentResponse` component.
* A failed payment's `payment_result.error` (new `PaymentError` component) carries a stable `code` and a customer-facing `message`.
* Checkout `status` is the order's status after payment, and amounts in checkout and order-received responses are minor-unit strings (`formatted` for display).
* New path `POST /batch` (in the "others" spec and the collection), including the single-cart response for a batch of cart routes and failed requests as `error` notices.
* `RateLimit-*` headers are listed as exposed through CORS.
* Extension data: new `CartExtensions`, `CartItemExtensions` and `ProductExtensions` components describe the data each supported plugin adds under `extensions`, generated from the plugins' own schemas. Each description names the plugin. `CartV2.items` is corrected to the list Starter v2 sends.
* A "Choices sent on CoCart Starter routes" section in the cart, products and collection specs says how a client sends a subscription plan (`convert_to_sub`), switches a cart item's plan (`POST /cart/update`, `namespace` `update-item-schema`), and sends a gift recipient (`recipient_email`) or a warranty (`item_data[warranty]`).
* A product's subscription plan options have no `selected` (only a cart item's do), and the recurring totals' `subtotal` and `total` follow `formatted`.

## CoCart (community, API v1 and v2)

* `attributes`, `default_attributes` and, in API v1, a product's `variations` are objects keyed by attribute name or variation ID, not lists. In API v2, a variation's selected `option` and a product attribute's `options` are `{ slug: name }`. Examples are corrected to match.
* CoCart 4.x sends an empty map as `[]`, so the new keyed schemas also allow `[]` (new `EmptyArray` component).
* A coupon's `saving` is described as negative and `saving_html` as the unsigned amount for display, with corrected examples.

## README

* The checkout spec's description now includes confirming payments after an off-site step (8 paths).

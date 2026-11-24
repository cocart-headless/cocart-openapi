# Next Changelog for CoCart OpenAPI <!-- omit in toc -->

> [!WARNING]
> This changelog is **NOT** final. It lists what is coming next for the CoCart Starter 5.0, CoCart Plus 2.0 and CoCart 4.9.8 specs.

## CoCart Starter (API v2)

* Responses now match what the API actually returns, for carts, items, products, variations, categories, the store and sessions.
* Product attributes and variations are described as keyed objects instead of lists.
* Cart totals, fees and shipping rates are described in the format they are sent.
* Examples are corrected to match real responses.
* Cart and session response headers are now documented.
* Documented the errors for an unknown cart or cart item, and the notice when a requested quantity is reduced to the maximum allowed.

## CoCart Plus (API v2)

* New specs for CoCart Plus 2.0, documenting every route, argument, response and example.
* Orders, subscriptions, customers, checkout and carts each have one consistent response wherever they are returned.
* Orders and subscriptions give `allowed_actions`, a list of what the customer may do now (`pay` and `cancel` for an order; `suspend`, `reactivate`, `cancel`, `resubscribe`, `change_payment_method` and `auto_renew` for a subscription).
* Orders: each item gives `details`, a list of `{label, value}` to print under it. `downloads` and `parent_order` sit on the order itself, and shipping lines give `title`, `total` and `tax`.
* Order and subscription summaries, and the orders listed in a subscription's `related.orders`, give a flat `total`. The customer gives `recent_orders`, a list of their latest orders. Payment methods and both downloads routes return the list itself.
* Payments: placing an order or paying for one documents every outcome, including 3D Secure, redirects, pending and failed payments.
* Routes include:
  * Confirming a payment after an off-site step.
  * Checking how a checkout ended if the response was lost.
  * Changing a subscription's payment method.
  * Downloads for an order.
  * Batch requests.
* Every route lists the errors it can return, with examples.
* Checkout config includes address search availability, terms and privacy links, and the order received URL.
* Checkout items include the product thumbnail.
* Data added by supported extensions (such as subscriptions, gifting and warranties) is described.
* A guide on sending subscription plans, gift recipients and warranties through CoCart Starter routes.

## CoCart (community, API v1 and v2)

* Product attributes and variations are described as keyed objects instead of lists, with corrected examples.
* Coupon savings are described correctly, with corrected examples.

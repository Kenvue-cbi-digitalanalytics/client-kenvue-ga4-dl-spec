# View Promotion

Fire whenever a user views/sees a promotion located in a component that forwards the user to a promotional page or an item/product. Component types include cards, carousels, search, promotions, home screen hero images, and similar components. A promotion is usually a temporary presentation of information that is different than clicking an item in a dynamic list which would normally send a "[Select Items](../../events/ecommerce/select_item.md)".

The most common use case of the "view_promotion" event user views/sees the hero image that is displayed on the home page of a brand site as this is most commonly a promotion space that will drive a user to a product or product list.

Pairs with "[Select Promotion](../../events/ecommerce/select_promotion.md)".

## HTML Data Attributes

```html
<a href="<link_url>"
  data-layer-event="view_promotion"
  data-layer-identifier="<identifier>"
  data-layer-name="<name>"
  data-layer-facets="<facets>"
  data-layer-list_type="<list_type>"
  data-layer-search_term="<search_term>"
  data-layer-search_type="<search_type>"
  data-layer-index="<index>"
>
```

## Javascript Code

```js
// When:
// User sees a promotion link

// Code:
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null, ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "view_promotion",
  event_data: {
    identifier: "<identifier>", // REQUIRED | string | ex. uniquely_created_id, skin360_pwa_ntg_atc
    name: '<name>' // REQUIRED | string | ex. pdp_add_to_cart, skin360_pwa_ntg add_to_cart
},
  ecommerce: {
    creative_name: "<creative_name>", // REQUIRED | string | ex. summer_banner2	
    creative_slot: "<creative_slot>", // REQUIRED | string | ex. featured_hero_splash_1	
    promotion_id: "<promotion_id>", // REQUIRED | string | ex. P_12345
    promotion_name: "<promotion_name>", // REQUIRED | string | summer_sale_2023
    items: "<items>" // REQUIRED | array | ex. [{item_id: "test"}]
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Maximum Length|
| --- | --- | --- | --- | --- | --- |
|**identifier**|`string`|required|The wtb-event machine-readable name. This should be a unique value specific to this piece of content, if one exists. If one does not exist, this can also be populated with the same value as the <name>.|`contact`, `lead_generation`|`100`|
|**name**|`string`|required|The wtb-event human-readable name. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify the event with. It should be lowercase snake_case.|`contact`, `lead_generation`|`100`|
|creative_name|string|required|The name of the promotional creative. Ignored if set at the item-level.|`summer_banner2`|`100`|
|creative_slot|string|required|The name of the promotional creative slot associated with the event. Ignored if set at the item-level.|`featured_hero_splash_1`|`100`|
|promotion_id|string|required|The ID of the promotion associated with the event. Ignored if set at the item-level.|`P_12345`|`100`|
|promotion_name|string|required|The name of the promotion associated with the event. Ignored if set at the item-level.|`summer_sale_2023`|`100`|
|items|array of [items](../../schemas/item.md)|required|Populate with item objects that represent the product viewed.|`[{item_id: "test"}]`|

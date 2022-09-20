# api.spacefill.fr changelog

## 2022-09-20

Updated endpoints:

- `GET /v1/logistic_management/orders/` return `pallet_sscc` field in `order_items` list
- `GET /v1/logistic_management/orders/{order_id}/` return `pallet_sscc` field in `order_items` list


## 2022-09-16

Updated endpoints:

- `POST /v1/logistic_management/orders/{order_id}/warehouse_acknowledges_receipt_of_order_action` support new field: `order_items[ ].pallet_sscc`
- `POST https://api.spacefill.fr/v1/logistic_management/orders/exit/` support new field: `order_items[ ].pallet_sscc`


## 2022-09-14

Updated endpoints:

- `order_items` `batch` is directly created if the couple master_item and `batch_name` is not found, this behaviour is available for this endpoints:
  - `POST /v1/logistic_management/orders/entry/`
  - `POST /v1/logistic_management/orders/exit/`
  - `POST /v1/logistic_management/orders/{order_id}/warehouse_acknowledges_receipt_of_order_action`
  - `POST /v1/logistic_management/orders/{order_id}/shipper_updates_order_action`
  - `POST /v1/logistic_management/orders/warehouse_creates_order_action`
  - `POST /v1/logistic_management/inventory_adjustments/`
- `POST /v1/logistic_management/orders/{order_id}/warehouse_acknowledges_receipt_of_order_action`:
  - `master_item` can be selected by `order_items[].item_reference`


## 2022-09-13

Fix bug:

- `POST /v1/logistic_management/orders/{order_id}/warehouse_acknowledges_receipt_of_order_action` return an 404 error when `order_id` not exists

Updated endpoints:

- `order_items` batch can be selected by `batch_name` in this endpoints:
    - `POST /v1/logistic_management/orders/entry/`
    - `POST /v1/logistic_management/orders/exit/`
    - `POST /v1/logistic_management/orders/{order_id}/warehouse_acknowledges_receipt_of_order_action`
    - `POST /v1/logistic_management/orders/{order_id}/shipper_updates_order_action`
    - `POST /v1/logistic_management/orders/warehouse_creates_order_action`
    - `POST /v1/logistic_management/inventory_adjustments/`


## 2022-09-12

Updated endpoints:

- `POST /v1/logistic_management/orders/{order_id}/warehouse_acknowledges_receipt_of_order_action`
  - `order_items[].id` is now optional when `order_items[].master_item_id` and `item_packaging_type": "PALLET"` are filled


## 2022-09-08

Updated endpoints:

- `POST /v1/logistic_management/orders/{order_id}/warehouse_acknowledges_receipt_of_order_action`:
  - `order_items[].expected_quantity` input field is removed (no breaking change, the `expected_quantity` field is still accepted but it is ignored)
  - `order_items[].actual_quantity` input field is mandatory


## 2022-06-30

Updated endpoints:

- `GET /v1/logistic_management/orders/`:
  - the `edi_erp_id`, `edi_wms_id`, `edi_tms_id` fields are returned in `orders_items` list
- `GET /v1/logistic_management/orders/{order_id}/`:
  - the `edi_erp_id`, `edi_wms_id`, `edi_tms_id` fields are returned in `orders_items` list
- `POST /v1/logistic_management/orders/entry/`:
  - the `edi_erp_id`, `edi_wms_id`, `edi_tms_id` fields are returned in `orders_items` list
- `POST /v1/logistic_management/orders/exit/`:
  - the `edi_erp_id`, `edi_wms_id`, `edi_tms_id` fields are returned in `orders_items` list
- `POST /v1/logistic_management/orders/warehouse_creates_order_action`:
  - the `edi_erp_id`, `edi_wms_id`, `edi_tms_id` fields are returned in `orders_items` list
- `POST /v1/logistic_management/orders/warehouse_acknowledges_receipt_of_order_action`:
  - the `edi_erp_id`, `edi_wms_id`, `edi_tms_id` fields are returned in `orders_items` list
- `POST /v1/logistic_management/inventory_adjustments/`:
  - the `edi_erp_id`, `edi_wms_id`, `edi_tms_id` fields are returned in `orders_items` list
- `POST /v1/logistic_management/orders/{order_id}/shipper_updates_order_action`:
  - the `edi_erp_id`, `edi_wms_id`, `edi_tms_id` fields are returned in `orders_items` list


## 2022-06-14

New endpoints:

- `POST /v1/logistic_management/orders/{order_id}/warehouse_finishes_preparation_action`, more information see [Swagger documentation](https://api.spacefill.fr/docs#%2Flogistic-management%2Fpost_v1_logistic_management_warehouse_finishes_preparation_action_v1_logistic_management_orders__order_id__warehouse_finishes_preparation_action_post=)

Updated endpoints:

- `POST /v1/logistic_management/orders/entry/`:
  - accept `item_reference` field in `order_items` array in input request body
  - accept `edi_erp_id` field in `order_items` array in input request  body
  - accept `edi_wms_id` field in `order_items` array in input request  body
  - accept `edi_tms_id` field in `order_items` array in input request  body
- `POST /v1/logistic_management/orders/exit/`:
  - accept `item_reference` field in `order_items` array in input request body
  - accept `edi_erp_id` field in `order_items` array in input request  body
  - accept `edi_wms_id` field in `order_items` array in input request  body
  - accept `edi_tms_id` field in `order_items` array in input request  body
- `POST /v1/logistic_management/orders/{order_id}/warehouse_acknowledges_receipt_of_order_action`:
  - `additional_order_items` field removed, now you can deliver all order items in `order_items`
- `GET /v1/logistic_management/master_items/{master_item_id}/`
  - `edi_erp_warehouse_id`, `edi_wms_warehouse_id`, `edi_tms_warehouse_id` fields added to `stock_by_warehouse` and `forecasted_quantity_by_warehouse` dictionaries
- `POST /v1/logistic_management/master_items/`:
  - a shipper account can be specify by `shipper_account_id`, `edi_erp_shipper_id`, `edi_wms_shipper_id`, or `edi_tms_shipper_id` input field
- `GET /v1/logistic_management/orders/`:
  - `edi_erp_shipper_id`, `edi_wms_shipper_id`, `edi_tms_shipper_id`, `edi_erp_warehouse_id`, `edi_wms_warehouse_id`, `edi_tms_warehouse_id`
    fields added to `items` object list
- `GET /v1/logistic_management/orders/{order_id}`:
  - `edi_erp_shipper_id`, `edi_wms_shipper_id`, `edi_tms_shipper_id`, `edi_erp_warehouse_id`, `edi_wms_warehouse_id`, `edi_tms_warehouse_id`
    added to response
- `POST /v1/logistic_management/orders/entry/`:
  - `edi_erp_shipper_id`, `edi_wms_shipper_id`, `edi_tms_shipper_id`, `edi_erp_warehouse_id`, `edi_wms_warehouse_id`, `edi_tms_warehouse_id`
    added to response
  - a warehouse can be specify by `warehouse_id`, `edi_erp_warehouse_id`, `edi_wms_warehouse_id`, or
    `edi_tms_warehouse_id` input field
- `POST /v1/logistic_management/orders/exit/`:
  - `edi_erp_shipper_id`, `edi_wms_shipper_id`, `edi_tms_shipper_id`, `edi_erp_warehouse_id`, `edi_wms_warehouse_id`, `edi_tms_warehouse_id`
    added to response
  - a warehouse can be specify by `warehouse_id`, `edi_erp_warehouse_id`, `edi_wms_warehouse_id`, or
    `edi_tms_warehouse_id` input field
- `POST /v1/logistic_management/orders/warehouse_creates_order_action`:
  - `edi_erp_shipper_id`, `edi_wms_shipper_id`, `edi_tms_shipper_id`, `edi_erp_warehouse_id`, `edi_wms_warehouse_id`, `edi_tms_warehouse_id`
    added to response
  - a warehouse can be specify by `warehouse_id`, `edi_erp_warehouse_id`, `edi_wms_warehouse_id`, or `edi_tms_warehouse_id` input field
  - a shipper account can be specify by `shipper_account_id`, `edi_erp_shipper_id`, `edi_wms_shipper_id`, or `edi_tms_shipper_id` input field
- `POST /v1/logistic_management/orders/{order_id}/warehouse_acknowledges_receipt_of_order_action`
  - `edi_erp_shipper_id`, `edi_wms_shipper_id`, `edi_tms_shipper_id`, `edi_erp_warehouse_id`, `edi_wms_warehouse_id`, `edi_tms_warehouse_id`
    added to response
- `POST /v1/logistic_management/orders/{order_id}/shipper_cancels_order_action`:
  - `edi_erp_shipper_id`, `edi_wms_shipper_id`, `edi_tms_shipper_id`, `edi_erp_warehouse_id`, `edi_wms_warehouse_id`, `edi_tms_warehouse_id`
    added to response
- `POST /v1/logistic_management/orders/{order_id}/shipper_updates_order_action`:
  - `edi_erp_shipper_id`, `edi_wms_shipper_id`, `edi_tms_shipper_id`, `edi_erp_warehouse_id`, `edi_wms_warehouse_id`, `edi_tms_warehouse_id`
    added to response
- `POST /v1/logistic_management/orders/{order_id}/warehouse_emits_order_receipt_error_action`:
  - `edi_erp_shipper_id`, `edi_wms_shipper_id`, `edi_tms_shipper_id`, `edi_erp_warehouse_id`, `edi_wms_warehouse_id`, `edi_tms_warehouse_id`
    added to response
- `POST /v1/logistic_management/inventory_adjustments/`:
  - `edi_erp_warehouse_id`, `edi_wms_warehouse_id`, `edi_tms_warehouse_id` added to response
  - a warehouse can be specify by `warehouse_id`, `edi_erp_warehouse_id`, `edi_wms_warehouse_id`, or `edi_tms_warehouse_id` input field
  - a shipper account can be specify by `shipper_account_id`, `edi_erp_shipper_id`, `edi_wms_shipper_id`, or `edi_tms_shipper_id` input field

## 2022-06-07

New endpoints:

- `POST /v1/logistic_management/orders/{order_id}/warehouse_starts_unloading_action`, more information see [Swagger documentation](https://api.spacefill.fr/docs#%2Flogistic-management%2Fpost_v1_logistic_management_warehouse_starts_unloading_action_v1_logistic_management_orders__order_id__warehouse_starts_unloading_action_post=)


## 2022-06-03

Updated endpoints:

- `POST /v1/logistic_management/master_items` can now be used by a `warehouse-user`


## 2022-05-31

Updated endpoints:

- `GET /v1/logistic_management/orders/`:
  - accept `tms_status` query filter
  - return `tms_status` field in response in `items`
- `GET /v1/logistic_management/orders/{order_id}/` return `tms_status` field in response
- `POST /v1/logistic_management/orders/exit/`:
  - accept `tms_status` in request input
  - return `tms_status` field in response
- `PATCH /v1/logistic_management/orders/{order_id}/` accept `tms_status` in request input


## 2022-05-24

New endpoint:

- `POST /v1/logistic_management/master_items`


## 2022-05-18

New endpoints:

- `POST /v1/logistic_management/inventory_adjustments/`, more information see [Swagger documentation](https://api.spacefill.fr/docs#/logistic-management/post_v1_logistic_management_inventory_adjustement_v1_logistic_management_inventory_adjustments__post)

Updated endpoints:

- `GET /v1/logistic_management/master_items/{master_item_id/}`: new `include_forecasted_quantity_at` url query parameter (more information see [Swagger documentation](https://api.spacefill.fr/docs#/logistic-management/get_v1_logistic_management_master_item_v1_logistic_management_master_items__master_item_id___get))

**Breaking changes:**

- `GET /v1/logistic_management/orders/`:
  - `customer_id` filter is renamed `shipper_account_id`
  - `customer_id` field is renamed `shipper_account_id` in query response
- `GET /v1/logistic_management/orders/{order_id}/`:
  - `customer_id` filter is renamed `shipper_account_id`
  - `customer_id` field is renamed `shipper_account_id` in query response
- `POST /v1/logistic_management/orders/entry/`:
  - `customer_id` field is renamed `shipper_account_id` in query response
- `POST /v1/logistic_management/orders/exit/`:
  - `customer_id` field is renamed `shipper_account_id` in query response
- `PATCH /v1/logistic_management/orders/{order_id}/`:
  - `customer_id` field is renamed `shipper_account_id` in query response
- `POST /v1/logistic_management/orders/{order_id}/shipper_cancels_order_action`:
  - `customer_id` field is renamed `shipper_account_id` in query response
- `POST /v1/logistic_management/orders/{order_id}/warehouse_acknowledges_receipt_of_order_action`:
  - `customer_id` field is renamed `shipper_account_id` in query response
- `POST /v1/logistic_management/orders/{order_id}/warehouse_adjust_stock_after_order_is_completed_action`:
  - `customer_id` field is renamed `shipper_account_id` in query response
- `POST /v1/logistic_management/orders/{order_id}/shipper_updates_order_action`:
  - `customer_id` field is renamed `shipper_account_id` in query response

## 2022-05-17

Updated endpoints:

- `GET /v1/logistic_management/master_items/`:
  - accept these new url query filters:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
  - return these new fields in response:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
- `POST /v1/logistic_management/master_items/`:
  - accept these new fields in request input:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
  - return these new fields in response:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
- `GET /v1/logistic_management/master_items/{master_item_id}/`: return these new fields in response:
  - `edi_erp_id`
  - `edi_wms_id`
  - `edi_tms_id`
- `PUT /v1/logistic_management/master_items/{master_item_id}/`:
  - accept these new fields in request input:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
  - return these new fields in response:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
- `PATCH /v1/logistic_management/master_items/{master_item_id}/`:
  - accept these new fields in request input:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
  - return these new fields in response:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
- `GET /v1/logistic_management/orders/`:
  - accept these new url query filters:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
  - return these new fields in response:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
- `GET /v1/logistic_management/orders/{order_id}/`: return these new fields in response:
  - `edi_erp_id`
  - `edi_wms_id`
  - `edi_tms_id`
- `POST /v1/logistic_management/orders/entry/`:
  - accept these new fields in request input:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
  - return these new fields in response:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
- `POST /v1/logistic_management/orders/exit/`:
  - accept these new fields in request input:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
  - return these new fields in response:
    - `edi_erp_id`
    - `edi_wms_id`
    - `edi_tms_id`
- `PATCH /v1/logistic_management/orders/{order_id}/`: return these new fields in response:
  - `edi_erp_id`
  - `edi_wms_id`
  - `edi_tms_id`


## 2022-05-10

- Endpoint that is now implemented:
  - `POST /v1/logistic_management/orders/{order_id}/shipper_updates_order_action`, more info see [Swagger documentation](https://api.spacefill.fr/docs#/logistic-management/post_v1_logistic_management_shipper_updates_order_action_v1_logistic_management_orders__order_id__shipper_updates_order_action_post)

- New endpoint not implemented:
  - `POST /v1/logistic_management/inventory_adjustments/`, more info see [Swagger documentation](https://api.spacefill.fr/docs#/logistic-management%20(not%20implemented)/post_v1_logistic_management_inventory_adjustement_v1_logistic_management_inventory_adjustments__post)


## 2022-05-03

- `master_items.transfered_to_erp_at`, `master_items.transfered_to_wms_at` and `master_items.transfered_to_tms_at` fields
   are automatically reset (set to `null`) on each API or Web interface `master_items` update events
- `orders.transfered_to_erp_at`, `orders.transfered_to_wms_at` and `orders.transfered_to_tms_at` fields
   are automatically reset (set to `null`) on each API or Web interface `orders` update events

## 2022-04-27

New endpoints:

- `PATCH /v1/logistic_management/master_items/{master_item_id}/`
- `PATCH /v1/logistic_management/orders/{order_id}/`

Updated endpoints:

- `GET /v1/logistic_management/master_items/`]
  - accept this new url query filters:
    - `is_transfered_to_erp`
    - `is_transfered_to_wms`
    - `is_transfered_to_tms`
  - return this news fields in response:
    - `transfered_to_erp_at`
    - `transfered_to_wms_at`
    - `transfered_to_tms_at`
- `POST /v1/logistic_management/master_items/`:
  - accept this new fields in request input:
    - `transfered_to_erp_at`
    - `transfered_to_wms_at`
    - `transfered_to_tms_at`
  - return this news fields in response:
    - `transfered_to_erp_at`
    - `transfered_to_wms_at`
    - `transfered_to_tms_at`
- `GET /v1/logistic_management/master_items/{master_item_id}/`: return this news fields in response:
  - `transfered_to_erp_at`
  - `transfered_to_wms_at`
  - `transfered_to_tms_at`
- `PUT /v1/logistic_management/master_items/{master_item_id}/`:
  - accept this new fields in request input:
    - `transfered_to_erp_at`
    - `transfered_to_wms_at`
    - `transfered_to_tms_at`
  - return this news fields in response:
    - `transfered_to_erp_at`
    - `transfered_to_wms_at`
    - `transfered_to_tms_at`
- `GET /v1/logistic_management/orders/`:
  - accept this new url query filters:
    - `is_transfered_to_erp`
    - `is_transfered_to_wms`
    - `is_transfered_to_tms`
  - return this news fields in response:
    - `transfered_to_erp_at`
    - `transfered_to_wms_at`
    - `transfered_to_tms_at`
- `GET /v1/logistic_management/orders/{order_id}/`: return this news fields in response:
  - `transfered_to_erp_at`
  - `transfered_to_wms_at`
  - `transfered_to_tms_at`
- `POST /v1/logistic_management/orders/entry/`:
  - accept this new fields in request input:
    - `transfered_to_erp_at`
    - `transfered_to_wms_at`
    - `transfered_to_tms_at`
  - return this news fields in response:
    - `transfered_to_erp_at`
    - `transfered_to_wms_at`
    - `transfered_to_tms_at`
- `POST /v1/logistic_management/orders/exit/`:
  - accept this new fields in request input:
    - `transfered_to_erp_at`
    - `transfered_to_wms_at`
    - `transfered_to_tms_at`
  - return this news fields in response:
    - `transfered_to_erp_at`
    - `transfered_to_wms_at`
    - `transfered_to_tms_at`
- `POST /v1/logistic_management/orders/{order_id}/warehouse_acknowledges_receipt_of_order_action`: return this news fields in response:
  - `transfered_to_erp_at`
  - `transfered_to_wms_at`
  - `transfered_to_tms_at`
- `POST /v1/logistic_management/orders/{order_id}/shipper_cancels_order_action`: return this news fields in response:
  - `transfered_to_erp_at`
  - `transfered_to_wms_at`
  - `transfered_to_tms_at`
- `POST /v1/logistic_management/orders/{order_id}/warehouse_emits_order_receipt_error_action`: return this news fields in response:
  - `transfered_to_erp_at`
  - `transfered_to_wms_at`
  - `transfered_to_tms_at`


## 2022-04-26

Updated endpoints:

- `GET /v1/logistic_management/master_items/`
  - accept this new url query filter: `archived`
  - return this new field in response: `archived_at`
- `GET /v1/logistic_management/master_items/{master_item_id}/`: return this new field in response: `archived_at`

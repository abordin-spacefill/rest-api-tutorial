# Master Items CRUD

See complete orders API endpoints on https://api.sandbox.spacefill.fr/docs

* [Create](#create)
* [Update](#update)
* [Get](#get)
* [List](#list)

In the following examples, each request uses [`jq`](https://stedolan.github.io/jq/) to parse and render the JSON, don't forget to remove it if you do some copy/paste.

## Create

```sh
$ curl -sLX 'POST' \
  'https://api.sandbox.spacefill.fr/v1/logistic_management/master_items/' \
  -H 'accept: application/json' \
  -H 'Authorization: Bearer secret' \
  -H 'Content-Type: application/json' \
  -d '{
  "item_reference": "POTATOES2KG",
  "designation": "Potatoes 2Kg",
  "each_quantity_by_pallet": 50,
  "edi_erp_id": null,
  "edi_wms_id": "123456",
  "edi_tms_id": null
}' | jq
{
  "id": "60109212-5336-4fd8-9512-d3f55383e44c",
  "shipper_account_id": "1de9c987-08ab-32fe-e218-89c124cd0001",
  "item_reference": "POTATOES2KG",
  "designation": "Potatoes 2Kg",
  "cardboard_box_quantity_by_pallet": null,
  "each_barcode_type": null,
  "each_barcode": null,
  "cardboard_box_barcode_type": null,
  "cardboard_box_barcode": null,
  "pallet_barcode_type": null,
  "pallet_barcode": null,
  "each_quantity_by_cardboard_box": null,
  "each_quantity_by_pallet": 50,
  "each_is_stackable": null,
  "cardboard_box_is_stackable": null,
  "pallet_is_stackable": null,
  "each_width_in_cm": null,
  "each_length_in_cm": null,
  "each_height_in_cm": null,
  "each_volume_in_cm3": null,
  "cardboard_box_width_in_cm": null,
  "cardboard_box_length_in_cm": null,
  "cardboard_box_height_in_cm": null,
  "cardboard_box_volume_in_cm3": null,
  "pallet_width_in_cm": null,
  "pallet_length_in_cm": null,
  "pallet_height_in_cm": null,
  "pallet_gross_weight_in_kg": null,
  "pallet_net_weight_in_kg": null,
  "cardboard_box_gross_weight_in_kg": null,
  "cardboard_box_net_weight_in_kg": null,
  "each_gross_weight_in_kg": null,
  "each_net_weight_in_kg": null,
  "edi_erp_id": null,
  "edi_wms_id": "123456",
  "edi_tms_id": null,
  "transfered_to_erp_at": null,
  "transfered_to_wms_at": null,
  "transfered_to_tms_at": null,
  "created_at": "2022-08-26T09:57:54.069021+00:00",
  "created_by": "4b03020e-007b-4430-86fd-dc409f6a0001",
  "updated_at": "2022-08-26T09:57:54.069021+00:00",
  "updated_by": "4b03020e-007b-4430-86fd-dc409f6a0001",
  "archived_at": null,
  "metadata": null,
  "global_stock": null,
  "stock_by_warehouse": null,
  "global_forecasted_quantity": null,
  "forecasted_quantity_by_warehouse": null
}
```

## Update

Update a master item by Spacefill id.

```sh
$ curl -sLX 'PUT' \
  'https://api.sandbox.spacefill.fr/v1/logistic_management/master_items/60109212-5336-4fd8-9512-d3f55383e44c/' \
  -H 'accept: application/json' \
  -H 'Authorization: Bearer secret' \
  -H 'Content-Type: application/json' \
  -d '{
  "edi_erp_id": "123456",
  "edi_tms_id": "123456"
}' | jq
{
  "id": "60109212-5336-4fd8-9512-d3f55383e44c",
  "shipper_account_id": "1de9c987-08ab-32fe-e218-89c124cd0001",
  "item_reference": "POTATOES2KG",
  "designation": "Potatoes 2Kg",
  "cardboard_box_quantity_by_pallet": null,
  "each_barcode_type": null,
  "each_barcode": null,
  "cardboard_box_barcode_type": null,
  "cardboard_box_barcode": null,
  "pallet_barcode_type": null,
  "pallet_barcode": null,
  "each_quantity_by_cardboard_box": null,
  "each_quantity_by_pallet": 50,
  "each_is_stackable": null,
  "cardboard_box_is_stackable": null,
  "pallet_is_stackable": null,
  "each_width_in_cm": null,
  "each_length_in_cm": null,
  "each_height_in_cm": null,
  "each_volume_in_cm3": null,
  "cardboard_box_width_in_cm": null,
  "cardboard_box_length_in_cm": null,
  "cardboard_box_height_in_cm": null,
  "cardboard_box_volume_in_cm3": null,
  "pallet_width_in_cm": null,
  "pallet_length_in_cm": null,
  "pallet_height_in_cm": null,
  "pallet_gross_weight_in_kg": null,
  "pallet_net_weight_in_kg": null,
  "cardboard_box_gross_weight_in_kg": null,
  "cardboard_box_net_weight_in_kg": null,
  "each_gross_weight_in_kg": null,
  "each_net_weight_in_kg": null,
  "edi_erp_id": "123456",
  "edi_wms_id": "123456",
  "edi_tms_id": "123456",
  "transfered_to_erp_at": null,
  "transfered_to_wms_at": null,
  "transfered_to_tms_at": null,
  "metadata": null
}
```

## Get

Get a master item by Spacefill id.

```sh
$ curl -sLX 'GET' \
  'https://api.sandbox.spacefill.fr/v1/logistic_management/master_items/60109212-5336-4fd8-9512-d3f55383e44c/' \
  -H 'accept: application/json' \
  -H 'Authorization: Bearer secret' \
  -H 'Content-Type: application/json' | jq
{
  "id": "60109212-5336-4fd8-9512-d3f55383e44c",
  "shipper_account_id": "1de9c987-08ab-32fe-e218-89c124cd0001",
  "item_reference": "POTATOES2KG",
  "designation": "Potatoes 2Kg",
  "cardboard_box_quantity_by_pallet": null,
  "each_barcode_type": null,
  "each_barcode": null,
  "cardboard_box_barcode_type": null,
  "cardboard_box_barcode": null,
  "pallet_barcode_type": null,
  "pallet_barcode": null,
  "each_quantity_by_cardboard_box": null,
  "each_quantity_by_pallet": 50,
  "each_is_stackable": null,
  "cardboard_box_is_stackable": null,
  "pallet_is_stackable": null,
  "each_width_in_cm": null,
  "each_length_in_cm": null,
  "each_height_in_cm": null,
  "each_volume_in_cm3": null,
  "cardboard_box_width_in_cm": null,
  "cardboard_box_length_in_cm": null,
  "cardboard_box_height_in_cm": null,
  "cardboard_box_volume_in_cm3": null,
  "pallet_width_in_cm": null,
  "pallet_length_in_cm": null,
  "pallet_height_in_cm": null,
  "pallet_gross_weight_in_kg": null,
  "pallet_net_weight_in_kg": null,
  "cardboard_box_gross_weight_in_kg": null,
  "cardboard_box_net_weight_in_kg": null,
  "each_gross_weight_in_kg": null,
  "each_net_weight_in_kg": null,
  "edi_erp_id": "123456",
  "edi_wms_id": "123456",
  "edi_tms_id": "123456",
  "transfered_to_erp_at": null,
  "transfered_to_wms_at": null,
  "transfered_to_tms_at": null,
  "created_at": "2022-08-26T09:57:54.069021+00:00",
  "created_by": "4b03020e-007b-4430-86fd-dc409f6a0001",
  "updated_at": "2022-08-26T10:00:26.171209+00:00",
  "updated_by": "4b03020e-007b-4430-86fd-dc409f6a0001",
  "archived_at": null,
  "metadata": null,
  "global_stock": {
    "each_actual_quantity": null,
    "cardboard_box_actual_quantity": null,
    "pallet_actual_quantity": null,
    "each_allocated_quantity": null,
    "cardboard_box_allocated_quantity": null,
    "pallet_allocated_quantity": null,
    "each_awaited_quantity": null,
    "cardboard_box_awaited_quantity": null,
    "pallet_awaited_quantity": null
  },
  "stock_by_warehouse": null,
  "global_forecasted_quantity": null,
  "forecasted_quantity_by_warehouse": null
}
```

## List

List master items.

```sh
$ curl -sLX 'GET' \
  'https://api.sandbox.spacefill.fr/v1/logistic_management/master_items/' \
  -H 'accept: application/json' \
  -H 'Authorization: Bearer secret' \
  -H 'Content-Type: application/json' | jq
{
  "total": 1,
  "items": [
    {
      "id": "60109212-5336-4fd8-9512-d3f55383e44c",
      "shipper_account_id": "1de9c987-08ab-32fe-e218-89c124cd0001",
      "item_reference": "POTATOES2KG",
      "designation": "Potatoes 2Kg",
      "cardboard_box_quantity_by_pallet": null,
      "each_barcode_type": null,
      "each_barcode": null,
      "cardboard_box_barcode_type": null,
      "cardboard_box_barcode": null,
      "pallet_barcode_type": null,
      "pallet_barcode": null,
      "each_quantity_by_cardboard_box": null,
      "each_quantity_by_pallet": 50,
      "each_is_stackable": null,
      "cardboard_box_is_stackable": null,
      "pallet_is_stackable": null,
      "each_width_in_cm": null,
      "each_length_in_cm": null,
      "each_height_in_cm": null,
      "each_volume_in_cm3": null,
      "cardboard_box_width_in_cm": null,
      "cardboard_box_length_in_cm": null,
      "cardboard_box_height_in_cm": null,
      "cardboard_box_volume_in_cm3": null,
      "pallet_width_in_cm": null,
      "pallet_length_in_cm": null,
      "pallet_height_in_cm": null,
      "pallet_gross_weight_in_kg": null,
      "pallet_net_weight_in_kg": null,
      "cardboard_box_gross_weight_in_kg": null,
      "cardboard_box_net_weight_in_kg": null,
      "each_gross_weight_in_kg": null,
      "each_net_weight_in_kg": null,
      "edi_erp_id": "123456",
      "edi_wms_id": "123456",
      "edi_tms_id": "123456",
      "transfered_to_erp_at": null,
      "transfered_to_wms_at": null,
      "transfered_to_tms_at": null,
      "created_at": "2022-08-26T09:57:54.069021+00:00",
      "created_by": "4b03020e-007b-4430-86fd-dc409f6a0001",
      "updated_at": "2022-08-26T10:00:26.171209+00:00",
      "updated_by": "4b03020e-007b-4430-86fd-dc409f6a0001",
      "archived_at": null,
      "metadata": null,
      "global_stock": {
        "each_actual_quantity": null,
        "cardboard_box_actual_quantity": null,
        "pallet_actual_quantity": null,
        "each_allocated_quantity": null,
        "cardboard_box_allocated_quantity": null,
        "pallet_allocated_quantity": null,
        "each_awaited_quantity": null,
        "cardboard_box_awaited_quantity": null,
        "pallet_awaited_quantity": null
      },
      "stock_by_warehouse": null,
      "global_forecasted_quantity": null,
      "forecasted_quantity_by_warehouse": null
    }
  ]
}
```

Find a master item by EDI identifier (`edi_erp_id`, `edi_wms_id` or `edi_tms_id`).

```sh
$ curl -sLX 'GET' \
  'https://api.sandbox.spacefill.fr/v1/logistic_management/master_items/?edi_erp_id=123456' \
  -H 'accept: application/json' \
  -H 'Authorization: Bearer secret' \
  -H 'Content-Type: application/json' | jq
{
  "total": 1,
  "items": [
    {
      "id": "60109212-5336-4fd8-9512-d3f55383e44c",
      "shipper_account_id": "1de9c987-08ab-32fe-e218-89c124cd0001",
      "item_reference": "POTATOES2KG",
      "designation": "Potatoes 2Kg",
      "cardboard_box_quantity_by_pallet": null,
      "each_barcode_type": null,
      "each_barcode": null,
      "cardboard_box_barcode_type": null,
      "cardboard_box_barcode": null,
      "pallet_barcode_type": null,
      "pallet_barcode": null,
      "each_quantity_by_cardboard_box": null,
      "each_quantity_by_pallet": 50,
      "each_is_stackable": null,
      "cardboard_box_is_stackable": null,
      "pallet_is_stackable": null,
      "each_width_in_cm": null,
      "each_length_in_cm": null,
      "each_height_in_cm": null,
      "each_volume_in_cm3": null,
      "cardboard_box_width_in_cm": null,
      "cardboard_box_length_in_cm": null,
      "cardboard_box_height_in_cm": null,
      "cardboard_box_volume_in_cm3": null,
      "pallet_width_in_cm": null,
      "pallet_length_in_cm": null,
      "pallet_height_in_cm": null,
      "pallet_gross_weight_in_kg": null,
      "pallet_net_weight_in_kg": null,
      "cardboard_box_gross_weight_in_kg": null,
      "cardboard_box_net_weight_in_kg": null,
      "each_gross_weight_in_kg": null,
      "each_net_weight_in_kg": null,
      "edi_erp_id": "123456",
      "edi_wms_id": "123456",
      "edi_tms_id": "123456",
      "transfered_to_erp_at": null,
      "transfered_to_wms_at": null,
      "transfered_to_tms_at": null,
      "created_at": "2022-08-26T09:57:54.069021+00:00",
      "created_by": "4b03020e-007b-4430-86fd-dc409f6a0001",
      "updated_at": "2022-08-26T10:00:26.171209+00:00",
      "updated_by": "4b03020e-007b-4430-86fd-dc409f6a0001",
      "archived_at": null,
      "metadata": null,
      "global_stock": {
        "each_actual_quantity": null,
        "cardboard_box_actual_quantity": null,
        "pallet_actual_quantity": null,
        "each_allocated_quantity": null,
        "cardboard_box_allocated_quantity": null,
        "pallet_allocated_quantity": null,
        "each_awaited_quantity": null,
        "cardboard_box_awaited_quantity": null,
        "pallet_awaited_quantity": null
      },
      "stock_by_warehouse": null,
      "global_forecasted_quantity": null,
      "forecasted_quantity_by_warehouse": null
    }
  ]
}
```

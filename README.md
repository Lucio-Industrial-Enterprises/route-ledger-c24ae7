# Warehouse tools

Small Python utilities for warehouse order and shipping workflows.

Run the tests with `python3 -m unittest discover -s tests -v`.

## Shipping

`shipping_quote(weight_kg, zone, service="standard")` returns a delivery quote
in dollars.

| Parameter | Values | Notes |
|-----------|--------|-------|
| `weight_kg` | positive float | Parcel weight in kilograms |
| `zone` | `"local"`, `"regional"` | Delivery zone |
| `service` | `"standard"` (default), `"express"` | Express adds a flat $7.00 surcharge |

Raises `ValueError` for non-positive weight, unknown zone, or unknown service.

### CLI

```
python -m warehouse.cli <weight_kg> <zone> [--service {standard,express}]
```

Examples:

```bash
python -m warehouse.cli 2 local                    # $8.00  (standard)
python -m warehouse.cli 2 local --service express  # $15.00 (express)
python -m warehouse.cli 2 regional --service express  # $18.00
```

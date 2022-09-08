<!-- TOP -->
<div class="top">
  <img src="https://datastax-academy.github.io/katapod-shared-assets/images/ds-academy-logo.svg" />
  <span class="scenario-title">Order Management Data Modeling</span>
  <span class="scenario-subtitle">ℹ️ For technical support, please contact us via <a href="mailto:aleksandr.volochnev@datastax.com">email</a> or <a href="https://dtsx.io/aleks">LinkedIn</a>.</span> 
</div>

<!-- NAVIGATION -->
<div id="navigation-top" class="navigation-top">
 <a href='command:katapod.loadPage?[{"step":"step2"}]' 
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 3 of 8</span>
 <a href='command:katapod.loadPage?[{"step":"step4"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Populate tables</div>

✅ Execute the CQL script to insert sample data:
```
SOURCE 'assets/order_management_data.cql'
```

✅ Retrieve all rows from table `orders_by_user`:
```
SELECT * FROM orders_by_user;        
```

✅ Retrieve all rows from table `orders_by_id`:
```
EXPAND ON;

SELECT 
  order_id,
  item_name,
  item_id,
  item_description,
  item_price,
  item_quantity,
  order_status,
  order_timestamp,
  order_subtotal,
  order_shipping,
  order_tax,
  order_total,
  payment_summary,
  payment_details,
  billing_summary,
  billing_details,
  shipping_summary,
  shipping_details,
  delivery_id,
  delivery_details 
FROM orders_by_id;

EXPAND OFF;
```

✅ Retrieve all rows from table `orders_by_user_item`:
```
SELECT * FROM orders_by_user_item;                    
```

✅ Retrieve all rows from table `order_status_history_by_id`:
```
SELECT * FROM order_status_history_by_id; 
```

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step2"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step4"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>

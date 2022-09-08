<!-- TOP -->
<div class="top">
  <img src="https://datastax-academy.github.io/katapod-shared-assets/images/ds-academy-logo.svg" />
  <span class="scenario-title">Order Management Data Modeling</span>
  <span class="scenario-subtitle">ℹ️ For technical support, please contact us via <a href="mailto:aleksandr.volochnev@datastax.com">email</a> or <a href="https://dtsx.io/aleks">LinkedIn</a>.</span> 
</div>

<!-- NAVIGATION -->
<div id="navigation-top" class="navigation-top">
 <a href='command:katapod.loadPage?[{"step":"intro"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 2 of 8</span>
 <a href='command:katapod.loadPage?[{"step":"step3"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Create tables</div>

✅ Create table `orders_by_user`:
```
CREATE TABLE IF NOT EXISTS orders_by_user (
  user_id TEXT,
  order_timestamp TIMESTAMP,
  order_id TEXT,
  order_status TEXT,
  order_total DECIMAL,
  PRIMARY KEY ((user_id),order_timestamp,order_id)
) WITH CLUSTERING ORDER BY (order_timestamp DESC, order_id ASC);
```

✅ Create table `orders_by_id`:
```
CREATE TABLE IF NOT EXISTS orders_by_id (
  order_id TEXT,
  item_name TEXT,
  item_id TEXT,
  item_description TEXT,
  item_price DECIMAL,
  item_quantity INT,
  order_status TEXT STATIC,
  order_timestamp TIMESTAMP STATIC,
  order_subtotal DECIMAL STATIC,
  order_shipping DECIMAL STATIC,
  order_tax DECIMAL STATIC,
  order_total DECIMAL STATIC,
  payment_summary TEXT STATIC,
  payment_details MAP<TEXT,TEXT> STATIC,
  billing_summary TEXT STATIC,
  billing_details MAP<TEXT,TEXT> STATIC,
  shipping_summary TEXT STATIC,
  shipping_details MAP<TEXT,TEXT> STATIC,
  delivery_id TEXT STATIC,
  delivery_details MAP<TEXT,TEXT> STATIC,
  PRIMARY KEY ((order_id),item_name,item_id)
);
```

✅ Create table `orders_by_user_item`:
```
CREATE TABLE IF NOT EXISTS orders_by_user_item (
  user_id TEXT,
  item_id TEXT,
  order_timestamp TIMESTAMP,
  order_id TEXT,
  PRIMARY KEY ((user_id,item_id),order_timestamp,order_id)
) WITH CLUSTERING ORDER BY (order_timestamp DESC, order_id ASC);
```

✅ Create table `order_status_history_by_id`:
```
CREATE TABLE IF NOT EXISTS order_status_history_by_id (
  order_id TEXT,
  status_timestamp TIMESTAMP,
  order_status TEXT,
  PRIMARY KEY ((order_id),status_timestamp)
) WITH CLUSTERING ORDER BY (status_timestamp DESC);
```

✅ Verify that the four tables have been created:
```
DESCRIBE TABLES;
```

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"intro"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step3"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>

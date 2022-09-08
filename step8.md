<!-- TOP -->
<div class="top">
  <img src="https://datastax-academy.github.io/katapod-shared-assets/images/ds-academy-logo.svg" />
  <span class="scenario-title">Order Management Data Modeling</span>
  <span class="scenario-subtitle">ℹ️ For technical support, please contact us via <a href="mailto:aleksandr.volochnev@datastax.com">email</a> or <a href="https://dtsx.io/aleks">LinkedIn</a>.</span> 
</div>

<!-- NAVIGATION -->
<div id="navigation-top" class="navigation-top">
 <a href='command:katapod.loadPage?[{"step":"step7"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 8 of 8</span>
 <a href='command:katapod.loadPage?[{"step":"finish"}]'
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Design update U1</div>

✅ Cancel order `113-3827060-8722206` placed by user `joe` on `2020-11-17` at `22:20:43` by updating its status from `pending` to `canceled`:

<details>
  <summary>Solution</summary>

<p>✅ Update the "source-of-truth" table using a lightweight transaction:</p>

```
UPDATE orders_by_id 
SET order_status = 'canceled' 
WHERE order_id = '113-3827060-8722206'
IF order_status = 'pending';
```

<p>✅ Update the other tables if and only if the previous transaction was successfully applied:</p>

```
UPDATE orders_by_user 
SET order_status = 'canceled' 
WHERE order_id = '113-3827060-8722206'
  AND user_id = 'joe'
  AND order_timestamp = '2020-11-17 22:20:43';

INSERT INTO order_status_history_by_id (order_id, status_timestamp, order_status)
VALUES ('113-3827060-8722206',TOTIMESTAMP(NOW()),'canceled');
```

<p>✅ Optionally, verify the changes:</p>

```
SELECT order_status
FROM orders_by_id
WHERE order_id = '113-3827060-8722206';

SELECT order_status
FROM orders_by_user
WHERE order_id = '113-3827060-8722206'
  AND user_id = 'joe'
  AND order_timestamp = '2020-11-17 22:20:43';

SELECT order_status
FROM order_status_history_by_id
WHERE order_id = '113-3827060-8722206'
LIMIT 1;
```

</details>

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step7"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"finish"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>


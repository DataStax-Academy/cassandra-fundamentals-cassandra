<!-- TOP -->
<div class="top">
  <img src="https://datastax-academy.github.io/katapod-shared-assets/images/ds-academy-logo.svg" />
  <span class="scenario-title">Introduction to Apache Cassandra®</span>
  <span class="scenario-subtitle">ℹ️ For technical support, please contact us via <a href="mailto:aleksandr.volochnev@datastax.com">email</a> or <a href="https://dtsx.io/aleks">LinkedIn</a>.</span> 
</div>

<!-- NAVIGATION -->
<div id="navigation-top" class="navigation-top">
 <a href='command:katapod.loadPage?[{"step":"step6"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 7 of 8</span>
 <a href='command:katapod.loadPage?[{"step":"step8"}]'
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Starting Cassandra</div>

✅ Start Cassandra:
```
cassandra
```

In the terminal, observe the log output while Cassandra is starting. Wait for message `Node localhost/127.0.0.1:7000 state jump to NORMAL` and hit <kbd class="kbd">enter</kbd> or <kbd class="kbd">return</kbd> on the keyboard to proceed.

✅ Check the status of Cassandra:
```
nodetool status
```

The status/state column in the output should report `UN`, which stands for Up/Normal.

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step6"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step8"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>


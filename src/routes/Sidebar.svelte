<!-- Sidebar.svelte -->

<script>
  export let markers = [];
</script>

<style>
  /* Add your panel styles here */
  .panel {
    position: fixed;
    top: 2px;
    left: 5px;
    bottom: 150px;
    width: 400px;
    height: 90%;
    background-color: #f1f1f1;
    overflow-x: hidden;
    padding-top: 20px;
    transition: width 0.3s ease;
    border-style: groove;
    box-shadow: inset 0 3px 6px rgba(0,0,0,0.16), 0 4px 6px rgba(0,0,0,0.45);
    border-radius: 10px;
    font-family: "Monaco", "Courier New", monospace;

  }

  ul {
    list-style-type: square;
    padding: 0;
    margin: 0;
  }

  li {
    list-style-type: square;
    padding: 8px 16px;
    border-bottom: 1px solid #ddd;
  }

  li:last-child {
    border-bottom: none;
  }
  

</style>

<div class="panel">
  <h1>Roam</h1>
<p>A personalized map for friends.</p>
  <h2>Nearby Places</h2>
  <ul>
    {#each markers as marker, index}
    <li>
      <div>
        <strong>{marker.title}</strong>: {marker.description}
      </div>
    </li>
    {/each}
  </ul>
</div>

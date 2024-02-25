<!-- Sidebar.svelte -->

<script>
  export let markers = [];
</script>

<style>
  /* Add your panel styles here */
  .panel {
    width: 440px;
    height: 700px;
    background-color: #f1f1f1;
    top: 0;
    left: 0;
    overflow-x: hidden;
    padding-top: 0px;
    transition: left 0.3s ease;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    padding: 8px 16px;
    border-bottom: 1px solid #ddd;
  }

  li:last-child {
    border-bottom: none;
  }
</style>

<div class="panel">
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

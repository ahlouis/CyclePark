<!-- Sidebar.svelte -->

<script>
    export let onOptionSelect; // Function to handle option selection
  </script>
  
  <style>
    /* Add your panel styles here */
    .panel {
      width: 200px;
      height: 100%;
      background-color: #f1f1f1;
      position: fixed;
      top: 0;
      left: 0;
      overflow-x: hidden;
      padding-top: 20px;
      transition: left 0.3s ease;
    }
  
    /* Button styles */
    .option-button {
      display: block;
      width: 100%;
      padding: 10px;
      margin-bottom: 10px;
      text-align: left;
      cursor: pointer;
      background-color: #ddd;
      border: none;
    }
  </style>
  
  <div class="panel">
    <!-- Buttons for different options -->
    <button class="option-button" on:click={() => onOptionSelect('Places')}>Nearby</button>
    <button class="option-button" on:click={() => onOptionSelect('Bucketlist')}>Bucketlist</button>
  
    <!-- Additional content goes here -->
  </div>
  
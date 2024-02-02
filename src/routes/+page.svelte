<h1>  Roam</h1>
<p>A perosnalized map for friends.</p>
<script>
    import LeafletMap from './LeafletMap.svelte';
    import MapboxComponent from './MapboxMap.svelte'; // Adjust the import path as needed
    import Sidebar from './Sidebar.svelte'

    let isSidebarOpen = false;
    let selectedOption = '';

    function toggleSidebar() {
      isSidebarOpen = !isSidebarOpen;
    }

    function handleOptionSelect(option) {
    selectedOption = option;
    isSidebarOpen = false; // Close the sidebar after selecting an option
  }
  </script>
  
  <style>
    h1 {
      left: 1;
      top: 2;
      left: 10;
      width: 540px;
      font-size: 40px;
      color: skyblue;
      background-color: #f1f1f1;
      font-family: "Lucida Console", "Courier New", monospace;
      font-weight: bold;
    } 
    p {
      
      top: 5;
      right: 0;
      width: 540px;
      font-size: 20px;
      color: skyblue;
      background-color: #f1f1f1;
      font-family: "Lucida Console", "Courier New", monospace;
  
    } 

  </style>

<MapboxComponent />
<button on:click={toggleSidebar}>Places</button>

{#if isSidebarOpen}
  <Sidebar onOptionSelect={handleOptionSelect} />
{/if}

{#if selectedOption === 'Places'}
  <p>Nearby</p>
{/if}

{#if selectedOption === 'Bucketlist'}
  <p>My Bucketlist</p>
{/if}
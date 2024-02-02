<script>
    let isUserLoggedIn = false;
  
    const toggleLogin = () => {
      isUserLoggedIn = !isUserLoggedIn;
    };
  
    const handleLogin = () => {
      // Add your login logic here
      // You can use a state management library or store to handle user authentication
      alert('User logged in!');
      toggleLogin();
    };
  
    const handleLogout = () => {
      // Add your logout logic here
      // You can use a state management library or store to handle user authentication
      alert('User logged out!');
      toggleLogin();
    };
  </script>
  
  <style>
    /* Add your custom styles for the pop-up here */
    .popup {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      padding: 16px;
      background-color: white;
      border: 1px solid #ccc;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      z-index: 1000;
    }
  
    .overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.5);
      z-index: 999;
      display: {isUserLoggedIn ? 'block' : 'none'};
    }
  </style>
  
  <div class="overlay" on:click={toggleLogin}>
    <div class="popup" on:click={(e) => e.stopPropagation()}>
      {isUserLoggedIn ? (
        <div>
          <p>Welcome, User!</p>
          <button on:click={handleLogout}>Logout</button>
        </div>
      ) : (
        <div>
          <p>Login Form</p>
          <button on:click={handleLogin}>Login</button>
        </div>
      )}
    </div>
  </div>
  
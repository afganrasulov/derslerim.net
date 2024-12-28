---
{"dg-publish":true,"permalink":"/test-delete-after/hello/","tags":["gardenEntry"]}
---

<!-- Firebase SDK -->
<script src="https://www.gstatic.com/firebasejs/9.17.1/firebase-app.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.17.1/firebase-auth.js"></script>

<script>
  // Firebase Configuration
  const firebaseConfig = {
    apiKey: "AIzaSyAL0eJaJQC1qBG-NuYzjGPmbfvlYdZs1VY",
    authDomain: "derslerim-6488b.firebaseapp.com",
    projectId: "derslerim-6488b",
    storageBucket: "derslerim-6488b.firebasestorage.app",
    messagingSenderId: "1008025347823",
    appId: "1:1008025347823:web:7ef5dd6a63c17a8e3b5d1a",
    measurementId: "G-X84QN8NYF0",
  };

  // Initialize Firebase
  const app = firebase.initializeApp(firebaseConfig);
  const auth = firebase.getAuth(app);

  // Login Function
  async function loginUser() {
    const emailInput = document.getElementById("email");
    const passwordInput = document.getElementById("password");

    const email = emailInput.value.trim();
    const password = passwordInput.value.trim();

    if (!email || !password) {
      alert("Please enter both email and password!");
      return;
    }

    try {
      // Firebase login
      await firebase.signInWithEmailAndPassword(auth, email, password);
      alert("Login successful!");
      // Redirect to your protected page
      window.location.href = "https://zingy-treacle-913ae0.netlify.app/test-delete-after/untitled/";
    } catch (error) {
      console.error("Login error:", error.message);
      alert("Login failed: " + error.message);
    }
  }
</script>

<style>
  .login-container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    font-family: Arial, sans-serif;
    background-color: #f4f4f9;
  }
  .login-box {
    width: 300px;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background: #fff;
    box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
    text-align: center;
  }
  .login-box input {
    width: 100%;
    padding: 10px;
    margin: 10px 0;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  .login-box button {
    width: 100%;
    padding: 10px;
    background-color: #007bff;
    border: none;
    border-radius: 5px;
    color: white;
    cursor: pointer;
    font-size: 16px;
  }
  .login-box button:hover {
    background-color: #0056b3;
  }
</style>

<div class="login-container">
  <div class="login-box">
    <h2>Login</h2>
    <input type="email" id="email" placeholder="Enter your email" />
    <input type="password" id="password" placeholder="Enter your password" />
    <button onclick="loginUser()">Login</button>
  </div>
</div>

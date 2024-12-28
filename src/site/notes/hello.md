---
{"dg-publish":true,"permalink":"/test-delete-after/hello/","tags":["gardenEntry"]}
---

<style>
  .login-container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    font-family: Arial, sans-serif;
  }
  .login-box {
    width: 300px;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    background-color: #f9f9f9;
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
    border: none;
    border-radius: 5px;
    background-color: #007bff;
    color: white;
    cursor: pointer;
  }
  .login-box button:hover {
    background-color: #0056b3;
  }
</style>

<div class="login-container">
  <div class="login-box">
    <h2>Giriş Yap</h2>
    <input type="email" id="email" placeholder="E-posta adresinizi girin" />
    <button onclick="loginUser()">Giriş Yap</button>
  </div>
</div>

<script>
  async function loginUser() {
    try {
      const emailInput = document.getElementById("email");
      const email = emailInput.value.trim();

      if (!email) {
        alert("Lütfen bir e-posta adresi girin!");
        return;
      }

      // Daha önce localStorage'da kayıtlı e-posta var mı ve geçerli mi?
      const savedEmail = localStorage.getItem("userEmail");
      const expirationTime = localStorage.getItem("expirationTime");

      if (savedEmail && expirationTime && new Date().getTime() < expirationTime) {
        alert("Erişim izni verildi! Tekrar giriş yapmanız gerekmiyor.");
        window.location.href = "https://zingy-treacle-913ae0.netlify.app/test-delete-after/untitled/";
        return;
      }

      // Fetch ile giriş doğrulaması
      const response = await fetch("https://script.google.com/macros/s/AKfycbwGbcD6wE7bA8ihlFXyQGkeBy7Ps7_elv57Yh44MH6wY2ymt_P-EkUdoaF-RHgLh1YYYQ/exec", {
        method: "POST",
        headers: { "Content-Type": "application/x-www-form-urlencoded" },
        body: new URLSearchParams({ email }),
      });

      const result = await response.text();
      if (result.trim() === "authorized") {
        // E-posta ve geçerlilik süresini kaydet
        localStorage.setItem("userEmail", email);
        localStorage.setItem("expirationTime", new Date().getTime() + 24 * 60 * 60 * 1000); // 24 saat
        alert("Erişim izni verildi!");
        window.location.href = "https://zingy-treacle-913ae0.netlify.app/test-delete-after/untitled/";
      } else if (result.trim() === "already_logged_in") {
        alert("Bu e-posta ile zaten başka bir oturum açık!");
      } else {
        alert("Erişim reddedildi!");
      }
    } catch (error) {
      console.error("Hata:", error);
      alert("Bir hata oluştu. Lütfen tekrar deneyin.");
    }
  }
</script>

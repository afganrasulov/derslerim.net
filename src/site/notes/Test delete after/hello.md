---
{"dg-publish":true,"permalink":"/test-delete-after/hello/","tags":["gardenEntry"]}
---

<script>
  async function authenticateUser() {
    try {
      const email = prompt("Lütfen e-posta adresinizi girin:");
      if (!email) {
        alert("E-posta girmeden devam edemezsiniz!");
        window.location.href = "/";
        return;
      }

      const response = await fetch("https://script.google.com/macros/s/AKfycbwGbcD6wE7bA8ihlFXyQGkeBy7Ps7_elv57Yh44MH6wY2ymt_P-EkUdoaF-RHgLh1YYYQ/exec", {
        method: "POST",
        headers: { "Content-Type": "application/x-www-form-urlencoded" },
        body: new URLSearchParams({ email }),
      });

      const result = await response.text();
      if (result.trim() === "authorized") {
        alert("Erişim izni verildi!");
      } else if (result.trim() === "already_logged_in") {
        alert("Bu e-posta ile zaten başka bir oturum açık!");
        window.location.href = "/";
      } else {
        alert("Erişim reddedildi! Ana sayfaya yönlendiriliyorsunuz.");
        window.location.href = "/";
      }
    } catch (error) {
      console.error("Bir hata oluştu:", error);
      alert("Doğrulama sırasında bir hata oluştu. Lütfen daha sonra tekrar deneyin.");
      window.location.href = "/";
    }
  }

  async function logoutUser() {
    const email = prompt("Çıkış yapmak istediğiniz e-posta adresini girin:");
    if (!email) {
      alert("E-posta adresi girmelisiniz!");
      return;
    }

    const response = await fetch(`https://script.google.com/macros/s/AKfycbwGbcD6wE7bA8ihlFXyQGkeBy7Ps7_elv57Yh44MH6wY2ymt_P-EkUdoaF-RHgLh1YYYQ/exec?logout=true&email=${encodeURIComponent(email)}`, {
      method: "GET",
    });

    const result = await response.text();
    if (result.trim() === "logged_out") {
      alert("Başarıyla çıkış yaptınız!");
      window.location.href = "/";
    } else {
      alert("Çıkış işlemi başarısız!");
    }
  }

  authenticateUser();
</script>

<button onclick="logoutUser()">Çıkış Yap</button>

hello world
<div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/960112301?h=3cf377f641&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture; clipboard-write" style="position:absolute;top:0;left:0;width:100%;height:100%;" title="ANI_12"></iframe></div>

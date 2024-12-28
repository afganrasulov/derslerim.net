---
{"dg-publish":true,"permalink":"/test-delete-after/hello/","tags":["gardenEntry"]}
---

<script>
  async function authenticateUser() {
    const email = prompt("Lütfen e-posta adresinizi girin:");
    const response = await fetch("https://script.google.com/macros/s/AKfycbx3Wg2ZZsif34nqyRzn2k6vRrb_HdQsZxHNmw24amchmRj3qGG95_DuQiyf8f6eNDA8_Q/exec", {
      method: "POST",
      headers: { "Content-Type": "application/x-www-form-urlencoded" },
      body: new URLSearchParams({ email }),
    });
    const result = await response.text();
    if (result !== "authorized") {
      alert("Erişim reddedildi! Ana sayfaya yönlendiriliyorsunuz.");
      window.location.href = "/";
    }
  }
  authenticateUser();
</script>

hello world
<div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/960112301?h=3cf377f641&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture; clipboard-write" style="position:absolute;top:0;left:0;width:100%;height:100%;" title="ANI_12"></iframe></div>

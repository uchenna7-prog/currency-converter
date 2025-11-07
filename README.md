

<script>
  const form = document.getElementById('contactForm');
  const responseMsg = document.getElementById('responseMessage');

  form.addEventListener('submit', async (e) => {
    e.preventDefault();

    const name = document.getElementById('name').value;
    const email = document.getElementById('email').value;
    const message = document.getElementById('message').value;

    try {
      const res = await fetch('https://your-backend-url.onrender.com/contact', { // replace with your Render backend URL later
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify({ name, email, message })
      });

      const data = await res.json();

      if (data.success) {
        responseMsg.textContent = "✅ Message sent successfully!";
        responseMsg.style.color = "green";
        form.reset();
      } else {
        responseMsg.textContent = "❌ Failed to send message. Try again.";
        responseMsg.style.color = "red";
      }

    } catch (error) {
      responseMsg.textContent = "⚠️ Error connecting to server.";
      responseMsg.style.color = "orange";
      console.error(error);
    }
  });
</script>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Travel Risk Report Form</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 20px;
      background: #f7f7f7;
    }
    h2 {
      color: #333;
    }
    form {
      background: #fff;
      padding: 20px;
      border-radius: 8px;
      max-width: 500px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }
    label {
      display: block;
      margin-bottom: 10px;
      font-weight: bold;
    }
    input {
      width: 100%;
      padding: 8px;
      margin-top: 4px;
      margin-bottom: 15px;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    button {
      padding: 10px 20px;
      font-size: 16px;
      background-color: #2ecc71;
      color: white;
      border: none;
      border-radius: 4px;
      cursor: pointer;
    }
    button:hover {
      background-color: #27ae60;
    }
    #response {
      margin-top: 15px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <h2>Trigger Travel Risk Report</h2>
  <form id="travelForm">
    <label>Destination:
      <input type="text" name="destination" required>
    </label>

    <label>Airport:
      <input type="text" name="airport">
    </label>

    <label>Train Station:
      <input type="text" name="trainStation">
    </label>

    <label>Bus Station:
      <input type="text" name="busStation">
    </label>

    <label>Hotel:
      <input type="text" name="hotel">
    </label>

    <button type="submit">Submit</button>
  </form>

  <p id="response"></p>

  <script>
    const form = document.getElementById('travelForm');
    const response = document.getElementById('response');

    form.addEventListener('submit', async (e) => {
      e.preventDefault();
      response.style.color = '#333';
      response.textContent = 'Submitting...';

      const formData = new FormData(form);
      const data = Object.fromEntries(formData.entries());

      try {
        const res = await fetch('https://dtts.app.n8n.cloud/webhook-test/eb47b7df-7354-44c2-a4fc-2499d1b37704', {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify(data)
        });

        if (res.ok) {
          response.style.color = 'green';
          response.textContent = 'Workflow triggered successfully!';
          form.reset();
        } else {
          response.style.color = 'red';
          response.textContent = 'Error triggering workflow.';
        }
      } catch (err) {
        console.error(err);
        response.style.color = 'red';
        response.textContent = 'Error triggering workflow.';
      }
    });
  </script>
</body>
</html>

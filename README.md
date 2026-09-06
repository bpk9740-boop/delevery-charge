# delevery-charge
Delivery Charge Website - Customer Delivery Information and Charge Management System
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>Delivery Charge</title>

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: Arial, sans-serif;
    }

    body {
      background: #f4f6f8;
      color: #222;
    }

    .header {
      background: #1769aa;
      color: white;
      padding: 25px 20px;
      text-align: center;
    }

    .header h1 {
      font-size: 28px;
      margin-bottom: 8px;
    }

    .header p {
      font-size: 15px;
      opacity: 0.9;
    }

    .container {
      width: 92%;
      max-width: 500px;
      margin: 25px auto;
    }

    .card {
      background: white;
      padding: 22px;
      border-radius: 15px;
      box-shadow: 0 5px 20px rgba(0,0,0,0.08);
      margin-bottom: 20px;
    }

    .card h2 {
      font-size: 21px;
      margin-bottom: 18px;
      color: #1769aa;
    }

    label {
      display: block;
      margin-top: 14px;
      margin-bottom: 6px;
      font-weight: bold;
    }

    input, select {
      width: 100%;
      padding: 13px;
      border: 1px solid #ccc;
      border-radius: 9px;
      font-size: 16px;
      outline: none;
    }

    input:focus, select:focus {
      border-color: #1769aa;
    }

    .btn {
      width: 100%;
      padding: 14px;
      margin-top: 20px;
      border: none;
      border-radius: 9px;
      background: #1769aa;
      color: white;
      font-size: 17px;
      font-weight: bold;
      cursor: pointer;
    }

    .btn:hover {
      background: #0f568e;
    }

    .result {
      display: none;
      margin-top: 20px;
      padding: 18px;
      background: #eef7ff;
      border-radius: 10px;
      text-align: center;
    }

    .result h3 {
      color: #1769aa;
      margin-bottom: 8px;
    }

    .charge {
      font-size: 30px;
      font-weight: bold;
      margin-top: 8px;
    }

    .info {
      line-height: 1.7;
      color: #555;
    }

    .notice {
      font-size: 13px;
      color: #666;
      margin-top: 15px;
      line-height: 1.5;
    }

    footer {
      text-align: center;
      padding: 25px 10px;
      color: #777;
      font-size: 13px;
    }
  </style>
</head>

<body>

  <div class="header">
    <h1>🚚 Delivery Charge</h1>
    <p>Delivery information and charge calculator</p>
  </div>

  <div class="container">

    <div class="card">
      <h2>📦 Calculate Delivery Charge</h2>

      <label for="distance">Delivery Distance</label>
      <input
        type="number"
        id="distance"
        placeholder="Enter distance in KM"
        min="0"
      >

      <label for="weight">Package Weight</label>
      <select id="weight">
        <option value="0">Up to 1 KG</option>
        <option value="30">1 - 5 KG</option>
        <option value="60">5 - 10 KG</option>
        <option value="100">Above 10 KG</option>
      </select>

      <button class="btn" onclick="calculateCharge()">
        Calculate Charge
      </button>

      <div class="result" id="result">
        <h3>Estimated Delivery Charge</h3>
        <div class="charge" id="charge">₹0</div>
        <p class="notice">
          This is an estimated charge. Final charges may vary according
          to the actual delivery service and package details.
        </p>
      </div>
    </div>


    <div class="card">
      <h2>📋 Delivery Information</h2>

      <div class="info">
        <p>✅ Safe and convenient delivery information</p>
        <p>📦 Charges depend on distance and package weight</p>
        <p>🚚 Delivery availability depends on service area</p>
        <p>📞 Contact the delivery provider for final confirmation</p>
      </div>
    </div>


    <div class="card">
      <h2>ℹ️ Important Notice</h2>

      <p class="info">
        Please verify the delivery provider and the final amount
        before making any payment. Do not share OTP, PIN, password,
        or banking credentials with anyone.
      </p>
    </div>

  </div>

  <footer>
    © 2026 Delivery Charge Website
  </footer>


  <script>
    function calculateCharge() {

      const distance = parseFloat(
        document.getElementById("distance").value
      );

      const weightCharge = parseFloat(
        document.getElementById("weight").value
      );

      if (isNaN(distance) || distance < 0) {
        alert("Please enter a valid delivery distance.");
        return;
      }

      // Base charge
      let charge = 40;

      // Distance charge
      if (distance > 5) {
        charge += (distance - 5) * 10;
      }

      // Weight charge
      charge += weightCharge;

      charge = Math.round(charge);

      document.getElementById("charge").innerText = "₹" + charge;
      document.getElementById("result").style.display = "block";
    }
  </script>

</body>
</html>

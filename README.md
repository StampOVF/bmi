<!DOCTYPE html>
<html lang="th">

<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>เครื่องคำนวณ BMI</title>
  <!-- นำเข้าฟอนต์ Prompt -->
  <link href="https://fonts.googleapis.com/css2?family=Prompt&display=swap" rel="stylesheet" />
  <style>
    body {
      font-family: 'Prompt', sans-serif;
      background: linear-gradient(to right, #83a4d4, #b6fbff);
      text-align: center;
      padding: 40px;
      margin: 0;
    }

    .container {
      background-color: white;
      max-width: 500px;
      margin: auto;
      padding: 50px 30px;
      border-radius: 20px;
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
    }

    h1 {
      color: #333;
      margin-bottom: 10px;
    }

    p {
      color: #555;
      margin-bottom: 30px;
    }

    input {
      width: 90%;
      padding: 12px;
      margin: 10px 0;
      border-radius: 10px;
      border: 1px solid #ccc;
      transition: all 0.3s ease;
      font-size: 16px;
    }

    input:focus {
      outline: none;
      border-color: #00bfff;
      box-shadow: 0 0 5px rgba(0, 191, 255, 0.5);
    }

    button {
      background-color: #00bfff;
      color: white;
      border: none;
      padding: 12px 30px;
      border-radius: 10px;
      font-size: 18px;
      cursor: pointer;
      margin-top: 10px;
      transition: 0.3s;
    }

    button:hover {
      background-color: #009acd;
    }

    .result {
      margin-top: 25px;
      font-size: 20px;
      padding: 20px;
      border-radius: 12px;
      background-color: #f2f2f2;
      transition: 0.3s;
    }

    @media (max-width: 600px) {
      .container {
        padding: 30px 20px;
      }

      input {
        width: 100%;
      }
    }
  </style>
</head>

<body>

  <div class="container">
    <h1>เครื่องคำนวณ BMI</h1>
    <p>กรอกข้อมูลของคุณ:</p>
    <input type="number" id="weight" placeholder="น้ำหนัก (กิโลกรัม)">
    <br>
    <input type="number" id="height" placeholder="ส่วนสูง (เซนติเมตร)">
    <br>
    <button onclick="calculateBMI()">คำนวณ</button>

    <div class="result" id="result"></div>
  </div>

  <script>
    function calculateBMI() {
      const weight = parseFloat(document.getElementById("weight").value);
      const height = parseFloat(document.getElementById("height").value) / 100;
      const resultEl = document.getElementById("result");
      if (!weight || !height || weight <= 0 || height <= 0) {
        resultEl.style.backgroundColor = "#ffe0e0";
        resultEl.innerHTML = "กรุณากรอกน้ำหนักและส่วนสูงให้ถูกต้อง";
        return;
      }
      const bmi = weight / (height * height);
      let category = "";
      let color = "";
      if (bmi < 18.5) {
        category = "น้ำหนักน้อย";
        color = "#fff3cd"; // เหลืองอ่อน
      } else if (bmi < 24.9) {
        category = "ปกติ";
        color = "#d4edda"; // เขียวอ่อน
      } else if (bmi < 29.9) {
        category = "น้ำหนักเกิน";
        color = "#ffeeba"; // ส้มอ่อน
      } else {
        category = "อ้วน";
        color = "#f8d7da"; // แดงอ่อน
      }
      resultEl.style.backgroundColor = color;
      resultEl.innerHTML = `BMI ของคุณคือ <strong>${bmi.toFixed(2)}</strong><br>อยู่ในเกณฑ์: <strong>${category}</strong>`;
    }
  </script>

  </body>

</html>

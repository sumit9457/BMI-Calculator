# BMI-Calculator
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>BMI Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f4f4;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    .calculator {
      background: #fff;
      padding: 20px 30px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
      width: 300px;
    }
    h2 {
      text-align: center;
      margin-bottom: 20px;
    }
    label {
      display: block;
      margin-top: 10px;
    }
    input[type="number"] {
      width: 100%;
      padding: 8px;
      margin-top: 5px;
      box-sizing: border-box;
    }
    .result {
      margin-top: 20px;
      text-align: center;
    }
    .badge {
      display: inline-block;
      padding: 5px 10px;
      border-radius: 5px;
      color: #fff;
      margin-top: 10px;
    }
    .underweight { background-color: #2196F3; }
    .normal { background-color: #4CAF50; }
    .overweight { background-color: #FF9800; }
    .obese { background-color: #F44336; }
  </style>
</head>
<body>
  <div class="calculator">
    <h2>BMI Calculator</h2>
    <label for="height">Height (cm):</label>
    <input type="number" id="height" placeholder="Enter height in cm" />

    <label for="weight">Weight (kg):</label>
    <input type="number" id="weight" placeholder="Enter weight in kg" />

    <div class="result" id="result"></div>
  </div>

  <script>
    const heightInput = document.getElementById('height');
    const weightInput = document.getElementById('weight');
    const resultDiv = document.getElementById('result');

    function calculateBMI() {
      const height = parseFloat(heightInput.value);
      const weight = parseFloat(weightInput.value);

      if (height > 0 && weight > 0) {
        const heightInMeters = height / 100;
        const bmi = weight / (heightInMeters * heightInMeters);
        let category = '';
        let badgeClass = '';

        if (bmi < 18.5) {
          category = 'Underweight';
          badgeClass = 'underweight';
        } else if (bmi >= 18.5 && bmi < 25) {
          category = 'Normal';
          badgeClass = 'normal';
        } else if (bmi >= 25 && bmi < 30) {
          category = 'Overweight';
          badgeClass = 'overweight';
        } else {
          category = 'Obese';
          badgeClass = 'obese';
        }

        resultDiv.innerHTML = `
          <p>Your BMI is ${bmi.toFixed(2)}</p>
          <span class="badge ${badgeClass}">${category}</span>
        `;
      } else {
        resultDiv.innerHTML = '';
      }
    }

    heightInput.addEventListener('input', calculateBMI);
    weightInput.addEventListener('input', calculateBMI);
  </script>
</body>
</html>


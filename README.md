#
Калькулятор Матриці долі
<html lang="uk">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Калькулятор Матриці Долі</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: #0e0d12;
      color: #f5f5f5;
      text-align: center;
      padding: 2rem;
    }

    h1 {
      color: #e0b64c;
    }

    input, button {
      padding: 10px;
      font-size: 1.2rem;
      border-radius: 8px;
      border: none;
      margin: 10px;
    }

    button {
      background: #e0b64c;
      color: #0e0d12;
      cursor: pointer;
      transition: 0.3s;
    }

    button:hover {
      background: #f4d35e;
    }

    .result {
      margin-top: 2rem;
    }

    .matrix-img {
      max-width: 300px;
      margin-top: 20px;
    }
  </style>
</head>
<body>
  <h1>Калькулятор Матриці Долі</h1>
  <p>Введіть вашу дату народження:</p>
  <input type="date" id="birthdate">
  <br>
  <button onclick="calculateMatrix()">Розрахувати</button>

  <div class="result" id="result"></div>

  <script>
    function sumDigits(n) {
      return n.toString().split('').reduce((acc, digit) => acc + Number(digit), 0);
    }

    function reduceToArkan(n) {
      while (n > 22) n = sumDigits(n);
      return n === 0 ? 22 : n;
    }

    function calculateMatrix() {
      const dateInput = document.getElementById("birthdate").value;
      if (!dateInput) {
        alert("Будь ласка, введіть дату народження.");
        return;
      }

      const [year, month, day] = dateInput.split("-").map(Number);

      const numbers = [
        day,
        month,
        year,
        sumDigits(day + month + year),
        sumDigits(day) + sumDigits(month) + sumDigits(year)
      ];

      const arkans = numbers.map(reduceToArkan);

      const resultDiv = document.getElementById("result");
      resultDiv.innerHTML = `
        <h2>Ваші аркани:</h2>
        <p>${arkans.join(" • ")}</p>
        <p>Це базовий розрахунок. Для повної розшифровки запишіться на консультацію 👇</p>
        <a href="https://forms.gle/D76ukkbWQzGSs4bu7" target="_blank">
          <button>Записатися</button>
        </a>
        <div>
       <img class="matrix-img" src="matrix.png" alt="Матриця Долі">
       <img class="matrix-img" src="example.png" alt="Приклад розшифровки">
        </div>
        <p>Слідкуй за оновленнями у 
          <a style="color:#e0b64c;" href="https://t.me/+RHPNwc7DmwliNWIy" target="_blank">Telegram</a> або 
          <a style="color:#e0b64c;" href="https://www.instagram.com/nataliianikoliak?igsh=Z3JvbGg4MDEzMDBi" target="_blank">Instagram</a>
        </p>
      `;
    }
  </script>
</body>
</html>

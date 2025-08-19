# Safal
Student grade card
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Student Marks & Grade Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f2f6fc;
      display: flex;
      justify-content: center;
      align-items: flex-start;
      
    }
    .container {
      
      background: white
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    }
    h2 {
      text-align: center;
      margin-bottom: 20px;
      color: #333;
    }
    .inputs {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-bottom: 20px;
      justify-content: center;
    }
    .inputs input {
      width: 120px;
      padding: 8px;
      border-radius: 6px;
      border: 1px solid #ccc;
    }
    button {
      padding: 10px 20px;
      border: none;
      border-radius: 6px;
      cursor: pointer;
      font-weight: bold;
      background: #007bff;
      color: white;
      transition: 0.2s;
    }
    button:hover { background: #0056b3; }
    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 20px;
    }
    table th, table td {
      border: 1px solid #ccc;
      padding: 10px;
      text-align: center;
    }
    table th {
      background: #007bff;
      color: white;
    }
    .result {
      margin-top: 15px;
      text-align: center;
      font-size: 18px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>🎓 Student Marks & Grade Calculator</h2>
    
    <div>
      <label>Student Name: </label>
      <input type="text" id="studentName" placeholder="Enter name">
    </div>

    <div class="inputs">
      <input type="number" id="s1" placeholder="Subject 1" min="0" max="100">
      <input type="number" id="s2" placeholder="Subject 2" min="0" max="100">
      <input type="number" id="s3" placeholder="Subject 3" min="0" max="100">
      <input type="number" id="s4" placeholder="Subject 4" min="0" max="100">
      <input type="number" id="s5" placeholder="Subject 5" min="0" max="100">
    </div>

    <div style="text-align:center;">
      <button onclick="calculateGrade()">Add Student</button>
    </div>

    <table id="resultTable">
      <thead>
        <tr>
          <th>Name</th>
          <th>S1</th>
          <th>S2</th>
          <th>S3</th>
          <th>S4</th>
          <th>S5</th>
          <th>Total</th>
          <th>Percent</th>
          <th>Grade</th>
        </tr>
      </thead>
      <tbody></tbody>
    </table>
  </div>

  <script>
    function getGrade(percent) {
      if (percent >= 90) return "A+";
      if (percent >= 80) return "A";
      if (percent >= 70) return "B";
      if (percent >= 60) return "C";
      if (percent >= 50) return "D";
      if (percent >= 40) return "E";
      return "F";
    }

    function calculateGrade() {
      const name = document.getElementById("studentName").value || "Student";
      const s1 = parseFloat(document.getElementById("s1").value) || 0;
      const s2 = parseFloat(document.getElementById("s2").value) || 0;
      const s3 = parseFloat(document.getElementById("s3").value) || 0;
      const s4 = parseFloat(document.getElementById("s4").value) || 0;
      const s5 = parseFloat(document.getElementById("s5").value) || 0;

      const total = s1 + s2 + s3 + s4 + s5;
      const percent = total / 5;
      const grade = getGrade(percent);

      const tableBody = document.querySelector("#resultTable tbody");
      const row = document.createElement("tr");
      row.innerHTML = `
        <td>${name}</td>
        <td>${s1}</td>
        <td>${s2}</td>
        <td>${s3}</td>
        <td>${s4}</td>
        <td>${s5}</td>
        <td>${total}</td>
        <td>${percent.toFixed(2)}%</td>
        <td>${grade}</td>
      `;
      tableBody.appendChild(row);

      // clear inputs
      document.getElementById("studentName").value = "";
      document.querySelectorAll(".inputs input").forEach(inp => inp.value = "");
    }
  </script>
</body>
</html>

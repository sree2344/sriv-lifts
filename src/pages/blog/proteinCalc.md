---
layout: '../../layouts/Post.astro'
title: Protein Per Day Calculator
image: /images/diet
publishedAt: "2025-01-23"
category: 'Nutrition'
---

<!--<h1>Protein Per Day Calculator</h1>-->

<p>Use this simple calculator to determine how much protein you need based on your body weight, gender, and activity level.</p>

<form id="protein-form">
  <label for="weight">Enter your weight (in pounds):</label>
  <input type="number" id="weight" name="weight" min="1" required>

  <label for="gender">Select your gender:</label>
  <select id="gender" name="gender" required>
    <option value="male">Male</option>
    <option value="female">Female</option>
  </select>

  <label for="activity">Select your activity level:</label>
  <select id="activity" name="activity" required>
    <option value="inactive">Inactive</option>
    <option value="active">Active</option>
  </select>

  <button type="submit">Calculate Protein Requirement</button>
</form>

<div id="protein-result" style="display: none;">
  <h2>Your Protein Requirement: <span id="protein-value"></span> grams/day</h2>
</div>

<script>
  document.getElementById('protein-form').addEventListener('submit', function(event) {
    event.preventDefault();

    const weight = parseFloat(document.getElementById('weight').value);
    const gender = document.getElementById('gender').value;
    const activity = document.getElementById('activity').value;

    if(weight && weight > 0) {
      let proteinMultiplier = 1.0;  // Default multiplier for inactive individuals

      // Adjust protein multiplier based on gender and activity level
      if (gender === "male") {
        proteinMultiplier = (activity === "active") ? 1.2 : 1.0;  // Active males need more protein
      } else if (gender === "female") {
        proteinMultiplier = (activity === "active") ? 1.1 : 1.0;  // Active females need slightly more protein
      }

      const proteinRequired = weight * proteinMultiplier;
      document.getElementById('protein-value').textContent = proteinRequired.toFixed(2);
      document.getElementById('protein-result').style.display = 'block';
    } else {
      alert("Please enter a valid weight.");
    }
  });
</script>

<style>
  body {
    font-family: Arial, sans-serif;
    margin: 20px;
    background-color: #f9f9f9;
    transition: background-color 0.3s, color 0.3s;
  }

  body.dark-mode {
    background-color: #181818;
    color: #f1f1f1;
  }

  h1, h2 {
    text-align: center;
    color: #333;
  }

  body.dark-mode h1, body.dark-mode h2 {
    color: #f1f1f1;
  }

  form {
    max-width: 500px;
    margin: 20px auto;
    background: #fff;
    padding: 30px;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  }

  body.dark-mode form {
    background: #333;
  }

  label {
    display: block;
    margin: 15px 0 5px;
    font-weight: bold;
  }

  input, select, button {
    width: 100%;
    padding: 10px;
    margin: 8px 0 20px;
    border: 1px solid #ccc;
    border-radius: 6px;
    font-size: 16px;
  }

  body.dark-mode input, body.dark-mode select, body.dark-mode button {
    background-color: #444;
    color: #f1f1f1;
    border: 1px solid #555;
  }

  button {
    background-color: #28a745;
    color: white;
    border: none;
    cursor: pointer;
    font-weight: bold;
  }

  button:hover {
    background-color: #218838;
  }

  body.dark-mode button:hover {
    background-color: #1e7e34;
  }

  #protein-result {
    text-align: center;
    margin-top: 30px;
  }

  p {
    line-height: 1.6;
    color: #555;
  }

  body.dark-mode p {
    color: #ddd;
  }
</style>

<!-- Importance of Protein Section -->
<section id="protein-importance">
  <h2>Why Protein is Important</h2>
  <p>Protein is one of the three macronutrients essential for building and repairing tissues, including muscles. It is vital for many body functions, such as immune response, hormone production, and enzyme creation.</p>
  <h3>Key Benefits of Protein:</h3>
  <ul>
    <li><strong>Muscle Growth and Repair:</strong> Protein is essential for repairing and building muscle tissue. If you're engaging in regular exercise or strength training, protein supports recovery and muscle growth.</li>
    <li><strong>Weight Management:</strong> Protein can help control hunger by promoting satiety. This helps in managing weight as it reduces cravings and keeps you feeling full longer.</li>
    <li><strong>Immune System Support:</strong> Protein helps in the production of antibodies and other immune cells, crucial for maintaining a healthy immune system.</li>
    <li><strong>Enzyme and Hormone Production:</strong> Proteins are involved in creating hormones and enzymes that control various bodily functions, from digestion to metabolic regulation.</li>
    <li><strong>Healthy Skin, Hair, and Nails:</strong> Collagen and keratin, which support skin, hair, and nails, are proteins that need to be replenished regularly through diet.</li>
  </ul>
</section>

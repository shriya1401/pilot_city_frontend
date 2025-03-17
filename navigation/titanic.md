---
layout: post
title: Titanic
permalink: /titanic/
comments: true
---

<h1>Calculate Your Chance of Surviving the Titanic</h1>
<form id="survivalForm">
    <label for="pclass">Pclass (1-3):</label>
    <input type="number" id="pclass" min="1" max="3" required><br><br>

    <label for="sex">Sex:</label>
    <select id="sex" required>
        <option value="male">Male</option>
        <option value="female">Female</option>
    </select><br><br>

    <label for="age">Age:</label>
    <input type="number" id="age" min="0" required><br><br>

    <label for="sibsp">Siblings/Spouse Aboard (SibSp):</label>
    <input type="number" id="sibsp" min="0" required><br><br>

    <label for="parch">Parents/Children Aboard (Parch):</label>
    <input type="number" id="parch" min="0" required><br><br>

    <label for="fare">Fare:</label>
    <input type="number" id="fare" min="0" step="0.01" required><br><br>

    <label for="embarked">Embarked:</label>
    <select id="embarked" required>
        <option value="C">Cherbourg</option>
        <option value="Q">Queenstown</option>
        <option value="S">Southampton</option>
    </select><br><br>

    <label for="alone">Alone:</label>
    <input type="checkbox" id="alone"><br><br>

    <button type="submit">Calculate My Chance</button>
</form>

<h2 id="result"></h2>

<script type="module">
  import { pythonURI, fetchOptions } from '{{ site.baseurl }}/assets/js/api/config.js';

  // Handle the form submission to calculate survival chance
  document.getElementById("survivalForm").addEventListener("submit", async function(event) {
    event.preventDefault();

    // Get values from the form
    const pclass = parseInt(document.getElementById("pclass").value);
    const sex = document.getElementById("sex").value;
    const age = parseInt(document.getElementById("age").value);
    const sibsp = parseInt(document.getElementById("sibsp").value);
    const parch = parseInt(document.getElementById("parch").value);
    const fare = parseFloat(document.getElementById("fare").value);
    const embarked = document.getElementById("embarked").value;
    const alone = document.getElementById("alone").checked;

    // Input Validation
    if (isNaN(pclass) || pclass < 1 || pclass > 3) {
        alert("Pclass must be a number between 1 and 3.");
        return;
    }
    if (isNaN(age) || age <= 0) {
        alert("Age must be a positive number.");
        return;
    }
    if (isNaN(sibsp) || sibsp < 0) {
        alert("Siblings/Spouse Aboard (SibSp) must be a non-negative number.");
        return;
    }
    if (isNaN(parch) || parch < 0) {
        alert("Parents/Children Aboard (Parch) must be a non-negative number.");
        return;
    }
    if (isNaN(fare) || fare < 0) {
        alert("Fare must be a non-negative number.");
        return;
    }

    // Prepare data to send to the backend
    const postData = {
        Pclass: pclass,
        Sex: sex,
        Age: age,
        SibSp: sibsp,
        Parch: parch,
        Fare: fare,
        Embarked: embarked,
        Alone: alone
    };

    console.log("Survival Data:", postData); // Log the data to check before sending

    try {
        const response = await fetch(`${pythonURI}/api/titanic/predict`, {
            ...fetchOptions,
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify(postData)
        });

        if (!response.ok) {
            const errorMessage = await response.text();
            throw new Error(`Failed to calculate survival chance: ${response.statusText} - ${errorMessage}`);
        }

        const result = await response.json();
        document.getElementById("result").innerText = 
            `Your chance of surviving Titanic: ${(result.survive * 100).toFixed(2)}%`;
    } catch (error) {
        console.error("Error:", error);
        document.getElementById("result").innerText = "There was an error calculating your chance of survival.";
    }
  });
</script>

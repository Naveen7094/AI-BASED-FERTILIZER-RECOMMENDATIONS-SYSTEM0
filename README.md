# AI-BASED-FERTILIZER-RECOMMENDATIONS-SYSTEM
<!DOCTYPE html>
<html>
<head>
    <title>Login - AI Fertilizer System</title>
    <meta charset="UTF-8">
    <style>
        body {
            font-family: Arial;
            background: #e8f5e9;
            text-align: center;
        }

        .box {
            width: 350px;
            margin: 100px auto;
            padding: 25px;
            background: white;
            border-radius: 10px;
            box-shadow: 0 0 10px gray;
        }

        input {
            width: 90%;
            padding: 10px;
            margin: 8px;
        }

        button {
            padding: 10px 15px;
            background: green;
            color: white;
            border: none;
            cursor: pointer;
        }

        button:hover {
            background: darkgreen;
        }

        #error {
            color: red;
        }
    </style>
</head>
<body>

<div class="box">
    <h2>AI Fertilizer Recommendation</h2>

    <form id="loginForm">
        <input type="text" id="username" placeholder="Username" required>
        <input type="password" id="password" placeholder="Password" required>
        <button type="submit">Login</button>
    </form>

    <p id="error"></p>
</div>

<script src="script.js"></script>

</body>
</html>
<!DOCTYPE html>
<html>
<head>
    <title>Fertilizer Recommendation</title>
    <meta charset="UTF-8">
    <style>
        body {
            font-family: Arial;
            background: #f1f8e9;
            text-align: center;
        }

        .container {
            width: 400px;
            margin: 60px auto;
            padding: 25px;
            background: white;
            border-radius: 10px;
            box-shadow: 0 0 10px gray;
        }

        input, select {
            width: 90%;
            padding: 10px;
            margin: 8px;
        }

        button {
            padding: 10px 15px;
            background: green;
            color: white;
            border: none;
            cursor: pointer;
        }

        button:hover {
            background: darkgreen;
        }

        #result {
            margin-top: 20px;
            font-weight: bold;
            color: blue;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>Enter Soil Details</h2>

    <input type="number" id="nitrogen" placeholder="Nitrogen (N)" required>
    <input type="number" id="phosphorus" placeholder="Phosphorus (P)" required>
    <input type="number" id="potassium" placeholder="Potassium (K)" required>
    <input type="number" step="0.1" id="ph" placeholder="Soil pH" required>

    <select id="crop">
        <option value="">Select Crop</option>
        <option value="Rice">Rice</option>
        <option value="Wheat">Wheat</option>
        <option value="Maize">Maize</option>
        <option value="Cotton">Cotton</option>
        <option value="Sugarcane">Sugarcane</option>
    </select>

    <button onclick="recommendFertilizer()">Get Recommendation</button>

    <div id="result"></div>

    <br><br>
    <button onclick="logout()">Logout</button>
</div>

<script src="script.js"></script>

</body>
</html>
// LOGIN SYSTEM
document.addEventListener("DOMContentLoaded", function () {

    const form = document.getElementById("loginForm");

    if (form) {
        form.addEventListener("submit", function (e) {
            e.preventDefault();

            let username = document.getElementById("username").value;
            let password = document.getElementById("password").value;

            if (username === "admin" && password === "1234") {
                localStorage.setItem("loggedIn", "true");
                window.location.href = "dashboard.html";
            } else {
                document.getElementById("error").innerText = "Invalid Login Details!";
            }
        });
    }

    // Protect dashboard
    if (window.location.pathname.includes("dashboard.html")) {
        if (localStorage.getItem("loggedIn") !== "true") {
            window.location.href = "index.html";
        }
    }

});


// AI FERTILIZER LOGIC
function recommendFertilizer() {

    let n = parseInt(document.getElementById("nitrogen").value);
    let p = parseInt(document.getElementById("phosphorus").value);
    let k = parseInt(document.getElementById("potassium").value);
    let ph = parseFloat(document.getElementById("ph").value);
    let crop = document.getElementById("crop").value;

    let recommendation = "";

    if (n < 50) {
        recommendation = "Urea (Nitrogen Deficiency)";
    }
    else if (p < 30) {
        recommendation = "DAP (Phosphorus Deficiency)";
    }
    else if (k < 40) {
        recommendation = "MOP (Potassium Deficiency)";
    }
    else if (ph < 6) {
        recommendation = "Apply Lime (Low pH Soil)";
    }
    else if (ph > 7.5) {
        recommendation = "Apply Gypsum (High pH Soil)";
    }
    else {
        recommendation = "NPK 20-20-20 (Balanced Fertilizer)";
    }

    document.getElementById("result").innerHTML =
        "Recommended Fertilizer for " + crop + " : " + recommendation;
}


// LOGOUT
function logout() {
    localStorage.removeItem("loggedIn");
    window.location.href = "index.html";
}

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

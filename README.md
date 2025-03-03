# Cryptography-DES-algorithum-
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DES Encryption/Decryption Animation</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 50px;
            background: #f4f4f9;
        }
        h1 {
            color: #333;
        }
        .container {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            gap: 20px;
            margin-top: 50px;
        }
        input, button {
            padding: 10px;
            margin: 10px;
            width: 300px;
            border: 1px solid #ccc;
            border-radius: 10px;
        }
        button {
            background: #007BFF;
            color: white;
            cursor: pointer;
            transition: 0.3s;
        }
        button:hover {
            background: #0056b3;
        }
        .animation {
            display: none;
            margin-top: 20px;
            padding: 20px;
            border: 2px solid #007BFF;
            border-radius: 10px;
            background: #e9f5ff;
            animation: fadeIn 2s ease-in-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.8); }
            to { opacity: 1; transform: scale(1); }
        }
        .steps {
            display: none;
            text-align: left;
            margin-top: 20px;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 10px;
            background: #f9f9f9;
        }
    </style>
</head>
<body>
<h1>DES Encryption/Decryption Animation</h1>
<div class="container">
    <input type="text" id="plaintext" placeholder="Enter Plain Text">
    <input type="password" id="key" placeholder="Enter 8-byte Key">
    <button onclick="encrypt()">Encrypt</button>
    <button onclick="decrypt()">Decrypt</button>
    <button onclick="showSteps()">Show Demonstration</button>
    <div class="animation" id="animation"></div>
    <div class="steps" id="steps">
        <h3>Program Demonstration:</h3>
        <p>Step 1: Input Plain Text and 8-byte Key.</p>
        <p>Step 2: Click on Encrypt or Decrypt Button.</p>
        <p>Step 3: Encryption uses Base64 Encoding for demonstration purposes.</p>
        <p>Step 4: Decryption will revert the Base64 encoded text.</p>
    </div>
</div>

<script>
    function encrypt() {
        let plaintext = document.getElementById("plaintext").value;
        let key = document.getElementById("key").value;
        let animation = document.getElementById("animation");
        
        if (key.length !== 8) {
            alert("Key must be 8 bytes long!");
            return;
        }
        if (plaintext === "") {
            alert("Please enter plaintext");
            return;
        }
        
        animation.style.display = "block";
        animation.innerHTML = `Encrypting: ${plaintext} with Key: ${key}...`;
        setTimeout(() => {
            animation.innerHTML = `Encrypted Text: ${btoa(plaintext)}`;
        }, 3000);
    }

    function decrypt() {
        let plaintext = document.getElementById("plaintext").value;
        let animation = document.getElementById("animation");
        
        if (plaintext === "") {
            alert("Please enter text to decrypt");
            return;
        }
        
        animation.style.display = "block";
        animation.innerHTML = `Decrypting...`;
        setTimeout(() => {
            try {
                animation.innerHTML = `Decrypted Text: ${atob(plaintext)}`;
            } catch (e) {
                animation.innerHTML = "Invalid Encrypted Text!";
            }
        }, 3000);
    }

    function showSteps() {
        let steps = document.getElementById("steps");
        steps.style.display = "block";
    }
</script>
</body>
</html>

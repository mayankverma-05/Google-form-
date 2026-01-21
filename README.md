# Google-form-
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Student Details Form</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: #f2f2f2;
        }
        .form-box {
            width: 350px;
            margin: 80px auto;
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.2);
        }
        h2 {
            text-align: center;
        }
        input {
            width: 100%;
            padding: 8px;
            margin: 10px 0;
        }
        button {
            width: 100%;
            padding: 10px;
            background: #4285f4;
            color: white;
            border: none;
            cursor: pointer;
            font-size: 16px;
        }
        button:hover {
            background: #3367d6;
        }
    </style>
</head>
<body>

<div class="form-box">
    <h2>Student Details</h2>

    <form onsubmit="submitForm(); return false;">
        <input type="number" id="roll" placeholder="Enter Roll Number" required>
        <input type="text" id="name" placeholder="Enter Name" required>
        <input type="text" id="class" placeholder="Enter Class" required>
        <button type="submit">Submit</button>
    <script>
    function submitForm() {
        let roll = document.getElementById("roll").value;
        let name = document.getElementById("name").value;
        let cls = document.getElementById("class").value;

        fetch("https://script.google.com/macros/s/AKfycbwnwq32RYtaNZHgjxsYLC_G6gkZ3mIpchpfATXFhXu-GH5Fsvljj7iOf06C4hV_rBW_/exec", {
            method: "POST",
            body: JSON.stringify({
                roll: roll,
                name: name,
                class: cls
            })
        })
        .then(() => {
            alert("Data Google Sheet me save ho gaya ✅");
        })
        .catch(() => {
            alert("Error: Data save nahi hua ❌");
        });
    }
</script>

</script>

</body>
</html>
<script>
function submitForm() {
    const data = {
        roll: document.getElementById("roll").value,
        name: document.getElementById("name").value,
        class: document.getElementById("class").value
    };

    fetch("https://script.google.com/macros/s/AKfycbwnwq32RYtaNZHgjxsYLC_G6gkZ3mIpchpfATXFhXu-GH5Fsvljj7iOf06C4hV_rBW_/exec", {
        method: "POST",
        body: JSON.stringify(data)
    })
    .then(res => alert("Data saved successfully!"))
    .catch(err => alert("Error saving data"));
}
</script>

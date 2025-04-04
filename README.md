<!DOCTYPE html>
<html>
<head>
    <title>Online Aptitude Test</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }
        .container {
            width: 80%;
            margin: auto;
            background: white;
            padding: 20px;
            margin-top: 50px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        .hidden {
            display: none;
        }
        h1 {
            text-align: center;
        }
        button {
            display: block;
            margin: 20px auto;
            padding: 10px 20px;
            background-color: #007BFF;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
        .question {
            margin-bottom: 15px;
        }
        input[type="text"], input[type="number"] {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ddd;
            border-radius: 5px;
        }
        .mandatory {
            color: red;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Details Page -->
        <div id="detailsPage">
            <h1>User Details</h1>
            <label for="name">Name:<span class="mandatory">*</span></label>
            <input type="text" id="name" placeholder="Enter your name" required>
            <br><br>
            <label for="rollno">Roll No:<span class="mandatory">*</span></label>
            <input type="number" id="rollno" placeholder="Enter your roll no" required>
            <br><br>
            <label for="department">Department:<span class="mandatory">*</span></label>
            <input type="text" id="department" placeholder="Enter your department" required>
            <br><br>
            <label for="collagename">College Name:<span class="mandatory">*</span></label>
            <input type="text" id="collagename" placeholder="Enter your college name" required>
            <br><br>
            <button onclick="validateDetails()">Start Test</button>
        </div>
        
        <!-- Questions Page -->
        <div id="questionsPage" class="hidden">
            <h1>Aptitude Test</h1>
            <div class="question">
                <p>Question 1: What is 5 + 3?</p>
                <input type="text" id="q1">
            </div>
            <div class="question">
                <p>Question 2: What is the color of the sky during a sunny day?</p>
                <input type="text" id="q2">
            </div>
            <div class="question">
                <p>Question 3: What comes after 10 in counting?</p>
                <input type="text" id="q3">
            </div>
            <div class="question">
                <p>Question 4: What is the opposite of hot?</p>
                <input type="text" id="q4">
            </div>
            <div class="question">
                <p>Question 5: How many sides does a square have?</p>
                <input type="text" id="q5">
            </div>
            <div class="question">
                <p>Question 6: If you have 2 apples and you buy 3 more, how many apples do you have?</p>
                <input type="text" id="q6">
            </div>
            <div class="question">
                <p>Question 7: What is 100 divided by 10?</p>
                <input type="text" id="q7">
            </div>
            <div class="question">
                <p>Question 8: What is the capital of India?</p>
                <input type="text" id="q8">
            </div>
            <div class="question">
                <p>Question 9: What is 10 - 6?</p>
                <input type="text" id="q9">
            </div>
            <div class="question">
                <p>Question 10: What is the shape of a ball?</p>
                <input type="text" id="q10">
            </div>
            <button onclick="showResults()">Submit</button>
        </div>
        
        <!-- Results Page -->
        <div id="resultsPage" class="hidden">
            <h1>Results</h1>
            <p>Thank you for completing the test, <span id="userName"></span>!</p>
            <p>Your Score: <span id="score"></span>/10</p>
        </div>
    </div>

    <script>
        const answers = {
            q1: "8",
            q2: "blue",
            q3: "11",
            q4: "cold",
            q5: "4",
            q6: "5",
            q7: "10",
            q8: "Delhi",
            q9: "4",
            q10: "round"
        };

        function validateDetails() {
            const name = document.getElementById("name").value.trim();
            const rollno = document.getElementById("rollno").value.trim();
            const department = document.getElementById("department").value.trim();
            const collagename = document.getElementById("collagename").value.trim();

            if (!name || !rollno || !department || !collagename) {
                alert("Please fill out all mandatory fields before proceeding.");
                return;
            }

            // Move to the next page if all fields are filled
            document.getElementById("detailsPage").classList.add("hidden");
            document.getElementById("questionsPage").classList.remove("hidden");
        }

        function showResults() {
            const name = document.getElementById("name").value;
            document.getElementById("userName").innerText = name;

            let score = 0;
            for (let key in answers) {
                const userAnswer = document.getElementById(key).value.trim().toLowerCase();
                if (userAnswer === answers[key].toLowerCase()) {
                    score++;
                }
            }

            document.getElementById("score").innerText = score;
            document.getElementById("questionsPage").classList.add("hidden");
            document.getElementById("resultsPage").classList.remove("hidden");
        }
    </script>
</body>
</html>

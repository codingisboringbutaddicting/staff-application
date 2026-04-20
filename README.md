<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Discord Staff Application</title>

<style>
body {
    font-family: Arial, sans-serif;
    background: #1e1f22;
    color: white;
    display: flex;
    justify-content: center;
    padding: 30px;
}

.container {
    width: 650px;
    background: #2b2d31;
    padding: 20px;
    border-radius: 12px;
}

h1 {
    text-align: center;
    margin-bottom: 10px;
}

.note {
    text-align: center;
    font-size: 13px;
    opacity: 0.8;
    margin-bottom: 20px;
    line-height: 1.4;
}

input, textarea {
    width: 100%;
    padding: 10px;
    margin-top: 10px;
    margin-bottom: 15px;
    border-radius: 6px;
    border: none;
    background: #1e1f22;
    color: white;
}

textarea {
    resize: vertical;
    height: 80px;
}

button {
    width: 100%;
    padding: 12px;
    background: #5865F2;
    border: none;
    border-radius: 8px;
    color: white;
    font-size: 16px;
    cursor: pointer;
}

button:disabled {
    background: #3b3d45;
    cursor: not-allowed;
}

button:hover:not(:disabled) {
    background: #4752c4;
}

.small {
    font-size: 12px;
    opacity: 0.7;
    text-align: center;
}
</style>
</head>

<body>

<div class="container">

<h1>Discord Staff Application</h1>

<p class="note">
All staff members are expected to follow server rules and act professionally at all times.<br>
Any misuse of permissions or abuse of power may result in removal or demotion from staff.<br>
Staff who violate server rules will receive appropriate disciplinary action, including possible rank reduction.
</p>

<input id="username" placeholder="Your Discord Username">

<textarea id="q1" placeholder="Why do you want to become staff?"></textarea>

<textarea id="q2" placeholder="Do you have any previous moderation experience? If yes, explain."></textarea>

<textarea id="q3" placeholder="What would you do if a higher-ranked staff member abused their powers?"></textarea>

<textarea id="q4" placeholder="How active can you be daily/weekly?"></textarea>

<textarea id="q5" placeholder="How would you handle a user breaking rules but claiming ignorance?"></textarea>

<textarea id="q6" placeholder="What makes you stand out from other applicants?"></textarea>

<textarea id="q7" placeholder="How would you handle conflict between two members?"></textarea>

<textarea id="q8" placeholder="What is the most important trait for a moderator and why?"></textarea>

<textarea id="q9" placeholder="Have you ever moderated a server before? What did you learn from it?"></textarea>

<button id="submitBtn" onclick="submitApp()">Submit Application</button>

<p class="small">Anti-spam enabled: 1 submission per 60 seconds</p>

</div>

<script>
let lastSubmitTime = 0;

function submitApp() {

    const now = Date.now();
    const button = document.getElementById("submitBtn");

    // ⛔ anti-spam cooldown
    if (now - lastSubmitTime < 60000) {
        alert("Please wait 60 seconds before submitting again.");
        return;
    }

    const username = document.getElementById("username").value.trim();

    if (!username) {
        alert("Please enter your Discord username.");
        return;
    }

    lastSubmitTime = now;
    button.disabled = true;

    const data = {
        username: username,
        answers: {
            reason: document.getElementById("q1").value,
            experience: document.getElementById("q2").value,
            abuse: document.getElementById("q3").value,
            activity: document.getElementById("q4").value,
            rulebreak: document.getElementById("q5").value,
            advantage: document.getElementById("q6").value,
            conflict: document.getElementById("q7").value,
            trait: document.getElementById("q8").value,
            past_mod: document.getElementById("q9").value
        }
    };

    console.log("APPLICATION DATA:", data);

    alert("Application submitted successfully!");

    setTimeout(() => {
        button.disabled = false;
    }, 60000);
}
</script>

</body>
</html>

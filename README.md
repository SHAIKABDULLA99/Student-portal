# Student-portal
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>School Registration Form</title>
    <style>
        /* CSS Styling */
        :root {
            --primary-blue: #2563eb;
            --bg-gray: #f8fafc;
            --border-gray: #e2e8f0;
            --text-dark: #1e293b;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--bg-gray);
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 40px 20px;
            color: var(--text-dark);
        }

        .header-section {
            text-align: center;
            margin-bottom: 30px;
        }

        .header-section h1 {
            font-size: 2.5rem;
            margin: 0;
            color: var(--primary-blue);
        }

        .header-section h1 span { color: #1e293b; }

        .form-card {
            background: white;
            padding: 40px;
            border-radius: 15px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.05);
            width: 100%;
            max-width: 650px;
        }

        .form-card h2 { text-align: center; margin-top: 0; margin-bottom: 5px; }
        .form-card p { text-align: center; color: #64748b; font-size: 0.9rem; margin-bottom: 30px; }

        .form-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
        }

        .form-group { margin-bottom: 15px; }
        .full-width { grid-column: span 2; }

        label { display: block; font-size: 0.85rem; font-weight: 600; margin-bottom: 8px; }

        input, select {
            width: 100%;
            padding: 12px;
            border: 1px solid var(--border-gray);
            border-radius: 8px;
            box-sizing: border-box;
            background-color: #fafafa;
        }

        .radio-group {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
            margin-top: 5px;
        }

        .radio-item { display: flex; align-items: center; font-size: 0.9rem; }
        .radio-item input { width: auto; margin-right: 8px; }

        .password-container { position: relative; }
        .eye-icon {
            position: absolute;
            right: 12px;
            top: 50%;
            transform: translateY(-50%);
            cursor: pointer;
            opacity: 0.5;
        }

        .button-group {
            display: flex;
            gap: 15px;
            margin-top: 30px;
        }

        .btn {
            flex: 1;
            padding: 12px;
            border-radius: 8px;
            border: none;
            cursor: pointer;
            font-weight: 600;
            transition: 0.2s;
        }

        .btn-register { background: var(--primary-blue); color: white; }
        .btn-register:hover { background: #1d4ed8; }

        .btn-clear { background: white; border: 1px solid var(--border-gray); color: #64748b; }
        .btn-clear:hover { background: #f1f5f9; }

        @media (max-width: 500px) {
            .form-grid { grid-template-columns: 1fr; }
            .full-width { grid-column: span 1; }
        }
    </style>
</head>
<body>

    <div class="header-section">
        <h1><span>School</span> Registration</h1>
        <h1>Form</h1>
        <p>Built with HTML, CSS & JavaScript</p>
    </div>

    <div class="form-card">
        <h2>Student Portal</h2>
        <p>Complete your school registration below</p>

        <form id="registrationForm">
            <div class="form-grid">
                <!-- Row 1 -->
                <div class="form-group">
                    <label>Full Name</label>
                    <input type="text" placeholder="Juan Dela Cruz" required>
                </div>
                <div class="form-group">
                    <label>Email Address</label>
                    <input type="email" placeholder="student@school.edu" required>
                </div>

                <!-- Row 2 -->
                <div class="form-group">
                    <label>Student ID</label>
                    <input type="text" placeholder="e.g. 202300123" required>
                </div>
                <div class="form-group">
                    <label>Course</label>
                    <select required>
                        <option value="" disabled selected>-- Select a Course --</option>
                        <option value="cs">Computer Science</option>
                        <option value="it">Information Technology</option>
                        <option value="eng">Engineering</option>
                    </select>
                </div>

                <!-- Year Level -->
                <div class="form-group full-width">
                    <label>Year Level</label>
                    <div class="radio-group">
                        <label class="radio-item"><input type="radio" name="year" value="0"> 0 Year</label>
                        <label class="radio-item"><input type="radio" name="year" value="1"> 1st Year</label>
                        <label class="radio-item"><input type="radio" name="year" value="2"> 2nd Year</label>
                        <label class="radio-item"><input type="radio" name="year" value="3"> 3rd Year</label>
                        <label class="radio-item"><input type="radio" name="year" value="4"> 4th Year</label>
                    </div>
                </div>

                <!-- Gender -->
                <div class="form-group full-width">
                    <label>Gender</label>
                    <div class="radio-group">
                        <label class="radio-item"><input type="radio" name="gender" value="male"> Male</label>
                        <label class="radio-item"><input type="radio" name="gender" value="female"> Female</label>
                        <label class="radio-item"><input type="radio" name="gender" value="other"> Other</label>
                    </div>
                </div>

                <!-- Password Row -->
                <div class="form-group password-container">
                    <label>Password</label>
                    <input type="password" id="pass" placeholder="At least 8 characters" required>
                    <span class="eye-icon" onclick="togglePass('pass')">👁️</span>
                </div>
                <div class="form-group password-container">
                    <label>Confirm Password</label>
                    <input type="password" id="confirm" placeholder="Confirm password" required>
                    <span class="eye-icon" onclick="togglePass('confirm')">👁️</span>
                </div>
            </div>

            <div class="button-group">
                <button type="submit" class="btn btn-register">Register Student</button>
                <button type="reset" class="btn btn-clear">Clear Form</button>
            </div>
        </form>
    </div>

    <script>
        // JavaScript for interactivity
        function togglePass(id) {
            const field = document.getElementById(id);
            field.type = field.type === "password" ? "text" : "password";
        }

        document.getElementById('registrationForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const pass = document.getElementById('pass').value;
            const confirm = document.getElementById('confirm').value;

            if (pass !== confirm) {
                alert("Passwords do not match!");
                return;
            }
            
            alert("Registration Successful!");
        });
    </script>
</body>
</html

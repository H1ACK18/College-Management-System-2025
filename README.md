<!DOCTYPE html>
<link rel="stylesheet" href="style1.css" type="text/css" media="all" />
<script src=".js" type="text/javascript" charset="utf-8"></script>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Automated Admission Application</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>University Admission Application</h1>
        <p>Please fill out the form below to apply for admission.</p>
    </header>
    <!-- Images Section -->
    <div class="images-section">
        <img src="https://mum.digitaluniversity.ac/user/pages/images/slides/slide1.jpg" alt="Admission Process">
        <img src="https://www.vancopayments.com/hubfs/Graduation%20-%20Cap%20throw.png" alt="University Life">
        <img src="https://www.met.edu/uploadfile/images/AboutMET.jpg" alt="Student Success">
    </div>

    <div class="container">
        <form id="admissionForm">
            <label for="name">Full Name:</label>
            <input type="text" id="name" name="name" required><br><br>

            <label for="email">Email:</label>
            <input type="email" id="email" name="email" required><br><br>

            <label for="course">Course Applying For:</label>
            <select id="course" name="course" required>
                <option value="computer-science">Computer Science</option>
                <option value="business-administration">Business Administration</option>
                <option value="medicine">Medicine</option>
                <option value="law">Law</option>
            </select><br><br>

            <label for="documents">Upload Documents (PDF, JPG, PNG):</label>
            <input type="file" id="documents" name="documents" accept=".pdf,.jpg,.png" required><br><br>

            <button type="submit">Submit Application</button>
        </form>
        
        <div id="statusMessage" class="hidden">
            <h2>Application Status</h2>
            <p>Your application has been <strong>submitted successfully</strong>.</p>
            <p>Status: <span id="status">Pending</span></p>
        </div>
    </div>

    <footer>
        <p>&copy; 2025 University Admission Portal</p>
    </footer>

    <script>
        // Handle form submission
        document.getElementById('admissionForm').addEventListener('submit', function(event) {
            event.preventDefault(); // Prevent default form submission

            // Show status message
            document.getElementById('statusMessage').classList.remove('hidden');
            document.getElementById('status').textContent = "Pending";

            // Optional: You can send form data to the backend here using JavaScript (AJAX)
            alert("Your application has been submitted! You will receive a response soon.");
            document.getElementById('admissionForm').reset(); // Reset form after submission
        });
    </script>
</body>
</html> <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fee Payment and Receipt Generation</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>Fee Payment Portal</h1>
        <p>Enter the fee details and make your payment. A receipt will be generated after the payment.</p>
    </header>

    <div class="container">
        <form id="paymentForm">
            <label for="studentId">Student ID:</label>
            <input type="text" id="studentId" name="studentId" required><br><br>

            <label for="feeAmount">Fee Amount (in $):</label>
            <input type="number" id="feeAmount" name="feeAmount" required><br><br>

            <label for="paymentMethod">Payment Method:</label>
            <select id="paymentMethod" name="paymentMethod" required>
                <option value="credit-card">Credit Card</option>
                <option value="paypal">PayPal</option>
                <option value="bank-transfer">Bank Transfer</option>
            </select><br><br>

            <button type="submit">Make Payment</button>
        </form>

        <!-- Receipt Section (Hidden by default) -->
        <div id="receiptSection" class="hidden">
            <h2>Payment Receipt</h2>
            <p><strong>Student ID:</strong> <span id="receiptStudentId"></span></p>
            <p><strong>Fee Amount:</strong> $<span id="receiptAmount"></span></p>
            <p><strong>Payment Method:</strong> <span id="receiptPaymentMethod"></span></p>
            <p><strong>Status:</strong> <span id="paymentStatus">Paid</span></p>
            <button id="downloadReceipt">Download Receipt</button>
        </div>
    </div>

    <footer>
        <p>&copy; 2025 Fee Payment Portal</p>
    </footer>

    <script>
        // Handle form submission
        document.getElementById('paymentForm').addEventListener('submit', function(event) {
            event.preventDefault(); // Prevent default form submission

            // Retrieve form values
            const studentId = document.getElementById('studentId').value;
            const feeAmount = document.getElementById('feeAmount').value;
            const paymentMethod = document.getElementById('paymentMethod').value;

            // Display receipt section
            document.getElementById('receiptStudentId').textContent = studentId;
            document.getElementById('receiptAmount').textContent = feeAmount;
            document.getElementById('receiptPaymentMethod').textContent = paymentMethod;

            document.getElementById('paymentForm').reset(); // Reset the form

            // Show the receipt section and status message
            document.getElementById('receiptSection').classList.remove('hidden');

            // Optional: Handle receipt download action
            document.getElementById('downloadReceipt').addEventListener('click', function() {
                const receiptContent = `Receipt\n\nStudent ID: ${studentId}\nFee Amount: $${feeAmount}\nPayment Method: ${paymentMethod}\nStatus: Paid`;
                const blob = new Blob([receiptContent], { type: 'text/plain' });
                const link = document.createElement('a');
                link.href = URL.createObjectURL(blob);
                link.download = 'fee_receipt.txt';
                link.click();
            });
        });
    </script>
</body>
</html><!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Admission Portal - Transparent Process</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>Welcome to the Admission Portal</h1>
        <p>Your guide to the admission process, fee structure, and status updates.</p>
    </header>

    <div class="container">
        <section id="admission-process">
            <h2>Admission Process</h2>
            <p>Follow these steps to apply for admission:</p>
            <ol>
                <li><strong>Step 1:</strong> Fill out the online application form.</li>
                <li><strong>Step 2:</strong> Upload required documents (ID, certificates, etc.).</li>
                <li><strong>Step 3:</strong> Pay the application fee.</li>
                <li><strong>Step 4:</strong> Wait for application review and status update.</li>
                <li><strong>Step 5:</strong> Receive admission decision and instructions.</li>
            </ol>
        </section>

        <section id="fee-structure">
            <h2>Fee Structure</h2>
            <table>
                <thead>
                    <tr>
                        <th>Course</th>
                        <th>Tuition Fee (per year)</th>
                        <th>Other Fees</th>
                        <th>Total Fee</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Computer Science</td>
                        <td>$10,000</td>
                        <td>$500</td>
                        <td>$10,500</td>
                    </tr>
                    <tr>
                        <td>Business Administration</td>
                        <td>$9,000</td>
                        <td>$500</td>
                        <td>$9,500</td>
                    </tr>
                    <tr>
                        <td>Medicine</td>
                        <td>$15,000</td>
                        <td>$500</td>
                        <td>$15,500</td>
                    </tr>
                    <tr>
                        <td>Law</td>
                        <td>$8,000</td>
                        <td>$500</td>
                        <td>$8,500</td>
                    </tr>
                </tbody>
            </table>
        </section>

        <section id="status-updates">
            <h2>Application Status</h2>
            <p>Check the status of your application:</p>
            <form>
                <label for="applicant-id">Enter Your Application ID:</label>
                <input type="text" id="applicant-id" name="applicant-id" required>
                <button type="submit">Check Status</button>
            </form>
            <div id="status-message" class="hidden">
                <p>Status: <strong id="status">Pending</strong></p>
                <p>Next Step: <span id="next-step">Awaiting review</span></p>
            </div>
        </section>
    </div>

    <footer>
        <p>&copy; 2025 University Admission Portal. All Rights Reserved.</p>
    </footer>

    <script>
        // Simple status check simulation
        document.querySelector('form').addEventListener('submit', function(event) {
            event.preventDefault();

            const applicantId = document.getElementById('applicant-id').value;

            // Mocked status check based on the application ID
            if (applicantId === '12345') {
                document.getElementById('status').textContent = 'Accepted';
                document.getElementById('next-step').textContent = 'Prepare for admission interview';
            } else if (applicantId === '67890') {
                document.getElementById('status').textContent = 'Rejected';
                document.getElementById('next-step').textContent = 'Try again next year';
            } else {
                document.getElementById('status').textContent = 'Pending';
                document.getElementById('next-step').textContent = 'Awaiting review';
            }

            document.getElementById('status-message').classList.remove('hidden');
        });
    </script>
</body>
</html><!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Student Management Portal</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>Student Management Portal</h1>
        <p>Manage Scholarships, Grievances, Performance, and Payments in One Place</p>
    </header>

    <div class="container">
        <!-- Section: Scholarships -->
        <section id="scholarships">
            <h2>Scholarship Management</h2>
            <p>Apply for scholarships, track status, and view available scholarships.</p>
            <button class="action-btn">Apply for Scholarship</button>
            <button class="action-btn">View Available Scholarships</button>
        </section>

        <!-- Section: Grievances -->
        <section id="grievances">
            <h2>Grievance Handling</h2>
            <p>Submit your grievances and track their resolution.</p>
            <button class="action-btn">File a Grievance</button>
            <button class="action-btn">Track Grievance Status</button>
        </section>

        <!-- Section: Student Performance -->
        <section id="performance">
            <h2>Track Student Performance</h2>
            <p>Monitor your academic progress and grades.</p>
            <button class="action-btn">View Academic Performance</button>
            <button class="action-btn">Request Transcript</button>
        </section>

        <!-- Section: Payment Wallet -->
        <section id="payment-wallet">
            <h2>Payment Wallet</h2>
            <p>Manage your payments for activities like fines, late fees, journals, and ATKT forms.</p>
            <div class="wallet-info">
                <p><strong>Available Balance:</strong> $<span id="wallet-balance">50.00</span></p>
                <button class="action-btn" onclick="addFunds()">Add Funds</button>
            </div>
            <h3>Transactions</h3>
            <table>
                <thead>
                    <tr>
                        <th>Date</th>
                        <th>Activity</th>
                        <th>Amount</th>
                        <th>Status</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>2025-01-06</td>
                        <td>Fine</td>
                        <td>$10.00</td>
                        <td>Paid</td>
                    </tr>
                    <tr>
                        <td>2025-01-06</td>
                        <td>Late Fee</td>
                        <td>$5.00</td>
                        <td>Paid</td>
                    </tr>
                    <tr>
                        <td>2025-01-07</td>
                        <td>ATKT Form</td>
                        <td>$15.00</td>
                        <td>Pending</td>
                    </tr>
                </tbody>
            </table>
        </section>
    </div>

    <footer>
        <p>&copy; 2025 University Student Management Portal. All Rights Reserved.</p>
    </footer>
    <div class="social-icons">
            <a href="https://twitter.com" target="_blank" title="Twitter"><i class="fab fa-twitter"></i></a>
            <a href="https://instagram.com" target="_blank" title="Instagram"><i class="fab fa-instagram"></i></a>
            <a href="https://whatsapp.com" target="_blank" title="WhatsApp"><i class="fab fa-whatsapp"></i></a>
            <a href="https://facebook.com" target="_blank" title="Facebook"><i class="fab fa-facebook"></i></a>
        </div>
    <script>
        // Function to add funds to the wallet (simulated)
        function addFunds() {
            let currentBalance = parseFloat(document.getElementById('wallet-balance').innerText);
            let newBalance = currentBalance + 20; // Simulate adding $20
            document.getElementById('wallet-balance').innerText = newBalance.toFixed(2);
            alert('Funds added successfully!');
        }
    </script>
</body>
</html>

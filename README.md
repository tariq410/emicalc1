<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Advanced EMI Calculator with Amortization Schedule | Accurate Loan Calculations | Financial Planning Tool">
    <meta name="keywords" content="EMI calculator, loan calculator, amortization schedule, financial planning, debt management">
    <meta name="author" content="Financial Tools Pro">
    <title>Professional EMI Calculator with Payment Breakdown</title>
    <link rel="canonical" href="https://www.yourdomain.com/emi-calculator">
    
    <!-- Google AdSense -->
    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-XXXXXXXXXXXXXXXX" crossorigin="anonymous"></script>

    <style>
        :root {
            --primary: #4361ee;
            --secondary: #3f37c9;
            --success: #4cc9f0;
            --danger: #f72585;
            --light: #f8f9fa;
            --dark: #212529;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', system-ui, sans-serif;
        }

        body {
            line-height: 1.6;
            color: var(--dark);
            background: #f1f3f5;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }

        .calculator-card {
            background: white;
            padding: 2rem;
            border-radius: 1rem;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            margin: 2rem 0;
        }

        .input-group {
            margin-bottom: 1.5rem;
        }

        .input-label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: var(--dark);
        }

        .input-field {
            width: 100%;
            padding: 0.8rem;
            border: 2px solid #dee2e6;
            border-radius: 0.5rem;
            font-size: 1rem;
            transition: border-color 0.3s;
        }

        .input-field:focus {
            border-color: var(--primary);
            outline: none;
        }

        .range-slider {
            width: 100%;
            margin: 1rem 0;
        }

        .calculate-btn {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            border: none;
            padding: 1rem 2rem;
            border-radius: 0.5rem;
            cursor: pointer;
            font-size: 1rem;
            width: 100%;
            transition: transform 0.2s;
        }

        .calculate-btn:hover {
            transform: scale(1.02);
        }

        .result-card {
            background: white;
            padding: 2rem;
            border-radius: 1rem;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            margin-top: 2rem;
            animation: fadeIn 0.5s;
        }

        .summary-cards {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 1rem;
            margin: 2rem 0;
        }

        .summary-card {
            padding: 1.5rem;
            border-radius: 0.5rem;
            text-align: center;
            background: var(--light);
        }

        .amortization-table {
            overflow-x: auto;
            margin: 2rem 0;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            background: white;
        }

        th, td {
            padding: 1rem;
            text-align: center;
            border-bottom: 1px solid #dee2e6;
        }

        th {
            background: var(--primary);
            color: white;
        }

        .pie-chart {
            width: 200px;
            height: 200px;
            border-radius: 50%;
            margin: 1rem auto;
            background: conic-gradient(
                var(--success) 0% var(--principal-percent),
                var(--danger) var(--principal-percent) 100%
            );
        }

        @media (max-width: 768px) {
            .container {
                padding: 1rem;
            }

            .summary-cards {
                grid-template-columns: 1fr;
            }
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header Ad -->
        <div class="calculator-card">
            <ins class="adsbygoogle"
                 style="display:block"
                 data-ad-client="ca-pub-XXXXXXXXXXXXXXXX"
                 data-ad-slot="1234567890"
                 data-ad-format="auto"
                 data-full-width-responsive="true"></ins>
            <script>
                 (adsbygoogle = window.adsbygoogle || []).push({});
            </script>
        </div>

        <div class="calculator-card">
            <h1>EMI Calculator</h1>
            <p>Calculate your monthly loan payments with detailed breakdown</p>

            <div class="input-group">
                <label class="input-label">Loan Amount (₹)</label>
                <input type="number" id="loanAmount" class="input-field" placeholder="100000" min="0">
                <input type="range" class="range-slider" min="0" max="10000000" step="1000">
            </div>

            <div class="input-group">
                <label class="input-label">Annual Interest Rate (%)</label>
                <input type="number" id="interestRate" class="input-field" placeholder="8.5" step="0.1" min="0" max="30">
                <input type="range" class="range-slider" min="0" max="30" step="0.1">
            </div>

            <div class="input-group">
                <label class="input-label">Loan Tenure (Years)</label>
                <input type="number" id="loanTenure" class="input-field" placeholder="5" min="1" max="30">
                <input type="range" class="range-slider" min="1" max="30" step="1">
            </div>

            <button class="calculate-btn" onclick="calculateEMI()">Calculate EMI</button>
        </div>

        <!-- Live Preview -->
        <div class="calculator-card">
            <div class="summary-cards">
                <div class="summary-card">
                    <div style="color: var(--primary); font-size: 1.5rem;">₹<span id="previewEMI">0.00</span></div>
                    <p>Monthly Payment</p>
                </div>
                <div class="summary-card">
                    <div style="color: var(--danger); font-size: 1.5rem;">₹<span id="previewInterest">0.00</span></div>
                    <p>Total Interest</p>
                </div>
                <div class="summary-card">
                    <div style="color: var(--success); font-size: 1.5rem;">₹<span id="previewTotal">0.00</span></div>
                    <p>Total Payment</p>
                </div>
            </div>
        </div>

        <!-- Results Section -->
        <div class="result-card" id="result">
            <h2>Payment Breakdown</h2>
            <div class="pie-chart" style="--principal-percent: 50%"></div>

            <div class="amortization-table">
                <table>
                    <thead>
                        <tr>
                            <th>Month</th>
                            <th>Principal</th>
                            <th>Interest</th>
                            <th>Balance</th>
                        </tr>
                    </thead>
                    <tbody id="amortizationBody"></tbody>
                </table>
            </div>
        </div>

        <!-- Mid Content Ad -->
        <div class="calculator-card">
            <ins class="adsbygoogle"
                 style="display:block"
                 data-ad-format="fluid"
                 data-ad-layout-key="-gw-3+1f-3d+2z"
                 data-ad-client="ca-pub-XXXXXXXXXXXXXXXX"
                 data-ad-slot="0987654321"></ins>
            <script>
                 (adsbygoogle = window.adsbygoogle || []).push({});
            </script>
        </div>

        <!-- Feedback Section -->
        <div class="calculator-card">
            <h3>Your Feedback</h3>
            <form id="feedbackForm">
                <textarea class="input-field" placeholder="Share your suggestions..." required></textarea>
                <button class="calculate-btn" type="submit">Submit</button>
            </form>
        </div>
    </div>

    <script>
        // Precision calculation function
        const roundValue = (num) => Math.round(num * 100) / 100;

        function calculateEMI() {
            // Get input values
            const loanAmount = parseFloat(document.getElementById('loanAmount').value) || 0;
            const annualInterest = parseFloat(document.getElementById('interestRate').value) || 0;
            const years = parseFloat(document.getElementById('loanTenure').value) || 0;

            // Validate inputs
            if(!loanAmount || !annualInterest || !years) return;

            // Calculation parameters
            const monthlyInterestRate = annualInterest / 1200;
            const months = years * 12;
            const emi = calculateMonthlyEMI(loanAmount, monthlyInterestRate, months);

            // Amortization variables
            let balance = loanAmount;
            let totalInterest = 0;
            const amortizationData = [];

            // Calculate amortization schedule
            for(let month = 1; month <= months; month++) {
                const interest = roundValue(balance * monthlyInterestRate);
                const principal = roundValue(emi - interest);
                const actualPrincipal = Math.min(principal, balance);

                totalInterest = roundValue(totalInterest + interest);
                balance = roundValue(balance - actualPrincipal);

                // Last month adjustment
                if(month === months && balance > 0) {
                    balance = 0;
                }

                amortizationData.push({
                    month,
                    principal: actualPrincipal,
                    interest,
                    balance: Math.max(balance, 0)
                });
            }

            // Update UI
            updateResults(loanAmount, emi, totalInterest);
            updateAmortizationTable(amortizationData);
            updateCharts(loanAmount, totalInterest);
        }

        function calculateMonthlyEMI(P, r, n) {
            if(r === 0) return roundValue(P / n);
            const emi = (P * r * Math.pow(1 + r, n)) / (Math.pow(1 + r, n) - 1);
            return roundValue(emi);
        }

        function updateResults(principal, emi, totalInterest) {
            document.getElementById('previewEMI').textContent = emi.toFixed(2);
            document.getElementById('previewInterest').textContent = totalInterest.toFixed(2);
            document.getElementById('previewTotal').textContent = (principal + totalInterest).toFixed(2);
        }

        function updateAmortizationTable(data) {
            const tbody = document.getElementById('amortizationBody');
            tbody.innerHTML = data.map(item => `
                <tr>
                    <td>${item.month}</td>
                    <td style="color: var(--success);">₹${item.principal.toFixed(2)}</td>
                    <td style="color: var(--danger);">₹${item.interest.toFixed(2)}</td>
                    <td>₹${item.balance.toFixed(2)}</td>
                </tr>
            `).join('');
        }

        function updateCharts(principal, totalInterest) {
            const totalPayment = principal + totalInterest;
            const principalPercent = (principal / totalPayment * 100).toFixed(1);
            document.querySelector('.pie-chart').style.setProperty('--principal-percent', `${principalPercent}%`);
        }

        // Input synchronization
        document.querySelectorAll('.input-field').forEach(input => {
            input.addEventListener('input', function() {
                const slider = this.nextElementSibling;
                if(slider?.classList.contains('range-slider')) {
                    slider.value = this.value;
                    calculateEMI();
                }
            });
        });

        document.querySelectorAll('.range-slider').forEach(slider => {
            slider.addEventListener('input', function() {
                const inputField = this.previousElementSibling;
                if(inputField?.classList.contains('input-field')) {
                    inputField.value = this.value;
                    calculateEMI();
                }
            });
        });

        // Feedback handling
        document.getElementById('feedbackForm').addEventListener('submit', function(e) {
            e.preventDefault();
            alert('Thank you for your feedback!');
            this.reset();
        });

        // Initial calculation
        calculateEMI();
    </script>

    <!-- Structured Data -->
    <script type="application/ld+json">
    {
        "@context": "https://schema.org",
        "@type": "WebApplication",
        "name": "EMI Calculator",
        "description": "Advanced EMI calculator with amortization schedule and payment breakdown",
        "applicationCategory": "FinancialApplication",
        "operatingSystem": "All",
        "offers": {
            "@type": "Offer",
            "price": "0",
            "priceCurrency": "USD"
        }
    }
    </script>
</body>
</html>

# nraizada1.github.io

html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Income Tax Calculator</title>
</head>
<body>
    <h1>Income Tax Calculator</h1>
    <form id="taxForm">
        <label for="income">Enter your income:</label>
        <input type="number" id="income" name="income" required>
        <br><br>
        <label for="scheme">Choose tax scheme:</label>
        <select id="scheme" name="scheme" required>
            <option value="new">New Revised</option>
            <option value="old">New Scheme</option>
        </select>
        <br><br>
        <button type="button" onclick="calculateTax()">Calculate Tax</button>
    </form>
    <p id="result"></p>

    <script>
        function calculateTax() {
            let income = parseFloat(document.getElementById('income').value);
            income -= 75000; // Deduct 75000 from the income

            if (income < 0) {
                income = 0;
            }

            // Calculate tax for New Revised Scheme
            let newRevisedTax = calculateNewRevisedTax(income);

            // Calculate tax for Old Scheme
            let oldSchemeTax = calculateOldSchemeTax(income);

            // Determine which scheme has lower tax and calculate the difference
            let lowerTaxScheme;
            let difference;

            if (newRevisedTax < oldSchemeTax) {
                lowerTaxScheme = "New Revised";
                difference = oldSchemeTax - newRevisedTax;
            } else {
                lowerTaxScheme = "New Scheme";
                difference = newRevisedTax - oldSchemeTax;
            }

            // Display the results
            document.getElementById('result').innerText = `For an income of ₹${income.toFixed(2)}:\n` +
                `Tax under New Revised Scheme: ₹${newRevisedTax.toFixed(2)}\n` +
                `Tax under New Scheme: ₹${oldSchemeTax.toFixed(2)}\n` +
                `The lower tax scheme is: ${lowerTaxScheme}\n` +
                `Difference in tax: ₹${difference.toFixed(2)}`;
        }

        function calculateNewRevisedTax(income) {
            let tax = 0;
            if (income <= 300000) {
                tax = 0;
            } else if (income <= 700000) {
                tax = (income - 300000) * 0.05;
            } else if (income <= 1000000) {
                tax = (400000 * 0.05) + (income - 700000) * 0.10;
            } else if (income <= 1200000) {
                tax = (400000 * 0.05) + (300000 * 0.10) + (income - 1000000) * 0.15;
            } else if (income <= 1500000) {
                tax = (400000 * 0.05) + (300000 * 0.10) + (200000 * 0.15) + (income - 1200000) * 0.20;
            } else {
                tax = (400000 * 0.05) + (300000 * 0.10) + (200000 * 0.15) + (300000 * 0.20) + (income - 1500000) * 0.30;
            }
            return tax;
        }

        function calculateOldSchemeTax(income) {
            let tax = 0;
            if (income <= 250000) {
                tax = 0;
            } else if (income <= 500000) {
                tax = (income - 250000) * 0.05;
            } else if (income <= 750000) {
                tax = (250000 * 0.05) + (income - 500000) * 0.10;
            } else if (income <= 1000000) {
                tax = (250000 * 0.05) + (250000 * 0.10) + (income - 750000) * 0.15;
            } else if (income <= 1250000) {
                tax = (250000 * 0.05) + (250000 * 0.10) + (250000 * 0.15) + (income - 1000000) * 0.20;
            } else if (income <= 1500000) {
                tax = (250000 * 0.05) + (250000 * 0.10) + (250000 * 0.15) + (250000 * 0.20) + (income - 1250000) * 0.25;
            } else {
                tax = (250000 * 0.05) + (250000 * 0.10) + (250000 * 0.15) + (250000 * 0.20) + (250000 * 0.25) + (income - 1500000) * 0.30;
            }
            return tax;
        }
    </script>
</body>
</html>
```

### Explanation:
- **Deduction**: ₹75,000 is deducted from the entered income before tax calculation.


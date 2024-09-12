<script>
    let amount = 0;
    let fromCurrency = 'BTC';
    let toCurrency = 'USD';
    let prices = {};

    async function fetchPrices() {
        const response = await fetch('https://api.coincap.io/v2/rates');
        prices = await response.json();
    }

    function calculateConversion() {
        const fromPrice = prices[fromCurrency];
        const toPrice = prices[toCurrency];
        const conversionRate = toPrice / fromPrice;
        const result = amount * conversionRate;
        return result.toFixed(2);
    }

    fetchPrices();
</script>

<form>
    <label for="amount">Amount:</label>
    <input type="number" id="amount" bind:value={amount} />

    <label for="fromCurrency">From:</label>
    <select id="fromCurrency" bind:value={fromCurrency}>
        {#each Object.keys(prices) as currency}
            <option value={currency}>{currency}</option>
        {/each}
    </select>

    <label for="toCurrency">To:</label>
    <select id="toCurrency" bind:value={toCurrency}>
        {#each Object.keys(prices) as currency}
            <option value={currency}>{currency}</option>
        {/each}
    </select>

    <p>Result: {calculateConversion()}</p>
</form>
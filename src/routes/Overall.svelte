<script>
    async function getCovid() {
        let response = await fetch("https://disease.sh/v3/covid-19/all");
        let covidall = await response.json();
        return covidall;
    }
    const promise = getCovid();
</script>
<p class="toptext">the globe covid case be like:</p>
{#await promise}
    <p class="medium">freaking wait pls⌛</p>
{:then covidall}
    <p class="medium">the confirmed covid🦠 case is: {covidall.cases}</p>
    <p class="medium">today covid🦠 cases is: {covidall.todayCases}</p>
    <p class="medium">death💀 total is: {covidall.deaths}</p>
    <p class="medium">today death💀 cases is {covidall.todayDeaths}</p>
{:catch error}
    <p>error ❌ the error is {error}</p>
{/await}

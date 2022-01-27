<script>
    async function getCovid() {
        let response = await fetch("https://disease.sh/v3/covid-19/all");
        let covidall = await response.json();
        return covidall;
    }
    const promise = getCovid();
</script>

<main>
<h1 class="testing">
the globe covid case be like:
</h1>
{#await promise}
    <p>freaking wait pls⌛</p>
{:then covidall}
    <p>the confirmed covid🦠 case is: {covidall.cases}</p>
    <p>today covid🦠 cases is: {covidall.todayCases}</p>
    <p>death💀 total is: {covidall.deaths}</p>
    <p>today death💀 cases is {covidall.todayDeaths}</p>
{:catch error}
    <p>error ❌ the error is {error}</p>
{/await}
<h3>Write by Cephas with ❤ and time⏳</h3>
</main>

<style>
</style>

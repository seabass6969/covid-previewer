<style>
.toptext {
    font-size: 5vw;
    margin-top: 0%;
    margin-bottom:1%;
}
.medium {
    font-size: 2vw;
}
.credit {
    font-size: 3vw;
}
@media (max-width: 600px){
    .toptext{
        font-size: 10vw;
    }
    .medium{
        font-size: 8vw;
    }
    .credit {
        font-size: 6vw;
    }
}
</style>
<script>
    async function getCovid() {
        let response = await fetch("https://disease.sh/v3/covid-19/all");
        let covidall = await response.json();
        return covidall;
    }
    const promise = getCovid();
</script>
<main>
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
<h3 class="credit">Write by Cephas with ❤ and time⏳</h3>
</main>


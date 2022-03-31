<style>
.normalIMG {
width: 100px;
}
input {
    border-style: solid;
    border-color: #00b9ff;
    background-color: #00b9ff;
    width: 40vw;
    height: 5vw;
    display: block;
    font-size: 4vw;
    border-radius: 15px;
}
button {
    margin-top: 10px;
    border-style: solid;
    border-color: #00b9ff;
    font-size: 6vw;
    border-radius: 15px;
    display: block;
}
@media (min-width: 1000px){
    input {
        width: 45vw;
        height: 5vw;
        font-size: 4vw
    }
    button {
        font-size: 7vw
    }
}

@media (max-width: 600px){
    input {
        width: 70vw;
        height: 10vw;
        font-size: 8vw
    }
    button{
        font-size: 8vw
    }
}
</style>
<script>
    let country_data = {
        result: undefined,
        country_name: undefined,
        successful: false,
        done: false
    }
    async function onClick_country(){
        if(country_data.country_name === undefined){
        country_data.done = false 
        country_data.successful = false
        }else{
        console.log(country_data)
        let res = await fetch("https://disease.sh/v3/covid-19/countries/"+country_data.country_name)
        country_data.result = await res.json()
        if(country_data.result.message !== undefined){
            country_data.done = false 
            country_data.successful = false 
        } else {
        country_data.done = true 
        country_data.successful = true 
        console.log(country_data)
        }    
    }
    }
</script>
<p class="medium">search by country: </p>
<input type="text" bind:value={country_data.country_name}>
<button on:click={onClick_country}>search</button>
{#if country_data.done === true}
{#if country_data.successful === true}
<p class="medium"><img src={country_data.result.countryInfo.flag} class="normalIMG" alt=""><br>covid: </p>
<p class="medium">😨Cases:</p>
<p class="medium">Total Cases: {country_data.result.cases}</p>
<p class="medium">Active Cases: {country_data.result.active}</p>
<p class="medium">Today Cases: {country_data.result.todayCases}</p>

<p class="medium">💀Deaths:</p>
<p class="medium">Total deaths: {country_data.result.deaths}</p>
<p class="medium">Today deaths: {country_data.result.todayDeaths}</p>
<p class="medium">🏥hospital:</p>
<p class="medium">Total Recovered: {country_data.result.deaths}</p>
<p class="medium">Today Recovered: {country_data.result.todayRecovered}</p>
{:else}
<p class="medium">ERROR Country or no case </p>
{/if}

{/if}

<style >
</style>
<script>
    import Router from 'svelte-spa-router'
    import Overall from './routes/Overall.svelte'
    import Bycountry from './routes/Bycountry.svelte'
    import error from './routes/error.svelte'
    const routes = {
        '/': Overall,
        '/bycountry': Bycountry,
        '*': error
    }
</script>
<main>
<div class="header">
<a class="link" href="/#/">overall</a>
<a class="link" href="/#/bycountry">country</a>
</div>
<Router routes={routes}/>
<h3 class="credit">Write by Cephas with ❤ and time⏳</h3>
<h3 class="credit">Disclaimer not all data are correct. </h3>
</main>


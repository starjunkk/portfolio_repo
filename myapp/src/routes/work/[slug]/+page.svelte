<script>
    import { onMount } from 'svelte';
    import { supabase } from '../../supabaseClient.js';

    export let data;
    let loading = true;
    let error;
    let work;

    // Su supabase, crea prima la colonna slug e dai un nome unico, poi salva, solo dopo editala e dai Is Unique

    onMount(() => {
        console.log('data', data);
        supabase.from('works').select().eq('slug',data.slug).single().then((e) => {
            loading = false;
            error = e.error;
            work = e.data})

    });
</script>


    {#if loading}
    <p>Loading...</p>
    {:else if error}
    <p>{error.message}</p>
    {:else}
    <h1>{work.title}</h1>
    <p>{work.description}</p>

    {#if work.checkout_link}
    <h2>Want the same result? Subscribe</h2>
    <a href={work.checkout_link}></a>
    {/if}
{/if}

<a href="https://billing.stripe.com/p/login/test_6oE00J1zk2Nw6ukbII">Gestisci il tuo account</a>

<!-- Da Stripe, scrivendo Branding nella barra di ricerca, posso customizzare la UI dei pagamenti etc. -->
<!-- Se vuoi cambiare pagamento, personalizzandolo per ogni prodotto magari, crea sempre un nuovo pacchetto su Stripe e cambia il link su Supabase per ogni slug diverso. -->

<!-- Per ogni pagina, tieni in conto che ci sono come minimo tre stati. Caricamento, Caricata, Errore. -->

<style></style>
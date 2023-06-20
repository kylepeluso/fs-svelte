<script>
    /*
    Simple button to trigger the loading of the ads
    */
    export let adQueue;
    const loadAds = () => {
        freestar.queue.push(function () {
            freestar.newAdSlots(adQueue);
            adQueue = [];
        });
    }
</script>

<button on:click={loadAds} disabled={adQueue.length===0}>
    Trigger Ad Load
</button>

<style>
    button {
        padding: .5em;
    }
</style>
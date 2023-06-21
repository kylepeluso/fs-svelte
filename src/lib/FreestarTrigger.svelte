<script>
  /*
    Simple button to trigger the loading of the ads
    */
  export let adQueue;
  const loadAds = () => {
    // @ts-ignore
    freestar.queue.push(function () {
      // @ts-ignore
      freestar.newAdSlots(adQueue);
      adQueue = [];
    });
  };
</script>

<button on:click={loadAds} disabled={adQueue.length === 0}>
  Trigger Ad Load
</button>

<style>
  button {
    padding: 0.5em;
  }
</style>

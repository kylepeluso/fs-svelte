<script>
    /*
    Ad slot component to handle the creation of the div and adding the
    placement into an ad queue array to have the ad triggered at a later time
    */
    export let placementName, slotId, adQueue;
    window.freestar = freestar || {};
    window.freestar.queue = freestar.queue || [];
    window.freestar.config = freestar.config || {};
    adQueue.push({
        placementName: placementName,
        slotId: slotId,
    });
</script>

<div class="ad-slot">
    <div class="label">Placement: {placementName} - slotId: {slotId}</div>
    <div id={slotId}></div>
</div>

<style>
    .label {
        font-style: italic;
        font-size: 80%;
        text-align: center;
    }
</style>
<script>
    import FreestarHead from './lib/FreestarHead.svelte';
    import FreestarScript from './lib/FreestarScript.svelte';
    import FreestarTrigger from './lib/FreestarTrigger.svelte';
    import AdSlot from './lib/AdSlot.svelte';
    const freestarData = {
        channel: '/4735792/reuters.com/home', //defining the ad unit path for all ads on the page
        adQueue: [], //creating a queue to control ad load
        pageTargeting: { //defining the key-value pair targeting for all ads on the page
            articleId: '11235', //proper syntax for a single key-value pair, values must be a string
            key2: ['multivalue1',
                'multivalue2'
            ] //proper syntax for a multiple values for a single key, value must be an array of strings
        }
    }
</script>

<main>
    <div class="debug-info">
        <div>Channel: {freestarData.channel}</div>
        <div>Page-level targeting: {JSON.stringify(freestarData.pageTargeting,null,2)}</div>
        <div>Ads to load: {freestarData.adQueue.length}</div>
        <div class="ad-list">{JSON.stringify(freestarData.adQueue,null,2)}</div>
    </div>

    <FreestarScript />

    <FreestarHead freestarData={freestarData} />

    <FreestarTrigger bind:adQueue={freestarData.adQueue} />

    <AdSlot placementName='reuters_desktop_leaderboard_atf' slotId='reuters_desktop_leaderboard_atf'
        bind:adQueue={freestarData.adQueue} />

    <AdSlot placementName='reuters_desktop_right_rail_1' slotId='ad2' bind:adQueue={freestarData.adQueue} />

    <AdSlot placementName='reuters_desktop_native_1' slotId='reuters_desktop_native_1'
        bind:adQueue={freestarData.adQueue} />
</main>

<style>
    main {
        width: 900px;
        max-width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 2em;
    }

    .debug-info {
        background-color: black;
        width: 100%;
        display: grid;
        grid-template-columns: 1fr 1.5fr 1fr;
        gap: 1px;
        border: 1px solid black;
    }

    .ad-list {
        grid-column-start: span 3;
    }

    .debug-info>div {
        padding: .5em;
        background-color: white;
    }
</style>
<script>
  import { beforeUpdate } from "svelte";
  import FreestarHead from "./FreestarHead.svelte";
  /*
  Ad slot component to handle the creation of the div and adding the
  placement into an ad queue array to have the ad triggered at a later time
  */
  export let placementName,
    adQueue,
    slotId = placementName,
    targeting = {};
  beforeUpdate(() => {
    targeting = targeting || {};
    slotId = slotId || placementName;
  });
  const placementCode =
    Object.keys(targeting).length > 0
      ? {
          placementName: placementName,
          slotId: slotId,
          targeting: targeting,
        }
      : {
          placementName: placementName,
          slotId: slotId,
        };
  adQueue.push(placementCode);
</script>

<div class="ad-slot">
  <div class="label">Placement: {placementName} - slotId: {slotId}</div>
  <div id={slotId} />
</div>

<style>
  .label {
    font-style: italic;
    font-size: 80%;
    text-align: center;
  }
</style>

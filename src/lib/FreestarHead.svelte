<script data-cfasync="false" type="text/javascript">
    /*
    Head code component to handle the definition of Freestar and its config.
    The ad unit path (channel) is defined here as well as any page level targeting
    */
    export let channel, pageTargeting;
    window.freestar = window.freestar || {};
    window.freestar.queue = window.freestar.queue || [];
    window.freestar.config = window.freestar.config || {};
    window.freestar.config.enabled_slots = [];
    window.freestar.config.channel = channel;
    for (const [key, value] of Object.entries(pageTargeting)) {
        window.freestar.queue.push(function () {
            googletag.pubads().setTargeting(key, value);
        })
    }
    window.freestar.queue.push(function () {
        googletag.pubads().set('page_url',
            'https://www.reuters.com/'); //This line should only be used for testing

    });
</script>
<script>
    import {onMount} from "svelte";
    let {children, callback, options} = $props();

    let uniqueId = Math.random().toString(36).slice(2, 8);

    onMount(() =>{
        let intersectionObserver = new IntersectionObserver(callback, options);

        const element = document.getElementById(uniqueId);
        intersectionObserver.observe(element);
    })
</script>

<div id={uniqueId} class="text">
    {@render children()}
</div>

<style>
    .text {
        /* margin: 50vh auto; */
        width: 100%;
        color: #df783d;
        /* text-align: left; */
        /* padding-left: 5%; */
        font-size: 6.5vh;
        font-family: fantasy;
        /* text-shadow: 2px 2px 1px #FA9500; */
    }
</style>
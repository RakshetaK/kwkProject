<script>
    import CountUp from "svelte-countup";

    let {value} = $props();

</script>

<div class="count-wrapper">
    <CountUp value={value} />
</div>

<style>
    .count-wrapper{
        font-family: fantasy;
        margin: 0;
        font-size: 5vw;
    }
</style>
<script>
    let {children} = $props();
</script>

<div class="article-text">
    <p>
        {@render children()}
    </p>

</div>

<style>
    .article-text{
        color: #EB6424;
        font-size: 2.5vw;
        font-family: fantasy;
        align-items: center;
        padding-left: 7rem;
        padding-right: 7rem;
        position: relative;
        z-index: 1;
    }
</style>
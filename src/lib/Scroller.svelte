
<script>
    //IMPORTANT: Jasmine Samra's Code!!!


    // `layout` can be either "right" or "left"
    // `sticky` and `scrolly` are the snippets passed in (see one of the examples)
    let { layout, sticky, scrolly, keepSticky = false } = $props(); 
</script>

<div class="wrapper {layout}">
    {#if keepSticky}
    <div class="sticky">
        {@render sticky()}
    </div>
    {/if}
    <div class="scrolly">
        {@render scrolly()}
    </div>
</div>

<style>
    .wrapper {
        padding: min(100vh, 30rem) 1rem;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        align-items: flex-start;
        width: 98%;
    }

    .left .scrolly {
        order: 0;
    }
    .left .sticky {
        order: 1;
    }

    .right .scrolly {
        order: 1;
    }
    .right .sticky {
        order: 0;
    }

    .sticky,
    .scrolly {
        display: flex;
        flex-direction: column;
        flex: 1 1; /* Allows growing, shrinking */
    }

    .sticky {
        position: sticky;
        top: 50vh;
        transform: translateY(-50%);
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 0;
    }
    .sticky:empty {
        display: none;
    }
    .scrolly {
        z-index: 1;
        overflow: visible;
    }

    @media (max-width: 768px) {
        .wrapper {
            flex-direction: column;
            padding: 2rem 1rem;
            
        }

        .sticky,
        .scrolly {
            flex: 1 1 auto;
            min-width: 100%;
            position: static; /* remove sticky on mobile */
            transform: none;
        }

        .sticky {
            margin-bottom: 2rem;
        }
    }
</style>

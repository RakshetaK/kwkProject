<script>
    import ObservedText from "./ObservedText.svelte";
    import {fade} from "svelte/transition";
    
    import Scroller from "./Scroller.svelte";
    
    let {url="", children, alignment=false} = $props();
    
    let willShow = $state(false);
    
   
    const options = {
        threshold: 0.0
    }
    const callback = (entries, observer) => {
        entries.forEach((entry) => {
            const elem = entry.target;
            // console.log(`[${entry.target.dataset.id}] isIntersecting:`, entry.isIntersecting);
            if(entry.intersectionRatio > 0){
                willShow = true;
            }else{
                willShow = false;
            }
            
            
        });
    };
</script>



<div class = "wrapper">
    {#if willShow}
        <div class="bg" in:fade={{ duration: 800}} out:fade={{ duration: 800, delay: 2000 }} style={`background-image: url('${url}'); right: ${alignment? "0%":"27%"}` }></div>
    {/if}
    <Scroller layout="left" keepSticky={false}>
        {#snippet sticky()}
           <!-- Empty here since we don't need sticky  -->
        {/snippet}

        {#snippet scrolly()}
           <div class="text-wrapper" style={`width: ${alignment? "50%":"100%"}; margin-left: ${alignment? "5%":"0%"}` }>
            <ObservedText {callback} {options}>
                {@render children()}
            </ObservedText>
            </div>
            
        {/snippet}
    </Scroller>
</div>



<style>
    
     .wrapper{
        width: 100%;
        height: 100%;
        z-index: 0;
        
    }
    .bg{
        top:15px;
        position: fixed;
        aspect-ratio: 6/5;
        z-index: 0;
        right: 0;
        background-size: cover;
        background-repeat: no-repeat;
        display: flex;
        width: auto;
        height: 100%; 
        
    }
    .text-wrapper {
        z-index: 2;
        height: 100%;
        /* width: 100%; */
        background: transparent;
        position: relative;
        display: flex;
        align-items: center;
        justify-content: center;
        text-align: center;
        /* margin-left: 5%; */
        /* border: 2px solid white; */
    }
        
    

    

   
</style>
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
            if(entry.intersectionRatio > 0||window.innerWidth<=768){
                willShow = true;
                
                if(window.innerWidth<=768){
        alignment = false;
    }
            }else{
                willShow = false;
            }
            
            
        });
    };
   
</script>



<div class = "wrapper">
    {#if willShow}
        <div class="bg" class:two={!alignment} in:fade={{ duration: 800}} out:fade={{ duration: 800, delay: 1000 }} style={`background-image: url('${url}'); `}></div>
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
        height: auto;
        z-index: 0;
        
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
    .bg{
        top:15px;
        position: fixed;
        aspect-ratio: 6/5;
        z-index: 0;
        right: 16px;
        background-size: cover;
        background-repeat: no-repeat;
        display: flex;
        width: auto;
        height: 100%;
    }
    .bg.two{
        top:0px;
        position: fixed;
        aspect-ratio: 6/5;
        z-index: 0;
        left: 50%;
        transform: translateX(-50%);
        background-size: cover;
        background-repeat: no-repeat;
        background-position: center;
        display: flex;
        width: auto;
        height: 100%;
    } 
    
    @media (max-width: 768px) {
        
        .wrapper{
            display: flex;
            flex-direction: column;
            /* height: 100vh; */
            /* min-height: 80vh; */
            /* height:140vh; */
            overflow: visible;
            width: 100%;
            /* border: 2px solid white; */
        }
        .bg{
            /* transform: translateY(30vh); */
            position: static;
            transition: none;
            /* right: 16px; */
            z-index: 0;
            
            width: 100%;
           
            /* margin-top: 30vh; */
            /* border: 2px solid blue; */
            /* transform: translateY(30vh); */
            
            
        }
        .bg.two{
            /* top: 80vh; */
            aspect-ratio: 2.8/1;
            position: relative;
            transition: none;
            height: 40%;
            width: auto;
            /* border: 8px solid #98830c; */
        }
        
        .text-wrapper{
            top:0;
            /* transform: translateY(-20vh); */
            left: 0;
            /* padding: 2rem; */
            width: 80vw;
        }
    }
    

   
</style>
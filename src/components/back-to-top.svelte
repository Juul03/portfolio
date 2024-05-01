<script>
    import { onMount } from 'svelte';

    const scrollToTop = () => {
            window.scrollTo({
                top:0,
                behavior: 'smooth'
            })
        }

</script>

<a id="back-to-top" on:click={scrollToTop}>
    <img src="/img/icons/back-to-top-icon.svg" alt="Back to top">
</a>

<style lang="scss">
    #back-to-top {
        position:fixed;
        bottom:1rem;
        right:1rem;

        z-index:100;
        
        width:2rem;
        height:2rem;

        img {
            width:100%;
            height:100%;
            
            transition:var(--standard-transition-time);

            &:hover {
                transform:scale(1.2);

                cursor:pointer;
            }
        }
    }

</style>

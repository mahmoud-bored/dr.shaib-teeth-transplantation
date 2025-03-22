<script lang="ts">

    import CollapseCard from "./CollapseCard.svelte";
    
    let { isCurrentLangAr }: { isCurrentLangAr: boolean } = $props()
    
    let cardContainerMaxHeight = $state(420)
    let cardContainerHeight: number = $state(0)
    let cardContainer: HTMLElement | undefined = $state()
    let numberOfCards = $state(0)
    let isCardsListOpen = $state(false)
    $effect(() => {
        if(cardContainer) {
            numberOfCards = cardContainer.children.length
        }
    })
</script>
<div 
    class="relative w-8/10 max-w-[1000px] overflow-hidden transition-all duration-300"
    style="max-height: {isCardsListOpen ? cardContainerHeight : cardContainerMaxHeight }px"
>
    <div 
        class={[
            "w-full",
            "flex",
            "justify-center",
            "items-center",
            "gap-4",
            "flex-wrap",
            "flex-col",
            "md:flex-row",
            "transition-all",
            "duration-75",
            isCardsListOpen ? "pb-14" : "pb-0",
            "mb-3"
        ]} 
        bind:offsetHeight={cardContainerHeight} 
        bind:this={cardContainer}
    >
        <CollapseCard {isCurrentLangAr} >
            {#snippet title()}
                <span>
                    {
                        isCurrentLangAr ?
                            "هل الزراعة مؤلمة؟" : 
                            "Lorem Ipsum?"
                    }
                </span>
            {/snippet}
            {#snippet content()}
                <p>لا، الإجراء يتم تحت تخدير موضعي ولا تشعر بأي ألم أثناء الزراعة.</p>
            {/snippet}
        </CollapseCard>
        
        <CollapseCard {isCurrentLangAr} >
            {#snippet title()}
                <span>
                    {
                        isCurrentLangAr ?
                            "كم تستغرق الزراعة؟" : 
                            "What are the stages of the training program?"
                    }
                </span>
            {/snippet}
            {#snippet content()}
                <p>من 20 إلى 40 دقيقة فقط، والمتابعة خلال 2–3 أشهر حتى التركيب النهائي.</p>
            {/snippet}
        </CollapseCard>
        <CollapseCard {isCurrentLangAr} >
            {#snippet title()}
                <span>
                    {
                        isCurrentLangAr ?
                            "هل في تقسيط؟" : 
                            "What are the stages of the training program?"
                    }
                </span>
            {/snippet}
            {#snippet content()}
                <p>نعم، لدينا أنظمة تقسيط مرنة بدون فوائد.</p>
            {/snippet}
        </CollapseCard>
        <CollapseCard {isCurrentLangAr} >
            {#snippet title()}
                <span>
                    {
                        isCurrentLangAr ?
                            "هل في ضمان؟" : 
                            "What are the stages of the training program?"
                    }
                </span>
            {/snippet}
            {#snippet content()}
                <p>نعم، نقدم ضمانات حقيقية على الزرعات الألمانية والكورية.</p>
            {/snippet}
        </CollapseCard>
    </div>
    <!-- <div class="w-full h-12 bg-linear-0 from-white via-white to-white/0 flex justify-center items-center absolute bottom-0">
        <button
            class="text-[#0000EE] hover:text-[#FF0000] cursor-pointer p-2 transition duration-100"
            onclick={() => isCardsListOpen = !isCardsListOpen}
        >
            { 
                isCardsListOpen ?
                    isCurrentLangAr ? "إظهار أقل" : "Show less"
                    : isCurrentLangAr ? "إظهار المزيد" : "Show more" 
            }
        </button>
    </div> -->
</div>
<script>
    import Scroller from "../lib/Scroller.svelte";
    import ObservedArticleText from "../lib/ObservedArticleText.svelte";

    // this `options` object below is passed into the <ObservedArticleText>
    // component, and from there it gets passed to the IntersectionObserver object w
    // when it's created.
    // the thresholds to fire the callback are 85% and 95%. in the callback function,
    // we check whether the visible area is >= 90%. so, triggering the callback at
    // 85% and 95% ensures we trigger the correct change in background color
    // whether the element is being scrolled into the viewport or out of the viewport.
    const options = {
        threshold: [0.85, 0.95],
    };

    const callback = (entries, observer) => {
        entries.forEach((entry) => {
            const elem = entry.target;

            if (entry.intersectionRatio >= 0.9) {
                // "active" state
                elem.style.backgroundColor = "#e3ff00";
            } else if (entry.intersectionRatio < 0.9) {
                // "inactive" state
                elem.style.backgroundColor = "#888888";
            }
        });
    };
</script>

<div>
    <Scroller layout="left">
        {#snippet sticky()}
            <div>
                <p>
                    To tackle socioeconomic barriers that disadvantage some racial groups, preferential selection and providing additional consideration for marginalized groups is a helpful way to reduce inequalities and expand educational and employment opportunities.
                </p>
            </div>
        {/snippet}

        {#snippet scrolly()}
            <ObservedArticleText {callback} {options}>
                <code>{"Different racial groups experience varied life circumstances"}</code> 
            </ObservedArticleText>

            <ObservedArticleText {callback} {options}>
                <code>{"Affirmative action ensures that low-income, minority individuals are considered preferentially during university admissions"}</code> 
            </ObservedArticleText>

            <ObservedArticleText {callback} {options}>
                <code>{"Ignoring racial backgrounds during university admissions could risk the continual exclusion of minority groups from educational opportunities."}</code> 
            </ObservedArticleText>
        {/snippet}
    </Scroller>
</div>

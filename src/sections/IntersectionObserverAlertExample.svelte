<script>
    import "highcharts/modules/exporting";
    import Scroller from "../lib/Scroller.svelte";
    import ObservedArticleText from "../lib/ObservedArticleText.svelte";

    let hasAlerted = false;

    const options = {
        threshold: [0.85, 0.95],
    };

    const simpleCallback = (entries, observer) => {
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

    const alertCallback = (entries, observer) => {
        entries.forEach((entry) => {
            const elem = entry.target;
            if (entry.intersectionRatio >= 0.9 && !hasAlerted) {
                // "active" state
                alert(
                    "The first time that article text section scrolls into view," +
                        " this alert pops up! Then, we set the hasAlerted flag to true," +
                        " which we use to prevent the alert from showing again." +
                        " Refresh the page if you want to see it happen again. " +
                        '(btw, "flag" is just a jargon term for a boolean variable!)',
                );
                hasAlerted = true;
            }
        });
    };
</script>

<div>
    <Scroller layout="right">
        {#snippet sticky()}
            <div>
                <p>
                    The removal of Affirmative Action policies has discouraged minority groups from applying to prestigious and selective institutions. 
                </p>

                <p>
                    The lack of diversity in educational institutions can have far-reaching consequences upon racial harmony and cooperation. Diversity and intercultural collaboration can reduce stereotypes and foster understanding amongst individuals of different backgrounds resulting in fewer conflicts and tensions. 
                </p>
                <p>
                    <a href = escholarship.org/uc/item/91w10c8>CREDE UC Berkeley</a>
                </p>
            </div>
        {/snippet}

        {#snippet scrolly()}
            <ObservedArticleText callback={simpleCallback} {options}>
                Affirmative Action can promote interethnic relations
            </ObservedArticleText>

        

            <ObservedArticleText callback={simpleCallback} {options}>
                In an increasingly global world, diverse interactions are necessary to promote prosocial behaviour, enhance creativity and broaden horizons.
            </ObservedArticleText>

            <ObservedArticleText callback={simpleCallback} {options}>
                <strong>
                    All of us would benefit from a more equitable and diverse community!
                </strong>
            </ObservedArticleText>
        {/snippet}
    </Scroller>
</div>


<img src="Thank.png" alt="Thank you" width="1100">
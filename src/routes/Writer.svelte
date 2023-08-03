<style>
    :root {
        --pageLength: 936px;
        --pageWidth: 612px;
        --rulerThickness: 50px;
    }
    #writer-horizontal-select-div {
        display: flex;
        flex-direction: row;
    }
    #writer-vertical-select-div-1 {
        display: flex;
        flex-direction: column;
        margin-left: auto;
    }
    #writer-vertical-select-div-2 {
        display: flex;
        flex-direction: column;
        margin-right: auto;
    }
    main {
        height: calc(var(--pageLength) - var(--pagePaddingTop) - var(--pagePaddingBottom));
        width: calc(var(--pageWidth) - var(--pagePaddingLeft) - var(--pagePaddingRight));
        padding-left: var(--pagePaddingLeft);
        padding-right: var(--pagePaddingRight);
        padding-top: var(--pagePaddingTop);
        padding-bottom: var(--pagePaddingBottom);
        background: gray;
    }
    #top-ruler {
        height: var(--rulerThickness);
        width: var(--pageWidth);
        background: violet;
    }
    #side-ruler {
        height: var(--pageLength);
        width: var(--rulerThickness);
        background: violet;
    }
    #margin-neutral-button {
        height: calc(var(--rulerThickness) - 20px);
        width: calc(var(--rulerThickness) - 20px);
        margin: 10px;
    }
    #character-counter {
        background: green;
        height: 75px;
        padding: 10px;
        position: fixed;
        bottom: 0;
        left: 0;
    }
</style>
<!-- Vertical select divs are set as IDs in case I want to add a few things on the left-hand and right-hand (with a third select div) side later. -->
<div id="writer-horizontal-select-div">
    <div id="writer-vertical-select-div-1">
        <button id="margin-neutral-button" on:click={() => asd()}></button>
        <div id="side-ruler"></div>
    </div>
    <div id="writer-vertical-select-div-2">
        <div id="top-ruler"></div>
        <main contenteditable="true" id="writer-main" bind:textContent={textCount} bind:innerHTML={innerHTMLContent} style="--pagePaddingLeft: {pagePaddingLeft};--pagePaddingRight: {pagePaddingRight};--pagePaddingTop: {pagePaddingTop};--pagePaddingBottom: {pagePaddingBottom}" on:keypress={() => textCounter()}></main>
    </div>
    <div id="character-counter">
        <p>Chars: {charCounterValue}</p>
    </div>
</div>

<script>
    let textCount
    let innerHTMLContent
    let charCounterValue = 0

    const textCounter = () => {
        console.log("Character count:", textCount.length + 1)
        charCounterValue = textCount.length + 1
        if (textCount.length > 33) save()
    }
    const save = () => {
        console.log(innerHTMLContent)
    }
//Experimental area
    let pagePaddingLeftValue = 50
    let pagePaddingLeft = pagePaddingLeftValue.toString() + "px"
    let pagePaddingRightValue = 50;
    let pagePaddingRight = pagePaddingRightValue.toString() + "px"
    let pagePaddingTopValue = 50;
    let pagePaddingTop = pagePaddingTopValue.toString() + "px"
    let pagePaddingBottomValue = 50;
    let pagePaddingBottom = pagePaddingBottomValue.toString() + "px"

    const asd = () => {
        pagePaddingLeftValue += 50
        pagePaddingLeft = pagePaddingLeftValue.toString() + "px"
        console.log(pagePaddingLeft)
    }
</script>
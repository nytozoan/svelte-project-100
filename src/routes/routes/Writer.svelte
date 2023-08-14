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

    
    #tray {
        background: cyan;
    }
    ul {
        display: flex;
        gap: 5px;
        justify-content: center;
        margin-left: auto;
        margin-right: auto;
        width: 50%;
    }
    li {
        list-style-type: none;
    }
</style>
<div id="tray">
    <ul>
        <li><button id="tray-bold" on:click={() => bold()}>B</button></li>
        <li><button id="tray-italicize" on:click={() => italicize()}>I</button></li>
        <li><button id="tray-underline" on:click={() => underline()}>U</button></li>
    </ul>
</div>
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
        // console.log("Character count:", textCount.length + 1)
        charCounterValue = textCount.length + 1
    }
    const save = () => {
        console.log(textCount)
    }

    
    const getCursor = () => {
        return window.getSelection().focusOffset
        // console.log("\nGet Selection:", x)
        // console.log("Text Count Current:", Array.from(textDataArray)[x-1])
        // console.log("Text Count Array:", Array.from(textCount))
    }
    
    let boldState = 0
    const bold = () => {
        if (boldState == 0) {
            boldState = 1
            let x = Array.from(textCount)
            let y = x.splice(0, getCursor())
            y.push("****")
            y.push(x.join(""))
            innerHTMLContent = y.join("")
        }
        else if (boldState == 1) boldState = 0
        console.log("boldState:", boldState)
    }
    let italicizeState = 0
    const italicize = () => {
        if (italicizeState == 0) {
            italicizeState = 1
            let x = Array.from(textCount)
            let y = x.splice(0, getCursor())
            y.push("**")
            y.push(x.join(""))
            innerHTMLContent = y.join("")
        }
        console.log("italicizeState:", italicizeState)
    }
    let underlineState = 0
    const underline = () => {
        if (underlineState == 0) {
            underlineState = 1
            let x = Array.from(textCount)
            let y = x.splice(0, getCursor())
            y.push("__")
            y.push(x.join(""))
            innerHTMLContent = y.join("")
        }
        console.log("underlineState", underlineState)
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

    export const asd = () => {
        console.log(textCount)
        // pagePaddingLeftValue += 50
        // pagePaddingLeft = pagePaddingLeftValue.toString() + "px"
        // console.log(pagePaddingLeft)
    }
</script>
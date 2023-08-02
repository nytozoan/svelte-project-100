<style>
    :root {
        --pageLength: 936px;
        --pageWidth: 612px;
        --rulerThickness: 20px;
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
        margin-left: auto;
        margin-right: auto;
    }
    main {
        height:var(--pageLength);
        width: var(--pageWidth);
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
        height: var(--rulerThickness);
        width: var(--rulerThickness);
    }
</style>
<!-- Vertical select divs are set as IDs in case I want to add a few things on the left-hand and right-hand (with a third select div) side later. -->
<div id="writer-horizontal-select-div">
    <div id="writer-vertical-select-div-1">
        <button id="margin-neutral-button"></button>
        <div id="side-ruler"></div>
    </div>
    <div id="writer-vertical-select-div-2">
        <div id="top-ruler"></div>
        <main contenteditable="true"></main>
    </div>
</div>

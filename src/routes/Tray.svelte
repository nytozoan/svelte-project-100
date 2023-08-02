<style>
    #main {
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

<div id="main">
    <ul>
        <li>Placeholders</li>
        <li><button id="tray-bold" on:click={() => bold()}>B</button></li>
        <li><button id="tray-italicize" on:click={() => italicize()}>I</button></li>
        <li><button id="tray-underline" on:click={() => underline()}>U</button></li>
    </ul>
</div>

<script>
    let boldState = 0
    const bold = () => {
        if (boldState == 0) boldState = 1
        else if (boldState == 1) boldState = 0
        console.log("boldState:", boldState)
    }
    let italicizeState = 0
    const italicize = () => {
        if (italicizeState == 0) italicizeState = 1
        else if (italicizeState == 1) italicizeState = 0
        console.log("italicizeState:", italicizeState)
    }
    let underlineState = 0
    const underline = () => {
        if (underlineState == 0) underlineState = 1
        else if (underlineState == 1) underlineState = 0
        console.log("underlineState:", underlineState)
    }
</script>
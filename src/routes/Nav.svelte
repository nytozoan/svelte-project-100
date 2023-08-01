<script>
    let fileDisplay = "none"
    let optionsDisplay = "none"
    let pluginsDisplay = "none"
    let helpDisplay = "none"

    const showNavFileSublist = (dropdown) => {
        if (dropdown == "flex") return "none"
        else if (dropdown == "none") {
            fileDisplay = "none"
            optionsDisplay = "none"
            pluginsDisplay = "none"
            helpDisplay = "none"
            return "flex"
        }
    }
</script>

<style>
    #main {
        background: red;
    }
    li {
        list-style-type: none;
    }
    #nav-mainlist {
        display: flex;
        gap: 10px;
    }
    #nav-file-sublist {
        flex-direction: column;
        gap: 10px;
        background: orange;
    }
    #nav-options-sublist {
        flex-direction: column;
        gap: 10px;
        background: orange;
    }
    #nav-plugins-sublist {
        flex-direction: column;
        gap: 10px;
        background: orange;
    }
    #nav-help-sublist {
        flex-direction: column;
        gap: 10px;
        background: orange;
    }
</style>


<div id="main">
    <geek />
    <div>
        <h1 contenteditable="true">Your Document's Title Here</h1>
    </div>
    <div>
        <ul id="nav-mainlist">
            <li><button on:click={() => fileDisplay = showNavFileSublist(fileDisplay)}>File</button>
                <ul id="nav-file-sublist" style="display: {fileDisplay}">
                    <li>New</li>
                    <li>Open</li>
                    <li>Save</li>
                </ul>
            </li>
            <li><button on:click={() => optionsDisplay = showNavFileSublist(optionsDisplay)}>Options</button>
                <ul id="nav-options-sublist" style="display: {optionsDisplay}">
                    <li>Sample option here</li>
                </ul>
            </li>
            <li><button on:click={() => pluginsDisplay = showNavFileSublist(pluginsDisplay)}>Plugins</button>
                <ul id="nav-plugins-sublist" style="display: {pluginsDisplay}">
                    <li>Install plugin</li>
                    <li>Sample plugin</li>
                </ul>
            </li>
            <li><button on:click={() => helpDisplay = showNavFileSublist(helpDisplay)}>Help</button>
                <ul id="nav-help-sublist" style="display: {helpDisplay}">
                    <li>Beginners' Guide</li>
                    <li>Documentation</li>
                    <li>About</li>
                </ul>
            </li>
        </ul>
    </div>
</div>
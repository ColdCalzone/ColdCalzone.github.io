<section>
<style>
	#reset {
		cursor:pointer
	}
	h1, h2, h3, h4, h5, h6, a {
		text-shadow: none;
	}
	.post-icon {
		height: 100%;
		width: auto;
		display: inline-block; 
		position: absolute;
		right: 8px;
	}
	.name {
		display: inline-block;
	}
	.head {
		display: flex; 
		align-items: center; 
		position:relative;
	}
	@media only screen and (max-width: 645px) {
		/* For desktop: */
		.post-icon {
			display: none;
		}
	}
</style>
<script>
	/* WHY CAN'T THE INTERNET EVER SHOW ME *UP TO DATE* THINGS? */
	var restrictedTag = window.location.href.split("#")[1];
    var projects = []
    var root = document.getElementById("main_content");
    function removeFromPage(value, index, array) {
    	document.removeChild(value);
    	console.log("fucking hell");
    }
    function addToPage(value, index, array) {
        if(value["tags"].includes(restrictedTag) || restrictedTag == undefined) {
            var post = document.createElement("div");
            post.classList.add("post");
            var head = document.createElement("div");
            head.classList.add("head");
            var name = document.createElement("h3");
            name.innerHTML = value["name"];
            name.classList.add("name");
            head.appendChild(name);
            var icon = document.createElement("img");
            icon.src = value["icon"];
            icon.classList.add("post-icon");
            head.appendChild(icon);
            post.appendChild(head);
            var description = document.createElement("p");
            description.innerHTML = value["description"];
            post.appendChild(description);
            var source = document.createElement("h6");
            source.innerHTML = "<a href = \"" + value["source"] + "\">View the source code.</a>";
            post.appendChild(source);
            var tags = document.createElement("h6");
            var tag_list = "";
	    for(var i = 0;i < value["tags"].length;i++) {
	    	tag_list += "<a href=\"#" + value["tags"][i] + "\" onclick=\"reloadPage('#"+ value["tags"][i] +"')\">" + value["tags"][i] + "</a>"
	    	console.log("Help?");
	    	if(i + 1 < value["tags"].length) {
	    		tag_list += ", ";
	    	}
	    }
            tags.innerHTML = "Tags: " + tag_list;
            tags.classList.add("tags");
            post.appendChild(tags);
            root.appendChild(post);
            root.appendChild(document.createElement("hr"));
        }
    }
    async function generateSite() {
        await fetch("./projects.json")
                .then(response => {
                return response.json();
            }).then(json => projects = json);
        projects.forEach(addToPage); 
    }
    root.appendChild(document.createElement("hr"))
    generateSite();
    
    function reloadPage(tag) {
    	window.location.href = tag;
	window.location.reload();
    }
</script>
        <h1 id="coldcalzones-personal-hell">ColdCalzone’s Personal hell</h1>
	<h6 id="this-page-is-just-to-document-some-code-and-other-such-creations-of-mine">This page is just to document some code and other such creations of mine.</h6>
	<h5 id="my-github-page-where-the-repositories-are"><a href="https://github.com/ColdCalzone">My Github page (where the repositories are)</a></h5>
	<h5>Click on a tag to filter results to that tag, click the button below to reset the current tag filter</h5>
	<a class="btn" id="reset" onclick="reloadPage('/')" href="/">Reset Tag</a>
	<b>Get my latest game here:</b>
	<iframe src="https://itch.io/embed/1397309?bg_color=0d1120&amp;fg_color=cccccc&amp;link_color=f2843c&amp;border_color=bebebe" width="552" height="167" frameborder="0"><a href="https://coldcalzone.itch.io/bread">Bread Bread Breadvolution: Extra Toasty by ColdCalzone</a></iframe>
</section>

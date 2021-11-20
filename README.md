<section>
<style>
div li{
    float: left;
    width: 140px;
    height: 60px;
    font-size: 20px;
    line-height: 60px;
    /* border: 1px solid #000; */
    text-align: center;
}

div li a{
    text-decoration: none;
    color: #000;
    /* background-color: red; */
    display: block;
}

div li a:hover{
    background-color: #0cd2f3;
    transition: 1s all ease;
}
@keyframes drop{
    0%{
        transform: scale(2,2) rotatex(90deg);
    }
    100%{
        transform: scale(1,1) rotatex(0deg);
    }
}

</style>
<script>
	/* WHY CAN'T THE INTERNET EVER SHOW ME *UP TO DATE* THINGS? */
	var restrictedTag = window.location.href.split("#")[1];
	var projects = []
	var root = document.getElementById("main_content");
	function addToPage(value, index, array) {
		if(value["tags"].includes(restrictedTag)) {
			var post = document.createElement("div");
			var name = document.createElement("h3");
			name.innerHTML = value["name"];
			post.appendChild(name);
			var description = document.createElement("p");
			description.innerHTML = value["description"];
			post.appendChild(description);
			var source = document.createElement("h6");
			source.innerHTML = "<a href = \"" + value["source"] + "\">View the source code.</a>";
			post.appendChild(source);
			var tags = document.createElement("h6");
			tags.innerHTML = "Tags: " + value["tags"].join(", ");
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
	generateSite();
</script>
        <h1 id="coldcalzones-personal-hell">ColdCalzone’s Personal hell</h1>
	<h6 id="this-page-is-just-to-document-some-code-and-other-such-creations-of-mine">This page is just to document some code and other such creations of mine.</h6>
	<div>
		<a class="btn">Tags</a>
		<li><a href="#">Samsung</a></li>
		<li><a href="#">Apple</a></li>
		<li><a href="#">Asus</a></li>
	</div>
	<h5 id="my-github-page-where-the-repositories-are"><a href="https://github.com/ColdCalzone">My Github page (where the repositories are)</a></h5>
	<hr>
</section>

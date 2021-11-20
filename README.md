<section>
<script>
	/* WHY CAN'T THE INTERNET EVER SHOW ME *UP TO DATE* THINGS? */
	var projects = []
	var root = document.getElementById("main_content");
	function addToPage(value, index, array) {
		var post = document.createElement("div");
		var name = document.createElement("h3");
		name.innerHTML = value["name"];
		post.appendChild(name);
		var description = document.createElement("p");
		description.innerHTML = value["description"];
		post.appendChild(description);
		var source = document.createElement("h6");
		source.innerHTML = "<a href = \"" + value["source"] + "\">View the source code.</a>"
		post.appendChild(source);
		root.appendChild(post);
		root.appendChild(document.createElement("hr"));
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
	<h5 id="my-github-page-where-the-repositories-are"><a href="https://github.com/ColdCalzone">My Github page (where the repositories are)</a></h5>
	<hr>
</section>

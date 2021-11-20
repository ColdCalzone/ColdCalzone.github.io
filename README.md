<section id="main_content">
	<script>
	// https://www.codeproject.com/Tips/1263247/How-to-Open-a-JSON-File-in-JavaScript-for-Web
	function loadJSON(callback) {
                    var xobj = new XMLHttpRequest();
                    xobj.overrideMimeType("application/json");

                    xobj.onreadystatechange = function () {
                            if (xobj.readyState == 4 && xobj.status == "200") {
                                // Required use of an anonymous callback as .open will NOT return 
                                // a value but simply returns undefined in asynchronous mode
                                callback(xobj.responseText);
                            } else {
                                callback("[{\"Nothing\"}]");
                            }
                        };

                    xobj.open('GET', 'projects.json', true);
                    // Maybe you require use of an unknown origin.
                    /*xobj.setRequestHeader("Access-Control-Allow-Origin","*");*/
                    xobj.send(null);  
                };
            var projects = []
            loadJSON(function(response) {
                    projects = response;
                });
	    console.log(projects);
</script>
        <h1 id="coldcalzones-personal-hell">ColdCalzone’s Personal hell</h1>
	<h6 id="this-page-is-just-to-document-some-code-and-other-such-creations-of-mine">This page is just to document some code and other such creations of mine.</h6>
	<h5 id="my-github-page-where-the-repositories-are"><a href="https://github.com/ColdCalzone">My Github page (where the repositories are)</a></h5>
	<hr>

	
</section>

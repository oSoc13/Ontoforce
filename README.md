Genetikos
===================

WikiPathways is an open, public platform dedicated to the curation of biological pathways by and for the scientific community. A pathway is basicly a biological network that contains elements like genes, metabolisms, etc. These pathways can be downloaded (as TXT, PDF, PNG, SVG, etc.) directly from the [WikiPathways API](http://wikipathways.org/index.php/Help:WikiPathways_Webservice/API#getPathwayAs). Genetikos makes interaction with these elements possible (if more information about the element is available), you can:
 * hover an element
 * click on an element (multiple with hotkey: shift)
 * select an area of elements (multiple with hotkey: shift)
 * unselect elements with hotkey


Genetikos requests the SVG version of a specific pathway from the API. Afterwards a SPARQL Query is send to the SPARQL Endpoint of WikiPathways, and those information is mapped directly on each element of the SVG. JQuery is used to bind the events (hover,click) on a specific element. QunitJS is used for testing.

Requirements
===================
JQuery 1.7 (or higher)

Usage
===================
Include the javascript files.
```
<script type="text/javascript" src="http://code.jquery.com/jquery-2.0.0.min.js"></script>
<script type="text/javascript" src="js/jquery.genetikos.js"></script>
```

Bind Genetikos on a HTML-element and specify a callback function.
````
<script type="text/javascript">
    $(document).ready(function(){
        $("#pathway").genetikos({
            pathway_id:"WP1603",
            onselection: processNodes
        });
        function processNodes(elements) { 
            // do something with array of elements
            var str = elements.length + " element(s) in area selected <br/>-------<br/>";
            for(var i = 0; i < elements.length; i++)
                str += elements[i]["id"] + " " + elements[i]["value"] + "<br/>";
            $("#output").html(str);
        }
    });
</script>

<div id="pathway">Loading...</div>
<div id="output"></div>
```

When an area is selected, the area design can be specified with the following CSS selector.
```
#pathway #genetikos-region{
    background-color: #ccc;
    border: 1px dotted #333;
    opacity: 0.3;
}
```

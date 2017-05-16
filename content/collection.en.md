+++
date = "2017-03-30"
title = "Full Collection"
+++

To find maps by sheet name or NTS sheet number, use the search box or scroll through the list below. Once you have found a map, select _View in GeoPortal_ to visualize this map in the Scholars GeoPortal. This will overlay the map onto a current base map, allowing you to explore changes over time. It will also provide you with more detailed information about the map itself.

Please note that the map sheet name does not always correspond to the place name. For example, all early maps of London, ON were titled _Lucan_ or _St. Thomas_. If you are unable to find the place you are looking for by using the search box below, consult Natural Resources Canada's [name search](http://www4.rncan.gc.ca/search-place-names/search) to find the NTS number for that location. 

You can also search for maps by accessing the map indexes directly in the Scholars GeoPortal. Consult the [Using the Maps](../using-maps/) section for more information on using the map indexes and searching for maps in Scholars GeoPortal.

- [1:63 360 Index Navigation](http://geo.scholarsportal.info/#r/details/_uri@=564032357&_add:true)
- [1:25 000 Index Navigation](http://geo.scholarsportal.info/#r/details/_uri@=847590539&_add:true) 


<input placeholder="Search by sheet map name or number" name="Place name search" id="index-filter" type="text" aria-label="Search by sheet map name"/>

<script>
// Import a json file (previously sorted by place name, then year) and display, keeping all of the items with the same place name displayed together

  $.getJSON("../combined_namesort.json", function(json) {

    // Create an array from the json file
    var jsontext = JSON.parse(JSON.stringify(json));
    var lines = '';

    for (var i = 0; i<jsontext.length; i++) {
      var title = jsontext[i].title.replace(/[^a-zA-Z0-9-_]/g, '');

      // if the title for the current item is not the same as the previous one, print the place name
      if (jsontext[ (i===0) ? (jsontext.length-1) : (i-1)].title !== jsontext[i].title) {
        lines += '<div>';
        lines += '<a class="toggle-mapsheets" href="" data-target="' + title + '-section">' + jsontext[i].title + ' <p class="hidden-sheet" aria-hidden="true"> ' + jsontext[i].sheet +'</p></a></div>';
      }

      lines += '<div class="' + title + '-section sheet-item">';
      lines += '<p>Year: ' + jsontext[i].year + ', ';
      lines += 'Sheet no. ' + jsontext[i].sheet + ' |';
      lines += '<a href="http://geo.scholarsportal.info/#r/details/_uri@=' + jsontext[i].fullname + '&_add:true" target="_blank"> View in GeoPortal<i class="fa fa-external-link" aria-hidden="true"></i></a>| ';
      lines += '<a href="http://ocul.on.ca/topomaps/map-images/' + jsontext[i].fullname + '.jpg"> Download image </a></p>';
      lines += '</div>';

      // append the content into the div with the same id
      $(lines).appendTo('#index');

      // reset the lines variable so it isn't duplicated on the next loop
      lines = "";
    }

    // expand to see all sheets when the place name is clicked
    $( '.toggle-mapsheets' ).click(function(e) {
      e.preventDefault();
      var cssClass = $(e.target).data('target');
      $( '.' + cssClass ).toggle();
    });

    // Filter box
    $('#index-filter').keyup(function(){
        var valThis = $(this).val().toLowerCase();
        $('.sheet-item:visible').hide();

      if(valThis == ""){
          $('.toggle-mapsheets').show();
      }

      else {
        $('.toggle-mapsheets').each(function(){
            var text = $(this).text().toLowerCase();
            (text.indexOf(valThis) >= 0) ? $(this).show() : $(this).hide();
        });
      };
    });
  });
</script>

<div id="index"></div>

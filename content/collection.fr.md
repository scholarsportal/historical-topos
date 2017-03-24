+++
date = "2017-03-16"
title = "Collection complète"
+++

To find maps by place name, use the search box or scroll through the list below. Once you have found a map, select View in GeoPortal to visualize this map in the Scholar’s Portal GeoPortal. This will overlay the map onto a current base map, allowing you to explore changes over time. It will also provide you with more detailed information about the map itself.

For more information on using the map index and searching maps in the GeoPortal, see [‘Using the Maps’](../using-maps).

<input placeholder="Recherche par nom de feuille" name="Place name search" id="index-filter" type="text" aria-label="
Recherche par nom de feuille"/>

<script>
// Import a json file (previously sorted by place name, then year) and display, keeping all of the items with the same place name displayed together

  $.getJSON("../../combined_namesort.json", function(json) {

    // Create an array from the json file
    var jsontext = JSON.parse(JSON.stringify(json));
    var lines = '';

    for (var i = 0; i<jsontext.length; i++) {
      var title = jsontext[i].title.replace(/[^a-zA-Z0-9-_]/g, '');

      // if the title for the current item is not the same as the previous one, print the place name
      if (jsontext[ (i===0) ? (jsontext.length-1) : (i-1)].title !== jsontext[i].title) {
        lines += '<div>';
        lines += '<a class="toggle-mapsheets" href="" data-target="' + title + '-section">' + jsontext[i].title + '</a></div>';
      }

      lines += '<div class="' + title + '-section sheet-item">';
      lines += '<p>Year: ' + jsontext[i].year + ' | ';
      lines += '<a href="http://geodev.scholarsportal.info/#r/details/_uri@=' + jsontext[i].fullname + '&_add:true"> View in GeoPortal<i class="fa fa-external-link" aria-hidden="true"></i></a>| '; 
      lines += '<a href="http://geostaging.scholarsportal.info/proxy.html?http:__maps.scholarsportal.info/files/images/OpenContent/' + jsontext[i].fullname + '.jpg"> Download image </a></p>';
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

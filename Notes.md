# jQuery


4.5 Slide Effect I 
In this new click event handler, show the .photos element by querying the DOM for it then calling slideDown. This will draw the eye to the photos by adding a little movement.


`$(document).ready(function() { 
  $('#tour').on('click', 'button', function() { 
    $('.photos').slideDown();
  });
});`

4.6 Slide Effect II
The photos will now be shown, but we have no way of hiding them. Let's change this to use slideToggle so that the photos will be hidden if they click again.



`$(document).ready(function() { 
  $("#tour").on("click", "button", function() { 
    $(".photos").slideToggle();
  });
});`

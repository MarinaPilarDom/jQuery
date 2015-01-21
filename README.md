# jQuery


4.5 Slide Effect I 
In this new click event handler, show the .photos element by querying the DOM for it then calling slideDown. This will draw the eye to the photos by adding a little movement.

[code]
$(document).ready(function() { 
  $('#tour').on('click', 'button', function() { 
    $('.photos').slideDown();
  });
});
[/code]

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

4.8 Mouseover I
Our tour page is going great! Let's add a bit more behavior to the page though. Write an event handler that watches for mouseenter on any li elements within our .photos elements and runs an empty function. We'll implement the function later on.


`$(document).ready(function() { 
  $('#tour').on('click', 'button', function() { 
    $('.photos').slideToggle();
  });
  $('.photos').on('mouseenter', 'li', function() {
    $(this).find('span').slideToggle();
  });
});`

4.9 Mouseover II 
In our new mouseenter event handler, call slideToggle on the span tag within the picture description. You'll need to traverse down from the current element, the li, and find the span tag.

`$(document).ready(function() { 
  $('#tour').on('click', 'button', function() { 
    $('.photos').slideToggle();
  });
  $('.photos').on('mouseenter', 'li', function() {
    $(this).find('span').slideToggle();
  });
});`

4.10 Mouseleave
When the mouse leaves the li element, we'll want to hide the description of the photo as well. Write another event handler that targets the same elements, but calls slideToggle only on the mouseleave event.

`$(document).ready(function() {
  $("#tour").on("click", "button", function() {
    $(".photos").slideToggle();
  });
  $(".photos").on("mouseenter", "li", function() {
    $(this).find("span").slideToggle();
  });
    $(".photos").on("mouseleave", "li", function() {
    $(this).find("span").slideToggle();
  });
});
`
4.11 Named Functions 
It looks like both our event handler on .photos li elements are exactly the same! Let's go ahead and refactor these into a new function named showPhotos and change our event handlers to reference that instead.

`$(document).ready(function() {
  $("#tour").on("click", "button", function() {
    $(".photos").slideToggle();
  });

  function showPhotos() {
    $(this).find("span").slideToggle();
  }
  $(".photos").on("mouseenter", "li", showPhotos)
              .on("mouseleave", "li", showPhotos);
});`

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

4.13 Keyup Event 
We've made a few changes to our tour page. Now we'll allow travelers to specify how many days they want their vacation to be. Write an event handler that will fire whenever the value within the keyup event is triggered on the #nights form field. The function can be empty now, then we'll implement it later.

'$(document).ready(function() {
  $('#nights').on('keyup', function() {
     $('#nights-count').text($(this).val());
  });
});'

4.14 Keyup Event Handler I
Within our event handler, update the number of nights in the #nights-count element to whatever the traveler entered in the #nights form field.

`$(document).ready(function() {
  $("#nights").on("keyup", function() {
    $("#nights-count").text($(this).val());
  });
});`

4.15 Keyup Event Handler II 
Set the content of the #total element to the number the traveler has entered into the form field multiplied by the daily price.

`$(document).ready(function() {
  $('#nights').on("keyup", function() {
    var nights = +$(this).val();
    var dailyPrice = +$(this).closest('.tour').data('daily-price');
    $('#total').text(nights * dailyPrice);
    $('#nights-count').text($(this).val());
  });
});`

4.16 Another Event Handler 
Let's write another event handler for the form field that will be run when the focus event is triggered. When this occurs, set the number of nights to 7.


`$(document).ready(function() {
  $('#nights').on('keyup', function() {
    var nights = +$(this).val();
    var dailyPrice = +$(this).closest('.tour').data('daily-price');
    $('#total').text(nights * dailyPrice);
    $('#nights-count').text($(this).val());
  }).on('focus', function(){
    $(this).val('7');
  });
});`


4.18 Link Events I
Write an event handler that will target all links with a class of .see-photos on click.

`$(document).ready(function() {
  $('.see-photos').on('click', function(event) {
    event.preventDefault();
  });
});`

4.19 Link Events II 
When this link is clicked, show the photos for the clicked tour by traversing to it using closest and find then sliding it down by using slideToggle.

`$(document).ready(function() {
  $('.see-photos').on('click', function(event) {
    event.preventDefault();
    $(this).closest('.tour').find('.photos').slideToggle();
  });
});`

4.20 Event Parameter I
Change your event handler method to take in a link event and prevent the other event handler from being called.

'$(document).ready(function() {
  $('.see-photos').on('click', function(event) {
    event.stopPropagation();
    $(this).closest('.tour').find('.photos').slideToggle();
  });
  $('.tour').on('click', function() {
    alert('This should not be called');
  });
});'

4.21 Event Parameter II 
Let's change this so that the browser doesn't jump to the top of the page when the link is clicked as well.

`$(document).ready(function() {
  $('.see-photos').on('click', function(event) {
    event.stopPropagation();
    event.preventDefault();
    $(this).closest('.tour').find('.photos').slideToggle();
  });
  $('.tour').on('click', function() {
    alert('This should not be called');
  });
});`

5.3 CSS I
Let's try to make this page stand out a bit more. For starters, let's add an event handler that will set the background-color to #252b30 using the css method whenever the mouseenter event is triggered.

`$(document).ready(function() {
  $('.tour').on('mouseenter', function() {
    $(this).css('background-color', '#252b30');
  });
});`

5.4 CSS II
Let's set the font-weight to bold as well by passing in a JavaScript object to the css method.

`$(document).ready(function() {
  $('.tour').on('mouseenter', function() {
    $(this).css({'background-color': '#252b30',
                 'font-weight': 'bold'});
  });
});`

5.5 Show Photo 
Let's see what the tour page would look like if we showed the photos on mouseenter as well. Try using the show method here to make it visible.

`$(document).ready(function() {
  $('.tour').on('mouseenter', function() {
    $(this).css({'background-color': '#252b30', 'font-weight': 'bold'});
    $('.photos').show();
  });
});`

5.6 Refactoring to CSS
We've extracted out our styles into a new CSS class of highlight. Go ahead and add this class when the tour is moused over. Also, add another event handler for when the mouse leaves the .tour element to remove this class by watching for mouseleave.

`$(document).ready(function() {
  $('.tour').on('mouseenter', function() {
    $(this).addClass('highlight');
  }).on('mouseleave', function(){
      $(this).removeClass('highlight');
  });
});`



# How-to-add-google-translator-in-website
How to add google translator in website


```html 
<ul class="translation-links">
			  <li><a href="#" class="spanish" data-lang="Spanish">Spanish</a></li>
			  <li><a href="#" class="german" data-lang="German">German</a></li>
</ul>
		  
 <div id="google_translate_element" style="display:none"></div>
```

```js

<script src="//translate.google.com/translate_a/element.js?cb=googleTranslateElementInit" type="text/javascript"></script>


<script type="text/javascript">
  function googleTranslateElementInit() {
    new google.translate.TranslateElement({pageLanguage: 'en', autoDisplay: false}, 'google_translate_element'); //remove the layout
  }
</script>


<!-- Flag click handler -->
<script type="text/javascript">
    function triggerHtmlEvent(element, eventName) {
var event;
if(document.createEvent) {
    event = document.createEvent('HTMLEvents');
    event.initEvent(eventName, true, true);
    element.dispatchEvent(event);
} else {
    event = document.createEventObject();
    event.eventType = eventName;
    element.fireEvent('on' + event.eventType, event);
}
}
            <!-- Flag click handler -->
        $('.translation-links a').click(function(e) {
  e.preventDefault();
  var lang = $(this).data('lang');
  $('#google_translate_element select option').each(function(){
    if($(this).text().indexOf(lang) > -1) {
        $(this).parent().val($(this).val());
        var container = document.getElementById('google_translate_element');
        var select = container.getElementsByTagName('select')[0];
        triggerHtmlEvent(select, 'change');
    }
});
});


</script>


```

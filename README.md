# JSizes ― jQuery extension plugin for CSS properties

JSizes is a small plugin for the [jQuery JavaScript library](http://jquery.com/) which adds convenience methods for querying and setting the CSS `min-width`, `min-height`, `max-width`, `max-height`, `border-*-width`, `margin`, and `padding` properties. Additionally it has one method for determining whether an element is visible. In total it adds six new methods to the jQuery element API. It internally calls the jQuery built-in `css` method, so syntax and use is identical to calling `css('property-name', ...)`. An example of its use follows.

    jQuery(function($) {
       var myDiv = $('#myDiv');
    
       myDiv.minWidth(100); // set 'min-width' to 100px
       alert(myDiv.minWidth()); // displays '100'
    });

Note that all returned values are converted to pixel values, without the `px` suffix. It is thus safe to use these methods in calculations without having to worry about non-numeric values. Most importantly, it does *not* add support for min- and max-sizes on browsers that do not natively support it, it just adds convenient methods to query these properties and return a sensible value when they are not available or not set.

## API

The plugin adds the following methods to the JQuery object:

<dl>
    <dt>minSize()</dt>
    <dd>Returns the CSS `min-width` and `min-height` properties of the first matched element as pixel values in an object with `width` and `height` properties. If a CSS property is not set `0` is returned as value.
</dd>
    <dt>minSize(value)</dt>
    <dd>Sets the CSS `min-width`, and `min-height` property on all matched elements. Expects a value object containing any of `width` and `height` properties. If the property values are numbers they will be converted to pixel values.</dd>
    
    <dt>maxSize()</dt>
    <dd>Returns the CSS `max-width` and `max-height` properties of the first matched element as pixel values in an object with `width` and `height` properties. If a CSS property is not set `Number.MAX_VALUE` is returned as value.</dd>
    
    <dt>maxSize(value)</dt>
    <dd>Sets the CSS `max-width` and `max-height` property on all matched elements. Expects a value object containing any of `width` and `height` properties. If the property values are numbers they will be converted to pixel values.</dd>
    
    <dt>margin()</dt>
    <dd>Returns the CSS `margin` property of the first matched element as pixel values in an object with `top`, `bottom`, `left`, and `right` properties.</dd>
    
    <dt>margin(value)</dt>
    <dd>Sets the CSS `margin` property on all matched elements. Expects a value object containing any of `top` , `bottom` , `left` , and `right` properties. If the property values are numbers they will be converted to pixel values.</dd>
    
    <dt>padding()</dt>
    <dd>Returns the CSS `padding` property of the first matched element as pixel values in an object with `top`, `bottom`, `left`, and `right` properties.</dd>
    
    <dt>padding(value)</dt>
    <dd>Sets the CSS `padding` property on all matched elements. Expects a value object containing any of `top`, `bottom`, `left`, and `right` properties. If the property values are numbers they will be converted to pixel values.</dd>
    
    <dt>border()</dt>
    <dd>Returns the CSS `border-*-width` property of the first matched element as pixels values in an object with `top`, `bottom`, `left`, and `right` properties.</dd>
    
    <dt>border(value)</dt>
    <dd>Sets the CSS `border-*-width` property on all matched elements. Expects a value object containing any of `top`, `bottom`, `left`, and `right` properties. If the property values are numbers they will be converted to pixel values. Note that the CSS `border-style` property also needs to be set in order for the border to show.</dd>
    
    <dt>isVisible()</dt>
    <dd>Returns true if the any of the matched element are visible, false otherwise.</dd>
</dl>

## Examples

Some examples of how the new methods can be used:

    jQuery(function($) {
       var myDiv = $('#myDiv');
    
       // set margin-top to 100px and margin-bottom to 10em
       myDiv.margin({top: 100, bottom: '10em'});
    
       // displays the size of the top border in pixels
       alert(myDiv.border().top);
    
       // displays true if the element is visible, false otherwise
       alert(myDiv.isVisible());
    
       // set padding-right to 10px and margin-left to 15px using chaining
       myDiv.padding({right: 10}).margin({left: 15});
    });

The above example also shows that chaining can be used on methods that do not return values.

## Credits

* John Bowers ― Setting values to zero bug fix.
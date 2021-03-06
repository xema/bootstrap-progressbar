# bootstrap-progressbar - 0.4.6

`bootstrap-progressbar` is a [jQuery](http://jquery.com) plugin which extends the basic [twitter-bootstrap](http://twitter.github.com/bootstrap) progressbar. It provides the ability to animate the progressbar by adding Javascript in combination with the preexisting css transitions. Additionally you can display the current progress information in the bar or get the value via callback.

## Demo

* http://minddust.github.com/bootstrap-progressbar

## Usage

1. include `bootstrap-progressbar.js`

    ```html
    <script type="text/javascript" src="bootstrap-progressbar.js"></script>
    ```

2. activate `bootstrap-progressbar` functionality on progressbars of your choice

    ```javascript
    $(document).ready(function() {
        $('.progress .bar').progressbar();
    });
    ```

3. set the `data` attribute and __remove__ the `width` style attribute (alternatively you can set it to 0)

    1. `data-percentage`

        ```html
        <div class="progress progress-info">
            <div class="bar" data-percentage="75"></div>
        </div>
        ```

    2. `data-amount-part` and `data-amount-total`

        ```html
        <div class="progress progress-info">
            <div class="bar" data-amount-part="1337" data-amount-total="9000"></div>
        </div>

## Usage Extended

You can now trigger progressbar as much as you want. Just change your `data` attribute and trigger `.progressbar()` again. All settings made before will be kept. Please have a look at the demo page for a working example.

## Customization

1. text and delay

    simply add additional parameters when activating the script

    ```javascript
    $(document).ready(function() {
        $('.progress .bar').progressbar({
            transition_delay: 300
        ,   refresh_speed: 50
        ,   display_text: 2
        ,   use_percentage: true
        ,   border_radius: '4px'
        ,   update: doSomethingCool( current_percentage ) { .. }
        ,   done: doSomethingCool( ) { .. }
        ,   fail: doSomethingCool( error_message ) { .. }
        });
    });
    ```
    * `transition_delay` is the time in milliseconds until the animation starts
    * `refresh_speed` is the time in milliseconds which will elapse between every text refresh / callback call
    * `display_text` determines whether the text will be displayed

        * `0` __no text__ *(this mode doesn't change any css / html)*
        * `1` __text on filled bar__ *(this mode doesn't change any css / html)*
        * `2` __text on center__ *(this mode changes css / html due to styling requirements)*
    * `use_percentage` determines whether the text will be displayed in percent or amount
    * `border_radius` hook to change the border radius of the progressbar

        * __you only have to set this if you are using centered text AND have overwritten the default bootstrap value__
    * `update` hook where you can grab the actual percentage value
    * `done` hook which indicates when progressbar is filled to the given value
    * `fail` hook where you can grab an error message when something went wrong

2. animation

    to change the animation itself you have to overwrite either less or css
    * less

        ```css
        .progress .bar {
          .transition(width 2s ease-in-out);
        }
        ```
    * css
    
        ```css
        .progress .bar {
            -webkit-transition: width 2s ease-in-out;
            -moz-transition: width 2s ease-in-out;
            -ms-transition: width 2s ease-in-out;
            -o-transition: width 2s ease-in-out;
            transition: width 2s ease-in-out;
        }
        ```

## License

Copyright 2012 [minddust.com](http://www.minddust.com)

bootstrap-progressbar is published under Apache License, Version 2.0 (see LICENSE file).
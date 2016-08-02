# pleaserespond v1

react-driven library for a fluid scss mobile-first layout.
currently it is a useful scss toolkit, but will be upgraded with intelligent fluidity

`npm install pleaserespond --save`

    //scss
    @import [path_to_node_modules]/pleaserespond/pleaserespond


Unifies normalize-sass, jeet, breakpoint-sass and provides a .wrap class to house your responsive content. You still need to skillfully leverage jeet to manage custom component breakpoints as you gradually go to higher resolutions (horizontally and/or vertically).

Plan and write all xhtml/css mobile first. At some point, you will begin resizing your browser window up in various directions and certain components will very apparently need a new breakpoint here or there to look natural. It can happen at 631px for all you know. The idea is to not only use the predefined breakpoint sizes like $mobile or $tablet. Though they are handy, jeet exists to allow extremely careful control of your website or app components on an individual basis.

Because jeet does not use a pre-defined grid system and has amazing gutter control, we do not have to pollute the DOM with any style-specific information (unless you want a fluid wrap). XHTML is for semantic content and CSS is for style, that was the idea a while ago some say.

    //html
    <section>
        <div class="wrap">
            <div class="pie">
                Pie is delicious
            </div>
            <div class="cake">
                Cake is delicious
            </div>
        </div>
    </section>
    
    //scss
    @import [path_to_node_modules]/pleaserespond/pleaserespond
    section{background: red;}
    
In the above case we will have two perfectly reasonable statements follow one another vertically on page. The red section will be 100% width, but the wrap will be a centered div with 95% (default) width that won't get larger than 1200px (default).

    //scss
    section{
        .pie{
            @include breakpoint($tablet) {
                @include column(2/3);
            }
        }

        .cake{
            @include breakpoint($tablet) {
                @include column(1/3);
            }
            
            @include breakpoint($tablet + 200) {
                background: blue;
            }
        }
    }

Now, above the $tablet breakpoint, we have a 3 column grid within our centered wrap, with Pie taking its well-deserved larger chunk of the screen. If you keep resizing the window by a few hundred pixels you might even see the cake get blue with envy.

# pleaserespond v2 - future plan

There will be a significant react core to the slim scss currently present in this repository. It will aim to speed up your responsive development, especially when it comes to areas highly reliant on screen fold size and variable-length content. We need to spend less time tweaking breakpoints when we can intelligently decide when it's time for something to notch itself up to the next breakpoint.


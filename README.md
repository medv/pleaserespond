# pleaserespond

Not a framework, but a ready collection with an opinion and some utils.

Unifies normalize.css, jeet.gs, sass-breakpoints and provides a .wrap class to house your responsive content. You still need to skillfully leverage jeet to manage custom component breakpoints as you gradually go to higher resolutions (horizontally and/or vertically).

Plan and write all xhtml/css with mobile-first mentality. At some point, you will begin resizing your browser window up in various directions and certain components will very apparently need a new breakpoint here or there to look natural. It can happen at 631px for all you know. The idea is to not only use the predefined breakpoint sizes like $mobile or $tablet. Though they are handy, jeet exists to allow extremely careful control of your website or app components on an individual basis.

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
        .left{
            @include breakpoint($tablet) {
                @include column(2/3);
            }
        }

        .right{
            @include breakpoint($tablet) {
                @include column(1/3);
            }
            
            @include breakpoint($tablet + 200) {
                background: blue;
            }
        }
    }

Now, above the $tablet breakpoint, we have 3 columns within our constricted wrap, with Pie taking its well-deserved larger chunk of the screen. If you keep resizing the window by a few hundred pixels you might even see the cake get blue with envy.
# Elementary
## Cascade

1. Importance:
    1.1 User !important
    1.2 Author !important
    1.3 Author
    1.4 User
    1.5 User agent

if RoolA.Importance === RoolB.Importance then

2. Specificity: (A, B, C, D)
    2.1 inline styles                     // each +1 to A
    2.1 id                                // each +1 to B  
    2.1 class, pseudo-classes, attribute  // each +1 to C
    2.1 element, pseudo-element           // each +1 to D  

if  RoolA.Specificity === RoolB.Specifity then

3. Compare order

## Units

%:
    {font-size} from parent's computed font-size
    {lengths: width, height, margin, padding, ...} from parent's computed width
em:
    {font-size} from parent's computed font-size
    {lengths} from current element computed font-size
rem:
    all from root computed font-size
vh, vw:
    from viewport height and width

## Box types

1. Block
    1.1 100% of parent's width
    1.2 vertically, one after another (add line breaks)

2. Inline
    2.1 Occupies only content's space
    2.2 No heights, widths. 
    2.3 Horizontal paddings and margins (except <img>) take away another elements.
        Vertical paddings overlap outer content.
        Verical margins are ignored.

3. Inline-block
    3.1 Occupies only content's space
    3.2 No line-breaks

## Development

// You can make alias for following commands in package.json.

node-sass %input%.scss css/style.css -w // watch and compile scss
live-server // static auto-reload server    

## Colors
    orangered, greenyellow
    tranparent

# Alignment

1. Using flexbox

use margin-right: auto in flex-element, to force its right margin occupies all available space; 

::before and ::after flex-container pseudo elements become flex-items. For example, justify-content: center push them apart.
# Centering

1.
.parent {
    position: relative;
}

.child {
    position: absolute;
    top: 40%; /*% means from parents height*/
    left: 50%;
    transform: translate(-50%, -50%); /*% means from element sizes itself*/
}

2. 

margin: 0 auto;

3. For inline elements (text, img, span, font-icons, etc...)
text-align: center;

# Cheat sheet

## Flexbox

Container:
    - *Main axis direction*
        flex-direcrtion: row, row-reverse, column, column-reverse
    - *Align items along the main axis*
        justify-content: flex-start, flex-end, center, space-between, space-around, space-evenly
    - *Align items along cross axis*
        align-items: stretch, flex-start, flex-end, center, baseline
    - *Align stripes of content along cross axis*
        align-content: stretch, flex-start, flex-end, center, space-between, space-around
    - *What to do if elements creeps out the flex-container*
        flex-wrap: nowrap, wrap, wrap-reverse

Item:
    - Align
        align-self: auto, stretch, flex-start, flex-end, center, baseline
    - Order
        order: 0 | <integer>
    - Width properties
       flex-grow: 0;
       flex-shrink: 1; // if 0, an element is not allowed to shrink
       flex-basis: auto;
       flex: 0 1 auto; // shorthand     


## Grid
% - percentage of parent size (exclude gaps)
1fr - include gaps

0. Terms
Row, column, track, area, cell, gap.
Explicit & implicit grid.

- item - about item
- content - about content
- justify - horizontal alignment
- align - vertical alignment


1. Container:

- justify-items # aligns content horizontally in grid-areas (cells)
- align-items # aligns content vertically in grid-areas (cells)
- justify-content # aligns rows vertically
- align-content # aligns columns horizontally


naming example:
    grid-template-columns: [sidebar-start] 8rem [sidebar-end full-start] 1fr [center-start] repeat(8, [col-start] minmax(min-content, 14rem) [col-end]) [center-end] 1fr [full-end];
then in grid-item:
    grid-column: col-start 2 / col-end 2; # If colunms have the same name, we use numbers to determine

Adaptive number of columns:
    grid-template-columns: repeat(auto-fit, minmax(15rem, 1fr));
    
auto-fill - adds as mush implicit columns as possible    
auto-fit - adds 0 width implicit columns


Adaptive picture-gallary:
    use 'vw' in grid-template-rows. When you scaleX (decrease viewport width), it'll automatically scaleY. That's why you save pictures aspect ratio.


Horizontal alignment.
Use grid-template-columns: max-content; to set with of grid to max-content. After that horizontal alignment (justify-self: center;) would look more consistently.
   
    
2. Item:

::before and ::after item pseudo elements become grid-items.

grid items (as same as flex items) ignore properties: float, display:inline-block/table-cell, vertical-align

# Unsortered

## Designations
1. Box // like a container
2. Form-group // group for button+label or radio-button+label


## Transparency

For transparent elem:
    opacity is inherited (so all subelems'll be transparent), but rgba(..., alpha) is not

## Tips
    outline is better then border in :focus, :active and etc. because it isn't change the size of the elem

## @mixin vs @extend

Mixins add properties separaty in every class. That's why mixin can have paramteres (@include mix(100px))

@Extend add one rule for group of selectors:
    .a, .b, .c {
        /* css-properties */
    }
That's why it can't use properties.    


## Vertical aligning inline/inline-block elements by:
- text-align: center;

## Buttons:
    in/push(half of out): hover, active
    
    skratch for link (<a> </a> button):
    .btn {
        border-radius: 3px;
        box-shadow: 0 1.5rem 4rem rgba($color-black, .15);
        transition: all .2s;
        padding: 1.5rem 2rem; /* x-padding should be bigger then vertical for beauty/*/
        
        &:link,
        &:visited {
    
        }
    
        &.hover {
    
        }
    
        &:active {
            
        }
    }
    
## Images
    - big img require width or height
    - use overflow: hidden in parent element with border-radius to prevent overflowing in corners
    - use line-height: 0 in parent element to prevent smth like "margin-bottom" of image (because image is inline element same as text)

### Responsive images:
    - density swithing: image depends on pixel density (in retina displays 2 physical pixels match 1 in css)
        <img srcset="pic1 1x, pic2 2x" alt="pic">
    - art direction: image depends on viewport size
        <picture>
            <source srcset="pic1 1x, pic2 2x" media=(max-width: **em)>
            <source ... >
            ...
            <-- default -->
            <img srcset="pic1 1x, pic2 2x" alt="pic">
        </picture>
        
        both dpr and direction:
            <img srcset="1.jpg 300w, 1-large.jpg 1000w"
                 alt="Photo 1"
                 sizes="(max-width: 900px) 20vw, (max-width: 600px) 30vw, 300px"
                 class="class"
                 src="img/nat-1-large.jpg">
## Pseudo-elements:
    ::after
        you need to add content and display (the best is inline-block) properties. 
        and may be add height & width. 

## Media query structure:
 Example:
    - Scale: [XS, S, M, L, XL]
    - You default size is M (development size; For example, desktop-first) 
    - Don't forget make parameterized mixin for @media
    
    html {
        font-size: M%;
        
        @media (min-width: XL em) {
            font-size: XL%;
        }
        
        @media (min-width: L em) {
            font-size: L%;
        }
        
        @media (max-width: S em) {
            font-size: S%;
        }
        
        @media (max-width: XS em) {
            font-size: XS%;
        }
    }

        
## Animation:
### Facts
    transition: all .2s; // for duration
    ...
    transform: ...
    
    when use delay:
        to set initial state use animation-fill-mode: backwards;
        
### Bugfixing
    try use backface-visibility: hidden;
    
# Troubleshooting
## Z-index
    only works with position relative:
        position: relative;
        z-index: 5;
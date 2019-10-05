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



# Unsortered

## Designations
1. Box // like a container
2. Form-group // group for button+label or radio-button+label


## Transparency

For transparent elem:
    opacity is inherited (so all subelems'll be transparent), but rgba(..., alpha) is not

## Tips
    outline is better then border in :focus, :active and etc. because it isn't change the size of the elem



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
    
## Pseudo-elements:
    ::after
        you need to add content and display properties
        
## Animation:
### Facts
    transition: all .2s; // for duration
    ...
    transform: ...
    
    when use delay:
        to set initial state use animation-fill-mode: backwards;
        
### Bugfixing
    try use backface-visibility: hidden;
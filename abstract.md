# Cascade

1. Importance:
    1.1 User !important
    1.2 Author !important
    1.3 Author
    1.4 User
    1.5 User agent

if A.Importance === B.Importance, then

2. Specificity: (A, B, C, D)
    2.1 inline styles                     // each +1 to A
    2.1 id                                // each +1 to B  
    2.1 class, pseudo-classes, attribute  // each +1 to C
    2.1 element, pseudo-element           // each +1 to D  


# Centering

.parent {
    position: relative;
}

.child {
    position: absolute;
    top: 40%; /*% means from parent*/
    left: 50%;
    transform: translate(-50%, -50%); /*% means element itself*/
}


# Unsortered

## Vertical aligning inline/inline-block elements by:
- text-align: center;

## Buttons:
    in/push(half of out): hover, active
    
## Pseudo-elements:
    ::after
        you need to add content and display properties
        
## Animation:
    when use delay:
        to set initial state use animation-fill-mode: backwards;
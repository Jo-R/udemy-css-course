# How CSS works: behind the scenes

## The 3 pillars
1. Responsive Design
2. Maintainable and scalable
3. Web performance

## An overview of page load
Load and Parse html > build DOM

Load and parse css (same time as html parse)
    1. resolve conflicting css declartions (cascade)
    2. process final css values e.g. based on device size
        > css object model (cssom)

dom and cssom > render tree > website rendering (visual formatting model)

then webiste is painted to screen

## CSS parsing part 1: cascade and specificity
1. cascade
    * Process of combining different stylesheets and resolving conflicts between different css rules and declarations when more than one rule applies to a certain element (e.g author, user, browser)
    * importance > specificity > source order
2. specificity looks at (* has 0,0,0,0 so all other operators have precendence over it)
    1. inline styles
    2. IDs
    3. classes, pseudo-classes, attributes
    4. elements, pseduo-elements
Rely on specificity more than order...but always put author stylesheet last cf overriding

## CSS parsing part 2: value processing
Every property has a value even if we haven't specified it

All rem, em, vh/w etc are converted to px (computed & used/actual value - final calc based on layout eg parent size) as part of parsing

% fonts - parent's computed font size

% lengths - parent element's **width** used as baseline

em font - x * parent computed font size

em length - x * current element computed font size

rem - same for font/length - x * root computed font size

em and rem are more robust cos based on font size which is relevant to length stuff - change the font size, chenages the length as well based on root

vh and vw (1vh/w = 1% viewport height/width) - useful for hero sections

## CSS parsing part 3: Inheritance
Uses cascade value if there is one but if not looks for inherited values for certain properties (inherits the computed value)

What is inherited?
    * text related (font stuff)

There is an inherit keyword to force inheritance

Initial keyword to reset property to initial value

## Converting px to rem: an effective workflow
set html font-size to 10 and then easy to calculate rems...but if do that overrides user default...

so...set html font size as 62.5% and it will be 10 generally but relative is user has overriden browser

## How CSS renders a website: the visual formatting model
Is an algo that calculates boxes and determines the layout of these boxes for each element in the render tree in order to determine the final layout of the page

## CSS architecture, components & BEM
1. Think
    * Modular building blocks to make up interfaces - reusable and independent (i.e. not dependent on parent)
2. Build
    * Block Element Modifier (BEM) .block__element--modifier
        - block = stand-alone component that is meaningful on its own
        - element = part of a block with no meaning on its own
        - modifier = to make a different version of an element
3. Architect
    * Logical folder and file structure
        - e.g. 7-1 pattern


## media queries
max-width desktop first (because we want the media query stuff to leave desktop code alone)

min-width mobile first (because we want the stuff in the media queries to leave our mobile design alone)

media queries override specific parts of css for specific widths (ofc)

eg so 500px...
both max-width 600px and max-width 900px will apply 
code order is what matters for overriding with media queries and this is why we put them at the end

## breakpoints
bad - use width of a few popular devices: optimising for specific devices, not future proof

good - look at all most used device widths and group them -> breakpoints between similar device widths

perfect - ignore devices, look at content - when does the design break on resize? that's your breakpoint...this is a difficult way of doing it tho!

we're gonna use the good way in the course...

do one for: phone (max width 600px), portrait tablet (up to 900px), landscape tablet (up to 1200) and desktop (norml up to 1800px and then more for biiig desktop)
























        


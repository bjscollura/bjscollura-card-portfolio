Theme Picker: 
    - fix a few coloring issues with the themes. And add 1 more theme?
    - remove / decide on Tangerine and other extra Google fonts
    - resize social and theme buttons/links to minimum 40x40px
    - add local cookie to remember theme setting, at least between page loads

Projects: 
    - complete and add a few development sideprojects under Projects
    - import images into the right places
    - reformat html and remove extraneous class names
Add basic css to project components
    - line height static, and use rlh units to size spaces between text (vertical rhythm)
    - ^^ How to do this without setting lineheight on html element, without being global?

Change multiple +page.svelte files for each Project --> create a component that calls @html into the right place
 - this would allow the component to be the place where the css lived, using "div :global()" to scope to the @html markup
 - may need variations on the component if UX vs Code projects are different in how they're presented
 

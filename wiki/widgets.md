Widgets
=======


## Hatch

full automatic wrapper for widgets
- forwards attibutes to widget (interface.mjs)
- exposes events from widget (exports.mjs)

## Web Embedded Widget

Can be included in arbitrary web pages

Communication between outer (embedded) widget and inner widget 
- resize
- expose inner attributes
- expose inner events
    --> exports.mjs
- forward outer attributes to inner
- expose methods from inner 
- forward document 'click' to inner 

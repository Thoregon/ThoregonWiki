# get rid of index.reliant.mjs

there exists different startup code for node and browser modules.
node: index.mjs
browser: index.reliant.mjs

if no 'index.reliant.mjs' exists, browser also uses index.mjs

make browser/node dependencies indirect and move to another config.

## Reliant redirects

- evolux.universe
- evolux.everblack
- evolux.dyncomponents

# Aurora Element Lifecycle

- async/event driven

## Architecture

- AuroraElement (CustomElement)
    - ThemeBehavior
- AuroraContent
- AuroraDynamicContent
    - just creates a shadow dom w/o style with just a <div> as container
    - local template
    - app view

- ViewModelPresenter
    - View
- ViewModel (local BusinessObject)

## Lifecycle

Statemodel
- AuroraElement
    - void -'create'-> created -'renderStatic'-> static rendered -'rendered'-> exists
    - 'exist' -'renderDynamic'-> exists
- ViewModelPresenter
    - void -'create'-> created
    - created    

- create AuroraElement
    - add to DOM
    - static render
        - there must be no need to react on changes of element attributes to render content
        - attribute changes may be suitable for structural behavior like 'disabled' or 'visible' 
        - if the element can't be rendered at all, it displays a 'proxy'
    - implement dynamic render if necessary
-> render when visible

- create ViewModel  
    

- refresh AuroraElement
    - collect and keep Placeholders
    - after rerender of template check which palceholders remains
    - replace? the remaining placeholders
        - tell each placeholder to (re)render dynamic


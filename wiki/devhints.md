Dev Hints
=========

Debugger Console with formats:
--> https://developer.mozilla.org/de/docs/Web/API/Console#outputting_text_to_the_console
  %c inserts CSS formats
console.log(
    '%cLike looking under the hood? We’re hiring people like you! Come and work for us: https://www.mixcloud.com/jobs/',
    'color: #4fa6d3;font:18px/80px "DM Sans", sans-serif;'
);

    Element.scrollIntoView()
    Window.scrollTo()

## SSH (permission denied)

Add to client ~/.ssh/config:

PubkeyAcceptedKeyTypes +ssh-rsa


## Element Visibility

        this.observer = new IntersectionObserver((entries, observer) => {
            if (entries.length === 0) return ;
            const entry = entries[0];
            if (!entry.isIntersecting) return ;
            // console.log("cropper visible");
        }, {
            root: this.container,
            rootMargin: '0px',
            threshold: 1.0
        } );

        this.observer.observe(elem);

! avoid 'unload' and 'beforeunload' 
    --> https://developer.mozilla.org/en-US/docs/Web/API/Navigator/sendBeacon
    --> https://developer.mozilla.org/en-US/docs/Web/API/Document/visibilitychange_event#examples

### CSS Features

- [scroll-behavior](https://developer.mozilla.org/de/docs/Web/CSS/scroll-behavior)
- [Scroll Snapping](https://css-tricks.com/practical-css-scroll-snapping/)

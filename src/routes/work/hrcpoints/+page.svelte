<h1>
    Loyalty / Membership App: House Rules Club
</h1>

<img class="w-full" src="/src/assets/hrcpoints.jpeg"/>

<h2>Intro</h2>

<p>
    The purpose of this app is to allow customers of a board game cafe to collect and use points, credits, or other units such as a free drink or game hour. I had full control over the decisions of which techstack to use, where to host, and any other technical decisions.
</p>

<h2>Tech Stack</h2>

<h3>Framework</h3>

<p>
    I decided to build this app as a "Progressive Web Application" PWA, so that we could roll out new features, fix bugs, or change the UI without forcing users to update the app. Another benefit of utilizing PWA technologies was that was it was cross platform between iPhone and Android users. Admin users could also access the same app using a browser on a laptop or tablet, by going to a protected URL.
</p>

<p>
    The using Svelte as the front-end framework. Naturally, SvelteKit was the obvious choice for the backend. It wasn't so obvious when I started this project. In the beginning, I had written API endpoints in NodeJS + Express, and only used Svelte for the frontend.
</p>

<p>
    PWA's are not without its own problems. Firstly, on iOS, the "Add to Home screen" option - the way PWA's are installed - is only available on Safari, whereas Android users may use Chrome other browsers to install the app. That means some code may not work on both platforms, or even older browsers that do not support the newer APIs and javascript features. I ran into this problem when I was testing the app on the cafe's POS tablet. It was an Android tablet running an older version of Google Chrome. SvelteKit did not support this older version of Chrome and some javascript enhancements did not work as expected.
</p>

<p>
    Another problem I ran into was that a customer did not have the "Add to Homescreen." They ended up simply using the browser without installing.
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

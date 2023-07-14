<h2>
    Loyalty / Membership App: House Rules Club
</h2>

    <img class="w-full" src="/src/assets/hrcpoints.jpeg"/>

<h3>Intro</h3>

<p>
    The purpose of this app is to allow customers of a board game cafe to collect and use points, credits, or other units such as a free drink or game hour. I had full control over the decisions of which techstack to use, where to host, and any other technical decisions.
</p>

<h3>Tech Stack</h3>

<h3>Framework: Svelte</h3>

<p>
    I decided to build this app as a PWA, so that we could roll out new features, fix bugs, or completely change the frontend UI without forcing users to update the app. Another benefit of utilizing PWA technologies was that was it was cross platform between iPhone and Android users. Admin users could also access the same app using a browser on a laptop or tablet, by going to a protected URL.
</p>

<p>
    PWA's are not without its own problems. Firstly, on iOS, the "Add to Home screen" option - the way PWA's are installed - is only available on Safari, whereas Android users may use Chrome other browsers to install the app. That means some code may not work on both platforms, or even older browsers that do not support the newer APIs and javascript features. I ran into this problem when I was testing the app on the cafe's POS tablet. It was an Android tablet running an older version of Google Chrome. SvelteKit did not support this older version of Chrome and some javascript enhancements did not work as expected.
</p>

<p>
    Another problem I ran into was that a customer did not have the "Add to Homescreen." They ended up simply using the browser without installing.
</p>

    <h3>Authentication</h3>
<p>
    A customer also had a problem with Google Sign-in 2FA. Could be solved by providing alternate sign-in options.
</p>

<p>
    The using Svelte as the front-end framework. Naturally, SvelteKit was the obvious choice for the backend. It wasn't so obvious when I started this project. In the beginning, I had written API endpoints in NodeJS + Express, and only used Svelte for the frontend.
</p>

<h3>Pros and Cons of current approach</h3>

<h3>Alternative ways</h3>

Flutter.
React Native or similar.
Native for both ios and android.

<h3>How it turned out</h3>

<h3>What would I change</h3>

Maybe try hosting myself on DO. Use Postres service from vercel.

<h3>tech stack and why.</h3>
<h3>pros and cons.</h3>
<h3>user pain points after launch.</h3>
<h3>google sign in, why google.</h3>
Because facebook banned.
<h3>vercel and why.</h3>
Free tier is enough to run in production. Planetscale free tier was also enough for production.


<style>
    p {
        @apply mb-4;
    }
</style>

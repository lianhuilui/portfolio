<h1>
    Galaxy 10 MM
</h1>

<img class="w-full" src="/src/assets/galaxy10mm.jpg"/>

<h2>Intro</h2>

<p>
    The purpose of this game was to drive engagement and increase awareness of client's product. Instead of being a static post about their new product, they went with an interactive mini-game where anyone can participate and win real prizes. A user simply chooses their passion and the game will generate a photo with a random phrase. The user can share or re-generate to get a new result.
</p>

<h3>Features</h3>

<ul style="padding-left: 18px; list-style-type: circle;">
    <li>Generate all combinations of text and images (baking text onto images) ahead of time, for QA and consistency</li>
    <li>Collect participant's contact details for lucky draw program</li>
    <li>Must be able to handle spike in traffic without any downtime</li>
</ul>

<h2>Tech Stack</h2>

<p>
    I went with GCP's Cloud Function running a nodeJS server backed by GCP's Cloud SQL. I went with Google Cloud Platform for their near zero downtime service provider agreement.
</p>

<h4>Some Hiccups</h4>

<p>
    To generate the combinations of text and images, I had a JS script using HTMLCanvas to add text to the images. However, the image quality and style changed from browser to browser and OS to OS. The best results were on MacOS running firebox (iirc)
</p>

<style>
    p {
        @apply mb-4;
    }
</style>

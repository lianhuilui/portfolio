<h2>Lucky Draw</h2>

<img class="w-full" src="/src/assets/berinaluckydraw.png" />

<h2>
    Intro
</h2>

<p>
    The client needed to run a marketing campaign, where customers who purchase a certain product within the marketing period will receive a QR code in the box. By scanning the code, the customer can register to be part of a lucky draw and win prizes. The prizes are different amounts of phone credits which the customer may win immediately after registration, upon which the client's staff will confirm and manually credit the winning value to the customer's phone number.
</p>

<h2>Features</h2>

<p>
    Some important features were discussed and implemented, some of which are:
</p>

<h3>Anti-brute-force attack</h3>


<p>
The codes were numerical codes, which could not be too long. If a customer had a problem, they would have to call custoemr service verbally say the number on the phone, therefore a number length of only 8 was used.
</p>

<h4>Utilities</h4>
<ul style="list-style: bullet; padding-left: 18px;">
    <li>Generate & Print unique QR codes</li>
    <li>Allow admin</li>
    <li>Randomly select prizes upon user scanning the QR code</li>
    <li>Prize probability distributed by order of scan, instead of being locked to a code</li>
</ul>

<h2>Technologies used</h2>

<ul>
    <li>Google Cloud Platform - hosting and database</li>
    <li>NodeJS - server code</li>
</ul>

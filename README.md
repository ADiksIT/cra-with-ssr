# SSR. Pros and cons.
SSR stands for Server Side Rendering. SSR is a technique for rendering app on the server and then sending a fully rendered page to the client.
Two main benefits of SSR are performance benefit and SEO optimization.
Lets go to details.

## Performance benefit.
Difference beetween SSR and CSR (client-side rendering):

![SSR](https://cdn-images-1.medium.com/max/800/1*jJkEQpgZ8waQ5P-W5lhxuQ.png)
![CSR](https://cdn-images-1.medium.com/max/800/1*CRiH0hUGoS3aoZaIY4H2yg.png)

For SSR we have rendered html with links to scripts in browser. For CSR case we have only links to scripts. It means that user will see some content faster with SSR scenario. The initial page load is faster.
But it is theoretical performance benefit because SSR work speed affects from internet speed of the user making the request, physical location of server and count of users which are trying to access the site.

## SEO optimization.
One of benefit of using SSR is in having an app that can be crawled for its content even for crawlers that don’t execute JavaScript code. This can help with SEO and with providing meta data to social media channels.

Page source for start page of create-react-app:

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="utf-8" />
    <link rel="shortcut icon" href="/favicon.ico" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <meta name="theme-color" content="#000000" />
    <!--
manifest.json provides metadata used when your web app is installed on a
user's mobile device or desktop. See https://developers.google.com/web/fundamentals/web-app-manifest/
-->
    <link rel="manifest" href="/manifest.json" />
    <!--
Notice the use of in the tags above.
It will be replaced with the URL of the `public` folder during the build.
Only files inside the `public` folder can be referenced from the HTML.

Unlike "/favicon.ico" or "favicon.ico", "/favicon.ico" will
work correctly both with client-side routing and a non-root public URL.
Learn how to configure a non-root public URL by running `npm run build`.
-->
    <title>React App</title>
</head>

<body>
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="root"></div>
    <!--
This HTML file is a template.
If you open it directly in the browser, you will see an empty page.

You can add webfonts, meta tags, or analytics to this file.
The build step will place the bundled scripts into the <body> tag.

To begin the development, run `npm start` or `yarn start`.
To create a production bundle, use `npm run build` or `yarn build`.
-->
    <script src="/static/js/bundle.js"></script>
    <script src="/static/js/0.chunk.js"></script>
    <script src="/static/js/main.chunk.js"></script>
</body>

</html>
```

And the page source for the same page with ssr:
```html
<!doctype html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no" />
    <title>Simple weather app</title>
    <link href="index.css" rel="stylesheet" />
    <link href="2.css" rel="stylesheet" />
</head>

<body>
    <div id="root">
        <div class="App">
            <header class="App-header"><img src="data:image/svg+xml;base64,..." class="App-logo" alt="logo" />
                <p>Edit <code>src/App.js</code> and save to reload.</p><a class="App-link" href="https://reactjs.org" target="_blank" rel="noopener noreferrer">Learn React</a></header>
        </div>
    </div>
    <script src="index.js"></script>
    <script src="start-page.chunk.js"></script>
</body>

</html>
```
As we can see in first snippet we have only links to scripts in the body tag and in second snippet we see rendered html and links to scripts. Second scenario is good for SEO bot, it can read context of page. 

## SSR cons.
SSR is not silver bullet for all use cases. Major cons of SSR are frequent server requests and full page reloads.

In conclusion, this is quote of Adam Zerner:
>SSR is analogous to you driving over to the supermarket every time you want to eat.
With client-side rendering, you go to the supermarket once and spend 45 minutes walking around buying a bunch of food for the month. Then, whenever you want to eat, you just open the fridge.


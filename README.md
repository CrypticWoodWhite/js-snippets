# js-snippets
A collection of various javascript plugins, functions, and whatnot, that do not deserve their own repository.

## Table of Contents

- [htmlEngine](#htmlEngine)
- [zipUrls](#zipUrls)
- [getBase64](#getBase64)

## htmlEngine

This is a simple HTML view engine for Express to be used where EJS or Jade or another such engine is overkill. To get started, download and include the `htmlEngine.js` file in your server.js file:

``` javascript
app.engine("html", require("./plugins/htmlEngine"));
app.set("view engine", "html");
```

## zipUrls

This is a utility that downloads files from a given array of URLs, and streams those files into a zip file. A CSV file is also streamed into that zip file. To use this plugin, first download the `zipURLs.js` file, then include it in your project:

``` javascript
let zipURLs = require("./plugins/zipURLs");
```

Install the dependencies:

```bash
npm install async request archiver
```

Call the function with an array of URLs and a CSV file as arguments:

``` javascript
let zipFile = zipURLs(arrUrls, csvFile);
```

Finally, set your headers and pipe the file to your client:

``` javascript
res.setHeader("Content-disposition", "attachment; filename=nameOfTheZipFile.zip");
res.setHeader("Content-Type", "application/zip, application/octet-stream");
res.status(200);
zipFile.pipe(res);
```

## getBase64

This function converts an image file to Base64 string data. To use, first download and require the `getBase64.js` file, then pass in the image file.

``` javascript
let getBase64 = ("./plugin/getBase64");
let img64 = getBase64(imageFile);
```
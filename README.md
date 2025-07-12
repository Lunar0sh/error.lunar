# Modern & Aggressive Error Pages

A complete, themed, and easily expandable suite of error pages for web servers. This project provides a consistent "Lunar" theme with an aggressive tone for all standard (and some non-standard) HTTP status codes.

---

## Features

* **Complete Set**: Covers all major `1xx`, `2xx`, `3xx`, `4xx`, and `5xx` status codes.
* **Custom Codes**: Includes non-standard `6xx` codes for specific use cases like content theft and connection blacklisting.
* **Aggressive Tone**: All messages are written with a sharp, direct, and unapologetic tone.
* **Themed Design**: A modern, dark "Lunar" theme with an animated starfield background is applied to all pages.
* **Easy Expansion**: Adding new error pages is as simple as creating one new file and adding a single line to a JSON manifest.
* **Dynamic Preview**: A `preview.html` file automatically fetches and displays all available error pages from the manifest.
* **Simple API**: A clear URL structure allows for easy fetching of error pages for use in other applications.

---

## API Usage

You can fetch these error pages programmatically.

* **Get All Errors**: `GET /errors/manifest.json`
    * Returns a JSON list of all available error pages.

* **Get Specific Error**: `GET /errors/{code}.html`
    * Returns the full HTML of the specified error page.

#### Example Fetch:
```javascript
// Get the HTML for the 503 error page
fetch('[https://error.lunar-sh.de/errors/503.html](https://error.lunar-sh.de/errors/503.html)')
  .then(response => response.text())
  .then(html => {
    // Inject the HTML into your document
    document.body.innerHTML = html;
  });
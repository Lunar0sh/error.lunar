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

## File Structure
```
The project uses a simple and clean file structure.
/
|-- css/
|   |-- style.css
|-- errors/
|   |-- 100.html
|   |-- ... (all other error files) ...
|   |-- 601.html
|   |-- manifest.json  <-- IMPORTANT: The error directory
|-- index.html
|-- preview.html
|-- README.md
```
---
## How to Use

1.  Place all files on your web server.
2.  Configure your server (e.g., Apache `.htaccess` or Nginx `nginx.conf`) to use these files for their corresponding HTTP status codes.
3.  Navigate to `preview.html` to see a menu of all available error pages.

### Adding a New Error Page

The system is designed to be easy to modify.

1.  **Create the HTML file**: Copy any existing error page in the `errors/` directory and rename it to your new code (e.g., `errors/603.html`). Modify the `<h1>`, `<h2>`, and `<p>` tags inside.
2.  **Update the Manifest**: Open `errors/manifest.json` and add an entry for your new page. This is the **only step** needed to make it appear in the `preview.html` menu.

    ```json
    // errors/manifest.json

    {
      "errors": [
        // ... all other entries
        { "code": 602, "name": "Connection Blacklisted" },
        { "code": 603, "name": "New Custom Error" } // <-- Add your new line here
      ]
    }
    ```

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
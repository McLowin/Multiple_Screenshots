![Extension logo](icons/logo.png)

**MultipleScreenshots** is a versatile Chrome extension designed to streamline the process of capturing screenshots from multiple URLs effortlessly. With this extension, users can paste a list of URLs, and MultipleScreenshots will open each one, take a screenshot, and save it according to your specified preferences.

<img width="631" height="888" alt="image" src="https://github.com/user-attachments/assets/f4462ef0-4b20-423f-a7a8-39f6e487be67" />

---

## Key Features

- **Window Mode**: Open the extension in a dedicated window instead of a popup bubble for more stability and workspace.
- **Auto Capture**: Take screenshots at regular intervals to monitor pages and track changes over time.
- **Customizable Delay**: Set a delay (in seconds) before capturing screenshots to ensure pages load fully.
- **Flexible File Names**: Specify custom file names or use default naming conventions.
- **Multiple Screenshot Formats**: Save screenshots in PNG, JPG, PDF, or GIF formats.
- **Path Column in CSV**: Add an optional column in the CSV to specify the full file path for easier organization.
- **URL & Timestamp Overlay**: Add a URL and timestamp overlay to your screenshots for reference.
- **Full-Screen Mode**: Take screenshots in full-screen mode for better visibility.
- **Full-Page Mode**: Take screenshots of full page.
- **Clip to XPath**: Crop screenshots to a specific element by providing its XPath.
- **Visual XPath Picker Tool**: Click a button to visually select an element on a webpage. The extension captures its XPath and makes it available for cropping screenshots.
- **CSV Generation**: Automatically create a CSV file mapping URLs to their corresponding filenames.
- **API Upload**: Alternative to local file saving — send screenshots directly to your configured API endpoint (JSON base64 or multipart/form-data).

---

## Installation

1. Go to the Chrome Web Store page for **Multiple Screenshots**:
   [Multiple Screenshots](https://chromewebstore.google.com/detail/multiplescreenshots/gbgeckhegkbgdlfpcgjdhdckdfcimmbc).
2. Click **Add to Chrome** to install the extension.

---

## Feature Guide

### 1. Window Mode

<p>Enable Window Mode to open the extension in a dedicated standalone window instead of the default small popup bubble.  
This gives you more space, stability and comfort — especially useful when working with long URL lists or advanced settings.  
Once enabled, clicking the extension icon will always focus the existing window instead of opening a new one, ensuring a clean and consistent workflow.  

<img width="631" height="83" alt="image" src="https://github.com/user-attachments/assets/bffd29f4-b79c-4879-b906-77c3e6ef812a" />

### 2. Auto-capture

<p>Enable the auto-capture switch to run screenshots on a recurring schedule.  
You can define the interval (in minutes), and the extension will automatically revisit the given URLs, capture updated screenshots, and repeat the process continuously.  
This makes it possible to use the extension as a simple monitoring tool — checking selected pages at regular intervals to track updates or detect changes over time.  
Auto Capture can be combined with all other features, such as full-page mode, overlays or API upload — so screenshots can be saved locally or sent directly to your endpoint on every cycle.  
The process can be stopped instantly at any moment with the STOP button.</p>

<img width="634" height="61" alt="image" src="https://github.com/user-attachments/assets/cd1d28d7-7230-497e-8bc2-693c2de764bc" />
<img width="634" height="61" alt="image" src="https://github.com/user-attachments/assets/b3158915-da19-4539-89e7-bbdf4f6b7fe0" />

### 3. Delay

<p>Set the delay (in seconds) before capturing each screenshot. Useful for pages that take longer to load.</p>

![image](https://github.com/user-attachments/assets/8ba75050-5d9d-4de1-aac5-70cf888dea90)

### 4. Custom Names

#### a) URL as filename
<p>Use the full URL (hostname + path) as the filename for easy identification.</p>

#### b) Domain as filename
<p>Generate filenames based solely on the URL domain to simplify file organization.</p>

#### c) Custom name
<p>Enter your custom filename prefix, which will be applied to all screenshots.</p>

![image](https://github.com/user-attachments/assets/85fbdd66-2f22-44e4-896d-da608f6f5ee1)

---

### 5. Fullscreen

<p>Enable this option to capture screenshots in Chrome's fullscreen mode (F11), ensuring cleaner visuals.</p>

### 6. Fullpage

<p>Activate this option to capture the entire webpage content, including parts not visible on screen. This feature automatically scrolls through the page to capture all content.</p>

### 7. URL & Timestamp Overlay

<p>Add the webpage URL and timestamp directly to the screenshot image, useful for documentation or audits.</p>

![image](https://github.com/user-attachments/assets/bef0017b-2a69-4bf3-a481-65fbda64b4fc)

### 8. Formats

<p>Select one or multiple screenshot output formats: PNG, JPG, PDF, or WEBP.</p>

### 9. Path (Settings Tab)

<p>Specify a custom path for your screenshot downloads in the <strong>Settings</strong> tab. Remember, this path should match Chrome’s download directory. It only adds the path text itself and connects it to the file name in the generated csv. If we provide the same path that we have set in Chrome Downloads, it makes it easier to create file paths and the entire analysis.
 </p>

<img width="631" height="858" alt="image" src="https://github.com/user-attachments/assets/b313cc26-01cb-4f47-b1eb-0bc4c356c912" />

<img width="632" height="860" alt="image" src="https://github.com/user-attachments/assets/9ffefc76-1dec-47a1-b2c8-cfe10d0ae490" />

![image](https://github.com/user-attachments/assets/a49801ff-4ecd-4254-b942-740d8acbebf0)

### 10. API Upload
<p>Instead of saving screenshots only as local files, you can switch the upload mode to <strong>API Upload</strong>.  
With this option enabled, every screenshot is sent directly to your configured API endpoint, allowing seamless integration with your backend systems, monitoring pipelines or CI/CD workflows.  
This makes the extension flexible — it can either act as a local screenshot tool or as part of an automated server-side process.</p>

#### Modes
API Upload supports two transmission formats, so you can adapt it to your server’s expectations:

   a) **JSON (base64-encoded image)**  
   - The screenshot is converted into base64 and sent in a JSON object.  
   - Example request:
     ```http
     POST /upload HTTP/1.1
     Content-Type: application/json

     {
       "filename": "screenshot_2025-08-21.png",
       "data": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA..."
     }
     ```
   - This format is simple to handle and works well for APIs that expect structured JSON input.
     
   <img width="632" height="241" alt="image" src="https://github.com/user-attachments/assets/3209efc1-1c6b-425b-8fbd-dd7877ec6e05" />

   b) **Multipart/form-data (file upload)**  
   - The screenshot is sent as a binary file in a multipart form, similar to how browsers upload files in HTML forms.  
   - Example request:
     ```http
     POST /upload HTTP/1.1
     Content-Type: multipart/form-data; boundary=---boundary

     -----boundary
     Content-Disposition: form-data; name="file"; filename="screenshot_2025-08-21.png"
     Content-Type: image/png

     ...binary PNG data...
     -----boundary--
     ```
   - This option is ideal when integrating with existing file upload endpoints or storage services.
     
   <img width="633" height="239" alt="image" src="https://github.com/user-attachments/assets/9a7f3aba-a2d6-4533-902e-2875e20e25d2" />

#### Example Endpoint Specification
- **Endpoint**: `https://example.com/api/upload`  
- **Methods**: `POST`  
- **Accepted Content-Types**:  
  - `application/json` (for JSON base64 mode)  
  - `multipart/form-data` (for file upload mode)  
- **Request Fields**:  
  - `filename` → string (name of the file, required)  
  - `data` → string (base64-encoded image, required in JSON mode)  
  - `file` → file binary (required in multipart mode)  
- **Response** (example):
  ```json
  {
    "status": "success",
    "url": "https://example.com/screenshots/screenshot_2025-08-21.png"
  }

### 11. XPath Settings
In the Settings tab, you can:
- Manually enter an XPath and save it with a label for future use.
- Use the Select XPath Manually button to visually pick an element on the currently active page — the XPath will be auto-filled and can be saved with a custom name.

![image](https://github.com/user-attachments/assets/05282949-9bcb-4771-9d28-28813fdf0076)
  
### 12. XPath Picker Tool

The Select XPath Manually button allows you to visually select any element on the open webpage:
- Hover will highlight elements.
- Click to select — the XPath is automatically retrieved.
- A confirmation alert appears, and the XPath is auto-filled back into the extension interface (even after reopening).
- You can then save it under a custom label for repeated use.

![image](https://github.com/user-attachments/assets/2deec07f-1e41-4e06-8857-28bc51c311a6)
  
### 13. Clip image to XPath (Crop Screenshot to Element)

Use this feature to crop the screenshot to a specific part of the page by:
- Selecting a saved XPath from the dropdown.

Enable the "Clip image to XPath" checkbox. The extension will attempt to crop the screenshot to the selected element.
- If the XPath exists on the page, the screenshot will be cropped precisely.
- If the XPath is not found, a normal screenshot will be taken instead as fallback.

### 14. Highlight element on screenshot (Highlight element by xpath)

Use this feature to highlight chosen element on screenshot:
- Selecting a saved XPath from the dropdown.

Enable the "Highlight element by xpath" checkbox. The extension will attempt to scroll into chosen element by xpath and make the screenshot with framed selected element.
- If the XPath exists on the page, the screenshot will frame element precisely.
- If the XPath is not found, a normal screenshot will be taken instead as fallback.

![image](https://github.com/user-attachments/assets/c85ff0cf-150b-4b96-bd6b-95397b87d1a6)

### 15. Generate CSV
<p>Automatically create a CSV file mapping each URL to its screenshot filename and optionally the full file path, ideal for batch processing and record keeping.</p>

---

## License

This project is licensed under the [Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License](LICENSE).

---

## Creator
For inquiries or feedback, please contact me at [kontakt@wentago.pl].

---

## Support & Donations

If you find **MultipleScreenshots** helpful, please consider supporting its development by making a donation. Your support helps keep the coffee flowing and the updates coming! ☕

<a href="https://buymeacoffee.com/skolmowski" target="_blank">
  <img src="icons/bmc-button.png" alt="Buy Me a Coffee" style="width: 150px; height: auto;">
</a>

---

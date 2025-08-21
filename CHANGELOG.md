# Changelog

This file contains a record of updates and changes made to the MultipleScreenshots Chrome extension.

## [0.2.0] - 2025-08-21
### Added
- **Window Mode**: Open the extension in a dedicated standalone window instead of a small popup bubble.  
  Provides more workspace and stability when managing long URL lists or advanced settings.  
  Clicking the extension icon now focuses the existing window instead of opening duplicates.
- **Auto Capture**: Schedule screenshots at regular intervals.  
  Makes it possible to monitor websites continuously, track changes over time, and combine with all other features (e.g. API Upload, full-page mode).  
  Includes instant STOP button for full control.
- **API Upload**: Alternative to local saving.  
  Screenshots can now be sent directly to a configured API endpoint, in either:
  - **JSON mode** (base64 inside JSON payload)  
  - **Multipart/form-data mode** (binary file upload).  
  Allows direct integration with backends, monitoring tools, or automated workflows.
### Fixed
- Improved **fullpage screenshots**: smoother scrolling, extra wait time for dynamic content, and no duplicated sections.

## [0.1.7] - 2025-05-17
### Added
- **New features notifications system**
- **Highlight element by XPath**: You can now highlight elements in your screenshots using a saved XPath. The extension will automatically scroll to the element on the page and draw a red frame around it — no cropping required. If the XPath is not found on a given page, a regular screenshot will be taken instead - so the workflow stays smooth.

## [0.1.6] - 2025-05-02
### Fixed
- Fixed small bugs.

## [0.1.5] - 2025-04-09
### Fixed
- **Domain opening bug**: Fixed bug with opening only domains.

## [0.1.4] - 2025-04-05
### Added
- **Clip Screenshots to Element by XPath**: Precisely crop screenshots to just the part of the page you need by selecting or saving XPath targets.
- **XPath Selector Tool**: New interactive tool lets users visually select elements on a webpage. The corresponding XPath is saved and ready to use for cropped screenshots.

## [0.1.3] – 2025-03-11
### Added
- **Fullpage screenshots**: Capture the entire webpage, including content not visible on the screen, by automatically scrolling.
- **Filename options**:
  - Use the full URL as the filename.
  - Use the domain as the filename.
  - Custom filenames.

## [0.1.2] - 2025-01-26
### Added
- WebP format support: Replaced GIF with WebP, providing better image quality and smaller file sizes.
- Optional **path** column in CSV: Allows users to include full file paths in the CSV for better file organization.
- URL and timestamp overlay: Users can now overlay the URL and timestamp directly onto the screenshots.

### Fixed
- JPG saving issue: Resolved a bug where JPG files were saved as PNG. JPG conversion now works correctly.

## [0.1.1] - 2024-12-23
### Added
- Full-screen mode option for taking screenshots: added for users who prioritize capturing screenshots at full resolution or with complete page coverage. This feature replicates the effect of manually entering full-screen mode (F11) in browser during screenshot capture.

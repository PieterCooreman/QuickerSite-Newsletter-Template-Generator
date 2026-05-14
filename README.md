# QuickerSite Newsletter Template Generator

A lightweight, standalone web tool designed to generate responsive, 100% table-based HTML email templates optimized for the legacy **QuickerSite webCMS**.

## 🚀 Features

* **Legacy Compatible:** Outputs deeply nested tables and inline CSS. Avoids `<head>` and `<body>` tags to seamlessly integrate with QuickerSite's rendering engine.
* **Mobile Responsive:** Employs a fluid `max-width` approach and injected `<style>` media queries to ensure templates look professional on both desktop clients (like Outlook) and mobile devices (like Gmail/iOS Mail).
* **Native Tag Support:** Pre-configured with QuickerSite shortcodes like `[NL_NAME]` and properly formats standalone tags like `[NL_UNSUBSCRIBELINK]`.
* **Randomized Designs:** Generates unique templates using predefined color schemes, layouts, and high-quality placeholder images from Unsplash.
* **One-Click Copy:** Instantly copies the raw HTML code to your clipboard, ready to paste into the QuickerSite Newsletter Manager.
* **Zero Dependencies:** The generator runs entirely in the browser using Vanilla JavaScript and Bootstrap 5 for the UI. No build steps or server required.

## 📋 Usage

1.  Download or clone this repository to your local machine.
2.  Open the `index.html` file in any modern web browser.
3.  Click the **"Generate Random Template"** button to cycle through different designs.
4.  Preview the template in the live view (which simulates a 600px mobile/desktop environment).
5.  Click the **"Copy HTML Code"** button.
6.  Paste the code directly into the source view of your QuickerSite Newsletter module.

## 📧 Email Client Compatibility

The generated templates have been structured to ensure maximum compatibility across:

* Microsoft Outlook (Legacy & Office 365)
* Gmail (Web & Mobile Apps)
* Apple Mail (Mac & iOS)
* Yahoo! Mail
* Hotmail / Outlook.com

## 🛠️ Customization

You can easily modify the generator's outputs by editing the arrays at the top of the `<script>` tag in `index.html`:
* `colorSchemes`: Adjust background, text, header, and accent colors.
* `unsplashImages`: Provide your own default header images.
* `headlines` & `loremParagraphs`: Change the default filler text.

---
*Built for legacy software preservation and robust email compatibility.*

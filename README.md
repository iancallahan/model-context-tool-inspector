# WebMCP - Model Context Tool Inspector

A Chrome Extension that allows developers to inspect, monitor, and execute WebMCP tools manually or with Gemini.

## Prerequisites

**Important:**  You must enable the "WebMCP for testing" flag in `chrome://flags` to turn it on in Chrome 150.0.7861.0 or higher.

## Installation

You can install this extension either directly from the Chrome Web Store or manually from the source code.

### Option 1: Chrome Web Store (recommended)

Install the extension directly via the [Chrome Web Store](https://chromewebstore.google.com/detail/model-context-tool-inspec/gbpdfapgefenggkahomfgkhfehlcenpd).

### Option 2: Install from source

1.  **Download the Source:**
    Clone this repository or download the source files into a directory.

2.  **Install dependencies:**
    In the directory, run `npm install`.

3.  **Open Chrome Extensions:**
    Navigate to `chrome://extensions/` in your browser address bar.

4.  **Enable Developer Mode:**
    Toggle the **Developer mode** switch in the top right corner of the Extensions page.

5.  **Load Unpacked:**
    Click the **Load unpacked** button that appears in the top left. Select the directory containing `manifest.json` (the folder where you saved the files).

## Usage

1.  **Navigate to a Page:**
    Open a web page that exposes Model Context tools.

2.  **Open the Inspector:**
    Click the extension's action icon (the puzzle piece or pinned icon) in the Chrome toolbar. This will open the **Side Panel**.

3.  **Inspect Tools:**
    * The extension will inject a content script to query the page.
    * A table will appear listing all available tools found on the page.

4.  **Execute a Tool:**
    * **Tool:** Select the desired tool from the dropdown menu.
    * **Input Arguments:** Enter the arguments for the tool in the text area.
        * *Note:* The input must be valid JSON (e.g., `{"text": "hello world"}`).
    * Click **Execute Tool**.

## Configuration

When installing from source, you can create a `.env.json` file next to `manifest.json` to preconfigure the extension:

```json
{
  "apiKey": "your-gemini-api-key",
  "model": "gemini-3.6-flash",
  "baseUrl": "https://your-proxy.example.com/gemini"
}
```

`baseUrl` is optional. Set it to route Gemini API requests through a proxy or API gateway instead of `generativelanguage.googleapis.com`. Omit the API version (for example `/v1beta`) because the Gemini SDK appends it. Voice input uses the Gemini Live API over a WebSocket at `<baseUrl>/ws/...`, so it works only if your proxy also forwards WebSocket connections.

## Disclaimer

This is not an officially supported Google product. This project is not
eligible for the [Google Open Source Software Vulnerability Rewards
Program](https://bughunters.google.com/open-source-security).

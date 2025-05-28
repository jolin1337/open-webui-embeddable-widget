# Open WebUI Chat Widget

This is a lightweight, embeddable Svelte chat widget that can be integrated into any HTML page or existing web application.

## Prerequisites

- Node.js and npm (or a compatible package manager like yarn or pnpm)

## Building the Widget

1.  **Install Dependencies:**
    Open your terminal in the project root directory and run:
    ```bash
    npm install
    ```

2.  **Build the Widget:**
    To compile the Svelte component into a distributable JavaScript file, run:
    ```bash
    npm run build
    ```
    This command will generate the bundled widget in the `dist` directory, specifically as `dist/ChatWidget.js`.

## How to Embed the Widget

Once built, you can embed the chat widget into any HTML page.

1.  **Include the Script:**
    Add the following script tag to your HTML file. Make sure to adjust the `src` path if you place the `dist` folder elsewhere relative to your HTML file.

    ```html
    <div id="owui-chat"></div>

    <script type="module">
      // Adjust path to where your ChatWidget.js is served from
      import ChatWidget from './dist/ChatWidget.js';

      new ChatWidget({
        target: document.getElementById('owui-chat')
      });
    </script>
    ```

2.  **Configure via URL Query Parameters:**
    The widget can be configured by passing query parameters in the URL of the page where it's embedded.

    -   `api_key` (required): Your API token for authentication.
    -   `model` (optional): The model to use (e.g., `llama3.1`). Defaults to `gpt-4o-mini`.
    -   `endpoint` (optional): The chat completions API endpoint. Defaults to `/api/chat/completions` (relative to the host serving the widget). If the widget isn't served from the same host as Open WebUI, provide the full URL (e.g., `https://owui.yourdomain.com/api/chat/completions`).

    **Example:**
    If your page is `https://example.com/chat-page.html`, you would append the parameters like this:
    `https://example.com/chat-page.html?api_key=YOUR_TOKEN&model=llama3.1`

    If using a custom endpoint:
    `https://example.com/chat-page.html?api_key=YOUR_TOKEN&model=llama3.1&endpoint=https://owui.yourdomain.com/api/chat/completions`

## Running the Demo

An example HTML page is provided in the `examples` directory.

1.  **Build the Widget:**
    If you haven't already, build the widget:
    ```bash
    npm run build
    ```

2.  **Serve the Demo Page:**
    To avoid browser security restrictions (CORS errors) when loading JavaScript modules from the local file system (`file:///`), you need to serve the demo page using a local HTTP server. Run the following command from the project root:
    ```bash
    npm run serve:demo
    ```
    This will start a local server, typically at `http://localhost:8080` (the exact port might vary if 8080 is in use). The terminal will display the accessible URLs.

3.  **Open the Demo Page in Your Browser:**
    Navigate to `http://localhost:8080/examples/index.html` (or the URL provided by `http-server`).

4.  **Provide Configuration:**
    As described above, you'll need to append query parameters (like `api_key`) to the URL in your browser's address bar for the chat to function. For example:
    `http://localhost:8080/examples/index.html?api_key=YOUR_TOKEN`

## Development

-   **Type Checking:**
    ```bash
    npm run check
    ```
    Or for watch mode:
    ```bash
    npm run check:watch
    ```

-   **Formatting:**
    ```bash
    npm run format
    ```

-   **Linting (Format Check):**
    ```bash
    npm run lint

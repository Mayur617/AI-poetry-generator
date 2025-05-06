# AI Poem Generator

## Table of Contents

1. [Project Overview](#project-overview)
2. [Key Features](#key-features)
3. [Prerequisites](#prerequisites)
4. [Installation & Setup](#installation--setup)
5. [Configuration](#configuration)
6. [Usage Guide](#usage-guide)
7. [Code Walkthrough](#code-walkthrough)

   * [HTML Structure](#html-structure)
   * [CSS Styling](#css-styling)
   * [JavaScript Logic](#javascript-logic)
8. [Error Handling & Edge Cases](#error-handling--edge-cases)
9. [Security Considerations](#security-considerations)
10. [Accessibility & UX Enhancements](#accessibility--ux-enhancements)
11. [Extending & Customization](#extending--customization)
12. [Architecture Diagram](#architecture-diagram)
13. [Contributing](#contributing)
14. [License](#license)
15. [Acknowledgments](#acknowledgments)

---

## Project Overview

The **AI Poem Generator** is a client-side web app that transforms simple user prompts into short, four-line romantic poems using the SheCodes AI Poem Generation API. With a dynamic typewriter animation effect, users enjoy an engaging experience as verses gently appear on screen. This tool is ideal for creative writers, social media enthusiasts, or anyone seeking poetic inspiration in seconds.

## Key Features

* **Prompt-Based Generation**: Enter any topic (e.g., "Sunset", "Paris") to receive a 4-line poem.
* **Typewriter Animation**: Character-by-character reveal for dramatic flair.
* **HTML Formatting**: Lines separated by `<br/>` and signed with **SheCodes AI**.
* **No Backend Required**: Entirely front-end; just open `index.html`.
* **Customizable**: Easily tweak styling, animation speed, or poem length.

## Prerequisites

* **Web Browser**: Latest versions of Chrome, Firefox, Edge, or Safari.
* **Internet Connection**: To reach the SheCodes AI endpoint.
* **SheCodes AI API Key**: Obtainable from your SheCodes dashboard.

## Installation & Setup

1. **Clone the repository**

   ```bash
   git clone https://github.com/username/ai-poem-generator.git
   cd ai-poem-generator
   ```

2. **Open in browser**

   * Simply double-click `index.html` or launch it via your preferred browser.

That’s it—no dependencies or package managers required!

## Configuration

1. In the `index.html` file, locate the `<script>` block near the bottom.
2. Replace the placeholder key:

   ```js
   let apiKey = "YOUR_SHECODES_API_KEY";
   ```
3. Save and refresh the page.

## Usage Guide

1. **Enter Topic**: Click on the input box and type your theme (e.g., "Love").
2. **Submit**: Hit the **Submit** button or press Enter.
3. **Watch**: A “Generating…” message appears, then the poem unfolds in a typewriter effect.
4. **Enjoy**: Each poem ends with a signature: **SheCodes AI**.

## Code Walkthrough

### HTML Structure

* **`<input id="user-instructions">`**: Captures the poem topic.
* **`<form id="poem-generator">`**: Wraps the input and submit button.
* **`<div id="poem">`**: Container for rendered poem text.

```html
<form id="poem-generator">
  <input id="user-instructions" ... />
  <input type="submit" value="Submit" />
</form>
<div id="poem" class="hidden"></div>
```

### CSS Styling

* **Container**: Centered with soft shadows and pastel background.
* **Typewriter Blink**: Custom keyframes for blinking cursor effect.
* **Responsive**: Fluid widths up to 600px for readability on mobile.

```css
.container { max-width: 600px; margin: auto; padding: 40px; }
.poem { font-size: 14px; padding: 20px; }
@keyframes blink { 50% { opacity: 0; }}
```

### JavaScript Logic

1. **Event Listener**: Triggers `generatePoem` on form submission.
2. **API URL Builder**: Combines user prompt and static context.
3. **Loading State**: Shows a “Generating…” message.
4. **Axios Request**: `axios.get(apiURL).then(displayPoem)`
5. **Typewriter Display**: Feeds response into `Typewriter` instance.

```js
function generatePoem(event) {
  event.preventDefault();
  const topic = document.querySelector('#user-instructions').value;
  const apiURL = `https://api.shecodes.io/ai/v1/generate?prompt=Generate a poem in English about ${topic}&context=${context}&key=${apiKey}`;
  poemElement.innerHTML = 'Generating...';
  axios.get(apiURL)
    .then(response => displayPoem(response))
    .catch(handleError);
}
```

## Error Handling & Edge Cases

* **Network Errors**: Caught via `.catch()`, user is shown a friendly retry message.
* **Empty Input**: Form `required` attribute prevents submission.
* **API Failure**: Check HTTP status codes and display specific alerts (e.g., 401 for invalid key).

## Security Considerations

* **API Key Exposure**: Front-end keys can be viewed—consider migrating the call to a server-side proxy.
* **Content Sanitization**: Trusted AI endpoint, but for other APIs, sanitize HTML output.
* **CORS**: Ensure your key and endpoint support cross-origin requests.

## Accessibility & UX Enhancements

* **Aria Labels**: Add `aria-label="Poem topic"` to input for screen readers.
* **Focus Management**: Auto-focus input on page load; return focus to input after poem.
* **Dark Mode Toggle**: Easily add a switch to invert colors.

## Extending & Customization

* **Poem Length**: Modify context string to request more/fewer lines.
* **Animation Timing**: Adjust `delay` parameter of `Typewriter`.
* **Themes & Styles**: Add dropdowns for different poetic forms (Haiku, Limerick).
* **Backend Proxy**: Build a simple Node.js or Flask service to hide the API key.

## Architecture Diagram

```
[User Browser] ---(HTTP GET)---> [SheCodes AI API]
        ^                                   |
        |-----------(Poem Response)--------|
```

## Contributing

1. Fork this repo.
2. Create a branch: `git checkout -b feature/awesome`
3. Commit your changes: `git commit -m "Add awesome feature"`
4. Push to GitHub: `git push origin feature/awesome`
5. Open a Pull Request.

## License

This project is licensed under the [MIT License](LICENSE).

## Acknowledgments

* [SheCodes](https://shecodes.io/) for the AI endpoint.
* [Typewriter Effect](https://github.com/tameemsafi/typewriterjs) for the animation library.
* Frontend design inspired by minimalistic UI patterns.

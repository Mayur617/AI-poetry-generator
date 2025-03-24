# AI Poem Generator

## Overview
The **AI Poem Generator** leverages the Hugging Face API to generate creative poems based on user-provided themes, styles, and moods. It allows users to input prompts for poems and select different styles and moods for their generated poetry. This application is designed to be easy to use and does not require advanced technical knowledge.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Features](#features)
- [Architecture](#architecture)
- [API Documentation](#api-documentation)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

## Prerequisites
To run this project, ensure you have the following:
- **Operating System**: Any system that can run modern web browsers (Windows, macOS, Linux).
- **Web Browser**: Chrome, Firefox, Safari, or any up-to-date browser.
- **API Token**: You will need a Hugging Face API token to generate poems using their model. Visit [Hugging Face](https://huggingface.co/) to get one.

## Installation
To get started with the AI Poem Generator:

1. Clone the repository:
   ```bash
   git clone https://github.com/username/ai-poem-generator.git
   cd ai-poem-generator
   ```

2. Open `index.html` in your web browser. No server-side installation is required; the app is entirely front-end based.

## Configuration
1. **API Key**: The Hugging Face API token is required to generate poems. Enter your token in the provided input field on the webpage.
   
2. **Configuration Files**: There are no specific configuration files required. The project operates purely on front-end JavaScript.

## Usage
To generate a poem:

1. Open the **AI Poem Generator** webpage.
2. Enter a **Hugging Face API Token** in the provided field.
3. Enter a **prompt** for the poem (e.g., a theme or specific details).
4. Choose the **Poetry Style** (e.g., Free Verse, Sonnet, Haiku, etc.).
5. Select the **Mood** of the poem (e.g., Joyful, Romantic, Melancholic, etc.).
6. Click the **Generate Poem** button.

The AI will generate a poem based on your input, and it will be displayed on the page once ready.

Example code for use (though the project works through a web interface, here's an outline for the backend request):
```javascript
const poem = generatePoemWithAI(apiKey, prompt, style, mood);
console.log(poem);
```

## Features
- **Poetry Styles**: Multiple styles including Free Verse, Sonnet, Haiku, Limerick, Acrostic, and Narrative.
- **Customizable Moods**: Choose a mood for your poem to tailor the tone (e.g., Joyful, Melancholic, etc.).
- **Hugging Face API Integration**: Uses Hugging Face's Inference API for powerful AI-generated poetry.

## Architecture
The project consists of the following components:

1. **Frontend (HTML/CSS/JS)**: The entire user interface is built using HTML, CSS, and JavaScript.
2. **API Integration**: The Hugging Face Inference API is used to generate the poems based on user input.

+------------------------+
|     Frontend (UI)      |
+------------------------+
           |
           v
+------------------------+
| Hugging Face API       |
| (Poetry Generation)    |
+------------------------+

## API Documentation
### Endpoint: /models/mistralai/Mistral-7B-Instruct-v0.2
- **Method**: POST
- **Parameters**:
  - `inputs` (required): The prompt for the poem.
  - `parameters` (optional):
    - `max_new_tokens`: Maximum number of tokens in the generated poem (default: 250).
    - `temperature`: Sampling temperature for randomness (default: 0.7).
    - `top_p`: Top-p (nucleus) sampling (default: 0.95).
    - `do_sample`: Whether to sample randomly (default: true).

**Example Request**:
```json
{
    "inputs": "Write a sonnet about love",
    "parameters": {
        "max_new_tokens": 250,
        "temperature": 0.7,
        "top_p": 0.95,
        "do_sample": true
    }
}
```

## Troubleshooting
Common issues and their solutions:

### Problem: Invalid API Key
*Symptom*: "Error: Invalid API Key" appears when trying to generate a poem.
*Solution*: Ensure your Hugging Face API key is correctly entered. You can retrieve it from [Hugging Face Token Settings](https://huggingface.co/settings/tokens).

### Problem: Empty Poem or No Response
*Symptom*: The poem is not generated.
*Solution*: Check if the API key is valid and if your network connection is stable. Also, ensure the prompt is correctly entered.

## Contributing
To contribute to this project:

1. Fork the repository.
2. Create a new feature branch.
3. Make your changes.
4. Commit your changes.
5. Push to the branch.
6. Submit a pull request.

## License
This project is licensed under the [MIT License](LICENSE).

---

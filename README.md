# Image Editing and Paint Color Changing App with Arabic Support

## Project Overview

This project demonstrates an **image editing** application that supports **Arabic** and leverages advanced AI models. The project offers two key functionalities:

1. **General Image Editing**: Users can provide text instructions in Arabic to edit images, which are translated into English before being passed to the **InstructPix2Pix** model.
2. **Paint Color Changing**: Users can upload images of rooms and change the wall color by selecting from a list of common paint colors (in Arabic), which is automatically translated into English for image processing.

The interface is built with **Gradio** and provides a simple yet powerful image manipulation tool using cutting-edge models from Hugging Face.

## Features

- **Arabic User Interface**: The entire interface is in Arabic, allowing non-English speakers to interact with the app seamlessly.
- **Image Editing**: Users can edit images by providing instructions (e.g., "اجعل الجو مثلج" -> "Make the weather snowy").
- **Color Translation**: Arabic color names are translated into English before processing to change the wall color in room images.
- **GPU Support**: The app detects and utilizes a GPU if available, otherwise, it falls back to CPU.
- **Random Seed**: Users can change the style of the generated output by randomizing the seed.

## Expected Outputs

1. **General Image Editing**: The user uploads an image and provides instructions in Arabic (e.g., "اجعل الصورة داكنة"). The application translates the prompt into English and applies the corresponding edits using the **InstructPix2Pix** model.
   
   **Example output**:
   - **Input**: An uploaded image of a landscape with the instruction "اجعل الجو ممطرًا" (Make it rainy).
   - **Output**: The image is modified to look as though it's raining.

2. **Paint Color Changing**: The user uploads an image of a room and selects a wall color from a dropdown list (in Arabic). The color is translated into English and applied to the image.

   **Example output**:
   - **Input**: An image of a living room with the color selected as "أبيض" (White).
   - **Output**: The walls of the room are changed to white.

## Models and Pipelines Used

### 1. **InstructPix2Pix Pipeline**

- **Model**: [timbrooks/instruct-pix2pix](https://huggingface.co/timbrooks/instruct-pix2pix)
- **Purpose**: This model is used to modify images based on textual instructions. It interprets instructions and applies relevant transformations to the image.
- **Why This Model?**: It’s specifically designed for fine-tuned image editing based on natural language instructions, making it ideal for this project’s general image editing functionality.

- **Pipeline Explanation**:
  - We use this pipeline to process user instructions (in English after translation), which are applied to the image using a combination of text and image guidance.
  - Text guidance (`guidance_scale`) controls how closely the output follows the provided instruction, while image guidance (`image_guidance_scale`) preserves the original content of the image.

### 2. **MarianMT Translation Pipeline**

- **Model**: [Helsinki-NLP/opus-mt-ar-en](https://huggingface.co/Helsinki-NLP/opus-mt-ar-en)
- **Purpose**: This model is used to translate the user’s Arabic text instructions into English before being passed to the image editing pipeline.
- **Why This Model?**: **MarianMT** is a state-of-the-art translation model that provides accurate and efficient translations between Arabic and English, ensuring the image editing instructions are correctly understood by the **InstructPix2Pix** model.

### 3. **Gradio**

- **Purpose**: Gradio is used to build the interactive user interface. It enables easy-to-use interfaces for uploading images, selecting colors, and providing textual instructions.

## Special Measures for Arabic Language Support

- **Full Arabic Interface**: The Gradio interface is fully translated into Arabic, including all text inputs, buttons, and labels, to provide an intuitive experience for Arabic-speaking users.
- **Right-to-Left (RTL) Layout**: The application uses RTL CSS styling to ensure the interface aligns naturally for Arabic users.
- **Translation Pipeline**: A dedicated translation pipeline (using **MarianMT**) translates Arabic instructions into English, ensuring compatibility with models that expect English input.
- **Arabic Color Names**: The app provides a list of common Arabic color names that are automatically translated into English before processing, ensuring a seamless user experience when changing paint colors.

## How to Run the Project

### Prerequisites

- Python 3.7 or higher
- Install the required libraries by running:

  ```bash
  pip install torch diffusers transformers gradio pillow
  ```
## Running the App
  
  1. Clone the repository and navigate to the project directory.

  2. Run the Python script to launch the Gradio app:
     ```bash
     python app.py
     ```

## Hugging Face Space

  https://huggingface.co/spaces/fahad11182/image_editing/blob/main/app.py

## Github Link

https://github.com/fahad1118/Image-Editing-Using-InstructPix2Pix-Model


# OpenAI-TextBlaze-CV-Generator

# Text Blaze OpenAI Cover Letter Generator

This project provides a Text Blaze snippet that leverages OpenAI's GPT-3.5-turbo model to generate personalized cover letter templates based on job descriptions copied to your clipboard.

## How It Works

1.  **Copy a Job Description:** Copy the job description you want to create a cover letter for to your clipboard.
2.  **Trigger the Snippet:** In Text Blaze, trigger the snippet (e.g., by typing `/makeCV`).
3.  **OpenAI API Interaction:**
    * The snippet sends the copied job description to the OpenAI API using a `POST` request.
    * It includes the necessary API key (securely stored in your Text Blaze account), model selection, and prompt.
    * The prompt instructs the model to act as a "resume expert" and generate a cover letter template.
4.  **Cover Letter Generation:** OpenAI generates a cover letter template based on the job description.
5.  **Output:** The generated cover letter template is inserted into your active application.

## Prerequisites

* **Text Blaze:** You need to have the Text Blaze browser extension installed.
* **OpenAI API Key:** You need an OpenAI API key. Ensure you securely store this key within your Text Blaze account's API key management.
* **OpenAI API Key Security:** **Important:** Never directly expose your OpenAI API key in publicly accessible code or files. Text Blaze's secure storage is essential.

## Installation and Usage

1.  **Install Text Blaze:** If you haven't already, install the Text Blaze extension for your browser.
2.  **Import the Snippet:**
    * Copy the content of `cover_letter_generator.tbt`.
    * In Text Blaze, create a new snippet.
    * Paste the copied content into the snippet editor.
    * Adjust the trigger (e.g., `/makeCV`) as desired.
3.  **Set Your OpenAI API Key:**
    * In Text Blaze, go to your account settings and manage API keys.
    * Input your OpenAI API Key.
4.  **Test the Snippet:**
    * Copy the content of `example_job_description.txt` to your clipboard.
    * Open a text editor or document.
    * Trigger the snippet (e.g., `/makeCV`).
    * Observe the generated cover letter template.

## Example Job Description

Here's an example job description you can use to test the snippet:

# AI Resume & Cover Letter Generator (n8n Workflow)

This repository contains an automated n8n workflow that generates a professional, LaTeX-formatted resume and a customized cover letter based on a user's form submission. It leverages Google Gemini for content generation and an external API for LaTeX-to-PDF compilation.

## 🚀 Workflow Overview

Here is how the automation works step-by-step:
1. **Trigger:** The workflow starts when a user submits a form (`On form submission`).
2. **AI Generation:** The data is passed to a `Resume Generator` powered by the **Google Gemini Chat Model**, which uses a `Structured Output Parser` to format the response accurately.
3. **Parallel Processing:** The workflow splits into two distinct tasks:
   * **Resume Compilation (Top Branch):** The AI-generated LaTeX code is sent via a POST request (`Send Latex`) to a compilation API (e.g., Advicement). The workflow waits for the compilation to finish, retrieves the link (`Get PDF Link`), and downloads the final document (`Download PDF`).
   * **Cover Letter Generation (Bottom Branch):** The AI-generated cover letter text is processed and saved as a downloadable text file (`Convert to Cover Letter to File`).

## 🛠️ Prerequisites

To run this workflow in your own n8n instance, you will need:
* A running instance of **n8n** (Cloud, Desktop, or Self-hosted).
* A **Google Gemini API Key** configured in your n8n credentials.
* Access/API keys for the LaTeX compilation service used in the HTTP Request nodes.

## 📥 How to Import

1. Clone or download this repository.
2. Open your n8n interface and click on **Workflows** > **Add Workflow**.
3. Click the menu icon (top right) and select **Import from File...**
4. Select the `.json` file from this repository.
5. Once imported, click on the **Google Gemini** node and the **HTTP Request** nodes to select or input your personal API credentials.
6. Save and activate the workflow!

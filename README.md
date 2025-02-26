# n8n Telegram AI Agent Workflow

This n8n workflow automates interactions with Telegram using an AI Agent. It listens for messages in a Telegram chat, enriches the data with information from Airtable, processes it with an AI model, and sends a response back to Telegram.

## Workflow Overview
![n8n Workflow Screenshot](https://i.postimg.cc/cHhWxW2V/Screenshot-2025-02-26-144516.png)

The workflow consists of the following nodes:

1.  **Telegram Trigger:**
    * Listens for new messages in a specified Telegram chat.
    * Triggers the workflow when a new message is received.
    * Outputs the message text and sender information.

2.  **Airtable:**
    * Searches an Airtable base for relevant information based on the incoming message.
    * Retrieves records from Airtable and adds them to the workflow data.

3.  **Aggregate:**
    * Aggregates the data from the Telegram message and Airtable records into a single item.
    * Combines the information for further processing.

4.  **Merge:**
    * Merges two input streams (in this case, the aggregated data and potentially other inputs).
    * Combines the data into a single stream for the AI Agent.

5.  **AI Agent (Tools Agent):**
    * The core of the workflow, utilizing an AI model (OpenRouter Chat Model) to process the combined data.
    * Uses tools such as `SoDutout Parser` and `memory_tool` to interact with external data and maintain context.
    * Processes the input and generates a response based on the AI model's output.

6.  **Telegram:**
    * Sends the AI-generated response back to the Telegram chat.
    * Completes the interaction loop.

7.  **OpenRouter Chat Model:**
    * The AI model used by the AI Agent.
    * Processes the input data and generates a response.

8.  **Window Buffer Memory:**
    * Maintains a memory of previous interactions, allowing the AI Agent to have context.
    * Stores recent messages and interactions.

9.  **memory_tool:**
    * A tool used by the AI Agent to interact with the Window Buffer Memory.
    * Allows the AI Agent to create and retrieve records from memory.

## Prerequisites

* **n8n Instance:** You need a running n8n instance.
* **Telegram Bot Token:** You need a Telegram bot token to connect to the Telegram API.
* **Airtable API Key and Base ID:** You need an Airtable API key and base ID to connect to your Airtable base.
* **OpenRouter API Key:** You need an OpenRouter API key to use the OpenRouter Chat Model.
* **n8n Credentials:** You need to configure the necessary credentials in n8n for Telegram, Airtable, and OpenRouter.

## Installation

1.  **Import the Workflow:**
    * Download the JSON file of the workflow.
    * In your n8n instance, go to "Workflows" and click "Import".
    * Select the downloaded JSON file and import it.

2.  **Configure Credentials:**
    * Open the workflow and configure the credentials for the Telegram, Airtable, and OpenRouter nodes.
    * Enter your API keys and other necessary information.

3.  **Configure Nodes:**
    * Configure the Telegram Trigger node with the correct chat ID.
    * Configure the Airtable node with the correct base ID, table name, and search parameters.
    * Configure the AI Agent node with the desired AI model and settings.
    * Configure the Telegram node with the correct chat ID.

4.  **Activate the Workflow:**
    * Click the "Activate" toggle in the top right corner of the workflow editor.

## Usage

1.  **Start a conversation with your Telegram bot.**
2.  **Send a message to the bot.**
3.  **The workflow will be triggered.**
4.  **The bot will process the message using the AI Agent and send a response.**

## Customization

* **Modify the Airtable node:** Change the search parameters to retrieve different data from Airtable.
* **Change the AI model:** Use a different AI model in the OpenRouter Chat Model node.
* **Customize the AI Agent:** Modify the tools and prompts used by the AI Agent.
* **Add more nodes:** Extend the workflow with additional nodes to perform more complex tasks.

## Contributing

Feel free to contribute to this workflow by submitting pull requests or opening issues.

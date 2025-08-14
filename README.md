# OpenAI Integration in Node.js

This project demonstrates how to integrate OpenAI's API into a Node.js application using the official OpenAI SDK.

## Features
- Connects to OpenAI's GPT models (e.g., gpt-3.5-turbo)
- Sends prompts and receives AI-generated responses
- Uses environment variables for secure API key management

## Prerequisites
- Node.js (v14 or higher recommended)
- An OpenAI account and API key ([Get your API key here](https://platform.openai.com/account/api-keys))

## Setup

1. **Clone the repository**
   ```sh
   git clone <your-repo-url>
   cd OpenAi-Integration-in-Node
   ```

2. **Install dependencies**
   ```sh
   npm install
   ```

3. **Configure your API key**
   - Create a `.env` file in the project root:
     ```env
     OPENAI_API_KEY=your_openai_api_key_here
     ```
   - **Never share your API key publicly!**

4. **Run the project**
   ```sh
   node index.js
   ```

## How it Works
- The code in `index.js` loads your API key from the `.env` file using `dotenv`.
- It initializes the OpenAI client and sends a prompt to the GPT model.
- The AI's response is printed to the console.

## Example Code
```js
const { OpenAI } = require('openai');
const dotenv = require('dotenv');
dotenv.config();
const openai = new OpenAI({ apiKey: process.env.OPENAI_API_KEY });
async function getCompletion(prompt) {
  const completion = await openai.chat.completions.create({
    messages: [{ role: 'user', content: prompt }],
    model: 'gpt-3.5-turbo',
  });
  console.log(completion.choices[0].message.content);
}
getCompletion('Hello, how can I integrate AI into my Node.js project?');
```

## Security
- Add `.env` and `node_modules/` to your `.gitignore` to avoid pushing sensitive data:
  ```
  .env
  node_modules/
  ```

## Troubleshooting
- **API Key Errors:** Make sure your `.env` file is present and contains a valid key.
- **Quota/Rate Limit Errors:** Check your [OpenAI usage and billing](https://platform.openai.com/usage).
- **Network Issues:** Ensure you have internet access and no firewall is blocking requests.

## Resources
- [OpenAI Node.js SDK Docs](https://github.com/openai/openai-node)
- [OpenAI API Reference](https://platform.openai.com/docs/api-reference)

## License
This project is licensed under the ISC License.

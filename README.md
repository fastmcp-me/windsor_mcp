# Windsor MCP Server

Windsor MCP (Model Context Protocol) enables your LLM to query, explore, and analyze your full-stack business data integrated into Windsor.ai with zero SQL writing or custom scripting.  
It connects seamlessly to 325+ platforms, giving AI-native tools such as Claude, Perplexity, Cursor, or others, real-time access to your performance marketing, sales, and customer data to help you unlock valuable insights.

---

## 🌟 Features

### Natural language access to business data  
Windsor MCP is a natural language interface that connects your integrated Windsor.ai datasets with the LLM platform, enabling you to better understand your data by asking questions like:
- “What campaigns had the best ROAS last month?”
- “Give me a breakdown of spend by channel over the past 90 days.”
- “What campaigns are wasting our advertising budget?”

All in real-time, directly inside your LLM chat interface.

### Out-of-the-box integration with 325+ sources  
Sync data from Facebook Ads, GA4, HubSpot, Salesforce, Shopify, TikTok Ads, and more via native Windsor.ai connectors.

### Zero-code setup  
Windsor MCP works via the Claude Desktop or with a lightweight dev proxy. No custom integrations required.

### Open standard compatibility  
Built on Anthropic’s open MCP spec, it’s compatible with Claude, Perplexity, Cursor, and more.

### Real-time Analytics without SQL  
Get instant breakdowns, summaries, and performance insights from your integrated data.

---

## 🎯 How It Works

You connect Windsor MCP to your preferred LLM as an external connector using the MCP protocol. The LLM can then issue real-time data queries and receive structured results, all within the chat interface.

### Example prompts:
- What was total ad spend by channel last month?
- Break down ROAS for Meta vs Google Ads for Q2
- Are there any campaigns overspending vs target ROAS?

---

## 🚀 Getting Started

### View our official documentation  
[https://windsor.ai/introducing-windsor-mcp/](https://windsor.ai/introducing-windsor-mcp/)

---

## Option 1: Claude Desktop (Recommended)

### Prerequisites:
- Claude Pro or higher-tier Claude Desktop plan  
- Your Windsor API key

### Steps:
1. Go to **Claude settings → Connectors → Add custom connector**
2. Use one of the following URLs for Windsor MCP:
   - `https://mcp.windsor.ai`  
   - `https://mcp.windsor.ai/sse`
3. Open a new chat and start with:
<pre>
  My Windsor.ai API key is {your-key}. {Your question here}
</pre>
4. Accept connector permissions and start querying your data!

---

## Option 2: Developer Proxy Setup
For users on lower-tier Claude plans or requiring custom setups for advanced flexibility.
### Prerequisites:
- Claude Desktop with dev mode enabled

### Installation steps:
1. Inatall mcp-proxy and copy its path.
<pre>
  uv tool install mcp-proxy
  which mcp-proxy  # Copy full path
</pre>

2. Configure Claude Desktop:
Open Settings → Developer → Edit Config and add:
<pre>
{
  "mcpServers": {
    "windsor": {
      "command": "/Users/{your-username}/.local/bin/mcp-proxy",
      "args": ["https://mcp.windsor.ai/sse"]
    }
  }
}
</pre>

💡 Replace <your-username> with your system username.

3. Fully quit and reopen Claude. You should now see “windsor” listed in your MCP options.

---

## Option 3: Windsor MCP with Gemini CLI

### Installation steps:
1. Install mcp-proxy
<pre>
  uv tool install mcp-proxy
  which mcp-proxy  # Copy full path
</pre>

2. Install Gemini CLI
Use Node.js to globally install the Gemini CLI (make sure you have Node.js 18 or later installed).
<pre>
  npm install -g @google/gemini-cli
</pre>

3. Configure Gemini to use Windsor MCP
Navigate to the Gemini config directory:
<pre>
  cd ~/.gemini
</pre>
If the .gemini directory doesn’t exist yet, run gemini once to generate it.
Open the settings.json file:
<pre>
   nano settings.json
</pre>
Add the following configuration inside the JSON object:
<pre>
{
  "mcpServers": {
    "windsor": {
      "command": "/Users/{your-username}/.local/bin/mcp-proxy",
      "args": ["https://mcp.windsor.ai/sse"]
    }
  }
}
</pre>
Note: Make sure the overall file remains valid JSON (no trailing commas or syntax errors).

4. Start Gemini with Windsor MCP
Now, simply run Gemini:
<pre>
   gemini
</pre>
You’ll be asked for your Windsor API key — paste it in to authenticate. You’re all set now!

## ❓ FAQs

### Is Windsor MCP free to use?
Yes, it's available during our beta phase. You’ll need a Windsor.ai account with integrated data and API key access. But keep in mind that Claude Desktop allows you to add external connectors only on the paid plans.
### What agents does it work with?
Any AI agent compatible with MCP, including Claude Desktop, Perplexity, Cursor, and custom tools.
### What can I ask Windsor MCP?
Marketing performance, sales pipelines, spend summaries, ROAS trends, campaign anomalies, and more. If it’s in your Windsor.ai data, you can ask it.
### Do I need to write SQL or set up dashboards?
No. Just ask your questions in plain English and get structured responses in real-time.

--- 

## 🧪 Beta Status
Windsor MCP is currently in beta. All features are fully functional, but you may encounter occasional quirks. We're actively improving performance, authentication, compatibility, and feature coverage.

## 🧠 Try It Now
Start querying your business data via Windsor MCP.
<br/>
👉 [Get your API Key](https://onboard.windsor.ai)
<br/>
👉 [Watch the demo](https://youtu.be/84bBP71qvjs)
<br/>
<br/>
For support or feedback, contact us at support@windsor.ai.

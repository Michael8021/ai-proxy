# AI Proxy

This is a simple proxy for AI services.

## Sponsorship

This project is sponsored by [ChatWise](https://chatwise.app), the fastest AI chatbot that works for any LLM.

## Usage

Replace your API domain with the domain of the proxy deployed on your server. For example:

- Gemini:
  - from `https://generativelanguage.googleapis.com/v1beta` 
  - to `https://your-proxy/generativelanguage/v1beta`
- OpenAI:
  - from `https://api.openai.com/v1`
  - to `https://your-proxy/openai/v1`
- Anthropic:
  - from `https://api.anthropic.com/v1`
  - to `https://your-proxy/anthropic/v1`
- Groq:
  - from `https://api.groq.com/openai/v1`
  - to `https://your-proxy/groq/openai/v1`
- Perplexity:
  - from `https://api.perplexity.ai`
  - to `https://your-proxy/pplx`
- Mistral:
  - from `https://api.mistral.ai`
  - to `https://your-proxy/mistral`
- OpenRouter:
  - from `https://openrouter.ai/api`
  - to `https://your-proxy/openrouter`
- xAI:
  - from `https://api.xai.ai`
  - to `https://your-proxy/xai`
- Cerebras:
  - from `https://api.cerebras.ai`
  - to `https://your-proxy/cerebras`
 
## Hosted by ChatWise

Use the hosted API, for example OpenAI `https://ai-proxy.chatwise.app/openai/v1`

## Deployment

### Option 1: Cloudflare Workers (Recommended)

Deploy to Cloudflare Workers for free with global edge network.

#### Prerequisites

- [Node.js](https://nodejs.org/) (v18 or later)
- A [Cloudflare account](https://dash.cloudflare.com/sign-up) (free)

#### Steps

1. **Clone this repository**

   ```bash
   git clone https://github.com/Michael8021/ai-proxy.git
   cd ai-proxy
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

3. **Login to Cloudflare**

   ```bash
   npx wrangler login
   ```
   
   This will open a browser window to authenticate with your Cloudflare account.

4. **Deploy to Cloudflare Workers**

   ```bash
   npm run deploy
   ```

   After deployment, you'll get a URL like: `https://ai-proxy.your-subdomain.workers.dev`

#### Custom Domain (Optional)

To use your own domain, edit `wrangler.toml` and uncomment the routes section:

```toml
routes = [
  { pattern = "api.yourdomain.com/*", zone_name = "yourdomain.com" }
]
```

Then run `npm run deploy` again.

#### Local Development

```bash
npm run dev:worker
```

This starts a local dev server at `http://localhost:8787`.

#### Notes

- Cloudflare Workers free tier includes **100,000 requests/day**
- Worker name is defined in `wrangler.toml` (`name = "ai-proxy"`)
- Re-deploying from a different machine with the same Cloudflare account and worker name will update the same worker

### Option 2: Docker

Deploy this as a Docker container, check out [Dockerfile](./Dockerfile).

```bash
docker build -t ai-proxy .
docker run -p 4000:4000 ai-proxy
```

## License

MIT.

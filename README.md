# AI Studio
A standalone Cloudflare Worker dashboard for OpenAI chat, image generation and photo editing.

## Deployment
The GitHub Actions workflow deploys the Worker **aistudio** on pushes to main, once repository Actions secrets **CLOUDFLARE_API_TOKEN** and **CLOUDFLARE_ACCOUNT_ID** are configured. The token must have Workers Scripts Edit permissions for the existing Worker. Do not commit credentials.

In Cloudflare Worker settings add secret **OPENAI_API_KEY** and secret **APP_PASSWORD**. Keep these settings on the Worker; redeploying does not require hardcoding them.

The image model defaults to **gpt-image-2**, and can be changed through the optional server-side **IMAGE_MODEL** variable if the OpenAI project supports a different image generation/editing model.

This app is intended for personal use. Before exposing a paid API publicly, add Cloudflare Access and robust server-side rate limits. Image gallery is session-local; chats are saved to your browser localStorage. The 18+ tab is a placeholder and does not generate explicit sexual content.

Deployment check: initiated after configuring Cloudflare GitHub Actions secrets.

Cloudflare deployment retry after configuring repository secrets.

Deployment retry after Cloudflare token configuration (attempt 3).

## Venice 18+ Studio
Set `VENICE_API_KEY` as a secret on the existing Cloudflare Worker. Optional `VENICE_IMAGE_MODEL` sets a Venice-supported image model; otherwise Venice's default image model is requested. This feature is limited to fictional consenting adult depictions and includes an 18+ self-confirmation, which is not a robust age-verification system. A production release requires suitable age verification, abuse prevention, per-user rate limiting, and legal/provider-terms review. The Venice image endpoint is separate from OpenAI image generation. Image generation costs can apply.

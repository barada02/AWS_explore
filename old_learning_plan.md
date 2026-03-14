# AWS Learning Plan — Amazon Nova Hackathon
> Goal: Build a working Gen AI app with Amazon Nova. Learn only what's needed to ship.

---

## Phase 1 — Setup (Do This First, ~1-2 hrs)

- [ ] Create an AWS account (or log into existing one)
- [ ] Enable MFA on root account (takes 5 min, prevents lockout disasters)
- [ ] Create an IAM user with programmatic access — attach `AmazonBedrockFullAccess` + `AmazonS3FullAccess`
- [ ] Save the Access Key ID and Secret Access Key somewhere safe
- [ ] Install AWS CLI → `winget install Amazon.AWSCLI`
- [ ] Run `aws configure` and paste your keys + set region to `us-east-1` (Nova is available there)
- [ ] Install boto3 → `pip install boto3`
- [ ] Verify setup: run `aws sts get-caller-identity` — should return your account info

---

## Phase 2 — Amazon Bedrock Core (~2-3 hrs)
> Bedrock is the service that hosts Nova. This is your main AWS service.

- [ ] Go to AWS Console → Bedrock → **Model Access** → Request access to all Amazon Nova models
  - Nova Lite, Nova Pro, Nova Sonic, Nova Multimodal Embeddings
  - Approval is usually instant or within minutes
- [ ] Read: [Bedrock Converse API docs](https://docs.aws.amazon.com/bedrock/latest/userguide/conversation-inference.html) — this is the main API you'll use
- [ ] Run your first Nova call with boto3:
  ```python
  import boto3, json
  client = boto3.client("bedrock-runtime", region_name="us-east-1")
  response = client.converse(
      modelId="us.amazon.nova-lite-v1:0",
      messages=[{"role": "user", "content": [{"text": "Hello!"}]}]
  )
  print(response["output"]["message"]["content"][0]["text"])
  ```
- [ ] Test streaming responses (`converse_stream`) — important for good UX
- [ ] Understand the model IDs:
  - `us.amazon.nova-lite-v1:0` — fast & cheap, use for most things
  - `us.amazon.nova-pro-v1:0` — smarter, use when quality matters
  - `us.amazon.nova-sonic-v1:0` — speech-to-speech (Voice AI track)

---

## Phase 3 — Pick Your Track & Go Deep (~3-4 hrs)
> Pick ONE track. Don't try to cover all of them.

### Track A: Agentic AI
- [ ] Learn Bedrock tool use (function calling) — [docs](https://docs.aws.amazon.com/bedrock/latest/userguide/tool-use.html)
- [ ] Build a simple agent loop: LLM decides → calls tool → gets result → continues
- [ ] Try [Strands Agents SDK](https://strandsagents.com) (AWS's own agent framework, minimal boilerplate)
- [ ] (Optional) Look at Bedrock Agents if you want fully managed orchestration

### Track B: Multimodal Understanding
- [ ] Test image input with Nova Lite — pass base64 image in the `content` array
- [ ] Test document understanding — PDFs can be passed directly
- [ ] Try Nova Multimodal Embeddings for semantic search across images+text
- [ ] (Optional) Use S3 to store and reference large files instead of base64

### Track C: Voice AI (Nova Sonic)
- [ ] Read Nova Sonic docs — it uses a **bidirectional streaming** WebSocket API (different from Converse)
- [ ] Set up the Nova Sonic SDK / sample from AWS GitHub
- [ ] Build a basic real-time voice loop: mic → Sonic → speaker
- [ ] Test latency — keep conversation turns short

### Track D: UI Automation (Nova Act)
- [ ] Sign up for Nova Act access at [aws.amazon.com/nova/act](https://aws.amazon.com/nova/act/)
- [ ] Install the Nova Act SDK → `pip install nova-act`
- [ ] Run the quickstart example from the docs
- [ ] Pick a real web workflow to automate (e.g., form filling, data extraction from websites)

---

## Phase 4 — Minimum Viable Project (~4-6 hrs)

- [ ] Define your project in one sentence before building
- [ ] Build the core loop (input → Nova → output) first, make it work end to end
- [ ] Add error handling and basic retry logic for API calls
- [ ] Record your ~3 min demo video while the app works (don't wait until last minute)
- [ ] Push code to a public GitHub repo
- [ ] Write a short README explaining what it does and how to run it

---

## Phase 5 — Submission Checklist

- [ ] Text description written (project summary, how it uses Nova)
- [ ] Demo video uploaded with `#AmazonNova` hashtag
- [ ] GitHub repo link ready (make sure it's accessible)
- [ ] Category selected: Agentic AI / Multimodal / UI Automation / Voice AI / Freestyle
- [ ] Submit on Devpost before deadline

---

## 🕐 If You Have Extra Time (Bonus / Nice-to-Have)

- [ ] Write a blog post on [builder.aws.com](https://builder.aws.com) — earns bonus prize points
- [ ] Add a simple web UI (Streamlit is the fastest: `pip install streamlit`)
- [ ] Deploy to AWS Lambda + API Gateway for a live URL (impressive in demo)
- [ ] Add S3 file upload so users can drop in their own files
- [ ] Use Bedrock Guardrails to add content safety layer
- [ ] Experiment with Nova Pro for better reasoning quality on complex tasks

---

## Quick Reference

| Thing | Value |
|---|---|
| Main Region | `us-east-1` |
| Nova Lite model ID | `us.amazon.nova-lite-v1:0` |
| Nova Pro model ID | `us.amazon.nova-pro-v1:0` |
| Nova Sonic model ID | `us.amazon.nova-sonic-v1:0` |
| Bedrock Console | console.aws.amazon.com/bedrock |
| Nova Docs | docs.aws.amazon.com/nova |
| Strands Agents | strandsagents.com |
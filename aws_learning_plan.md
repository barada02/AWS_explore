# AWS Learning Plan — Amazon Nova Hackathon
> Goal: Learn the minimum AWS + Nova needed for hands-on experimentation fast.

> Updated for current AWS/Nova positioning as of March 2026. This plan is for learning and experiments, not for shipping a hackathon project.

---

## What matters first

- [ ] Remember this rule: **learn by running small experiments, not by reading everything**
- [ ] Focus on only 2 things first:
  - [ ] how to access Amazon Nova
  - [ ] how to try one or two useful capabilities yourself
- [ ] Ignore advanced AWS services unless they directly help your experiment

---

## Phase 1 — Basic AWS setup (~45-90 min)

- [ ] Create/sign in to your AWS account
- [ ] Enable MFA on the root account
- [ ] Create an IAM user for daily work
- [ ] Give it only what you need for now:
  - [ ] access to Amazon Bedrock
  - [ ] access to S3 only if you need file-based experiments
- [ ] Install AWS CLI
- [ ] Run `aws configure`
- [ ] Set your working region to the one where the Nova feature you want is available
- [ ] Verify login with `aws sts get-caller-identity`

---

## Phase 2 — Understand where Nova fits (~30 min)

- [ ] Learn this mental model:
  - [ ] **Amazon Nova** = the models/services family
  - [ ] **Amazon Bedrock** = the main AWS platform where you access many Nova models
  - [ ] **Nova Act** = separate Nova service for browser/UI automation
- [ ] Open the Amazon Nova page and skim what each offering is:
  - [ ] Nova 2 Lite
  - [ ] Nova 2 Sonic
  - [ ] Nova Multimodal Embedding
  - [ ] Nova Act
- [ ] Do not try to learn all Nova products today

---

## Phase 3 — First hands-on with Nova through Bedrock (~1-2 hrs)

- [ ] Open Amazon Bedrock in the AWS console
- [ ] Request/enable access to the Amazon Nova models you actually want to test
- [ ] Find the currently available model names in your console/docs before coding
- [ ] Run one very small text experiment with Nova
- [ ] Change only one variable at a time:
  - [ ] prompt style
  - [ ] system instruction
  - [ ] response length
- [ ] Save the prompts that worked well in a notes file
- [ ] Try streaming output only if you need interactive behavior

---

## Phase 4 — Pick one experiment path only (~2-4 hrs)

### Option A — Text / reasoning with Nova 2 Lite
- [ ] Ask it to summarize a long note or article
- [ ] Ask it to extract structured information from messy text
- [ ] Ask it to compare two options and explain trade-offs
- [ ] Write down where it performs well and where it fails

### Option B — Multimodal understanding
- [ ] Give it an image and ask factual questions
- [ ] Try a document/PDF understanding task
- [ ] Test whether the response is actually grounded in the input
- [ ] If useful, try Nova Multimodal Embedding only after the basic tests work

### Option C — Voice with Nova 2 Sonic
- [ ] Read only the getting-started material for Sonic
- [ ] Run one sample app/demo first
- [ ] Test latency and conversation quality
- [ ] Stop if setup becomes heavy and switch back to Lite unless voice is your main interest

### Option D — UI automation with Nova Act
- [ ] Read the quickstart only
- [ ] Run one official sample first
- [ ] Test one simple browser task end-to-end
- [ ] Leave advanced workflow design for later

---

## Phase 5 — Useful AWS things to learn only if needed (~1-2 hrs)

- [ ] Learn S3 only if your experiments use files, images, PDFs, or outputs
- [ ] Learn basic IAM only enough to avoid permission confusion
- [ ] Learn CloudWatch only if you need logs for debugging
- [ ] Skip Lambda, API Gateway, deployment, VPC, and full architecture topics for now

---

## Phase 6 — Capture learning, not a project (~30-45 min)

- [ ] Keep a short log of every experiment:
  - [ ] what you tried
  - [ ] what worked
  - [ ] what failed
  - [ ] what to try next
- [ ] Keep 3 best prompts/examples
- [ ] Write 5-10 bullet points on what Nova seems good at
- [ ] Write 3-5 bullet points on current limitations you observed

---

## If you get extra time

- [ ] Compare Nova 2 Lite with another Nova option for the same task
- [ ] Try tool use / agent behavior after basic prompting feels clear
- [ ] Try embeddings only if search/retrieval actually matters to your exploration
- [ ] Try S3-based file workflows if your inputs are large

---

## What to skip for now

- [ ] Skip full project architecture
- [ ] Skip deployment
- [ ] Skip polished UI work
- [ ] Skip advanced AWS networking/security topics
- [ ] Skip services you are not actively using

---

## Quick clarification: Why Bedrock?

- [ ] Because the current Amazon Nova foundation models are made available through Amazon Bedrock for most builder workflows
- [ ] Because Bedrock is the place where you request model access and invoke many Nova models
- [ ] Because the hackathon promotes **Nova**, but in practice many Nova experiments are done **through Bedrock**
- [ ] Exception: **Nova Act** is its own Nova service, so not every Nova item means Bedrock

---

## Simple priority order

- [ ] 1. AWS login + CLI
- [ ] 2. Bedrock access to Nova
- [ ] 3. One successful experiment
- [ ] 4. One deeper path only
- [ ] 5. Notes on what you learned

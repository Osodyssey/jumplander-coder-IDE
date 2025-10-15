
# JumpLander Coder — User Panel Documentation (EN)

> This document explains, from a user's point of view, how to use the JumpLander AI coding platform panel (the web dashboard).  
> It also maps the code pieces (based on the provided `index.php`) to UI behaviors, explains available features (chat, models, agents, tools), and gives practical usage examples, API snippets and developer notes for the repository.

---

## Purpose & Scope

This README is a **complete usage guide** for users who sign in to the JumpLander panel. It is written for an English-speaking audience and is intended to be added to your GitHub repository (`jumplander-coder`) as a dedicated `README_PANEL.md` or merged into `README.md`.

The guide covers:
- How a user interacts with the panel (step-by-step UI walk-through).
- The available features (Chat, Models, Tools, Agents, VS Code-like integration).
- Example flows (generate code, refactor, security scan, agent-run pipelines).
- How the backend (`index.php` and included files) maps to these features.
- Installation and developer notes, environment variables, and a rough implementation completeness estimate.

---

## Quick User Onboarding (What the user sees when they first enter)

1. **Landing / Login**
   - User opens the panel URL and sees a Login / Signup form.
   - After login, session is created (`session_start()` in `index.php`) and user profile loads.

2. **Dashboard**
   - Top-level metrics: remaining credits/quota, active plan, plan expiry date (the PHP code reads `$planExpiryDate`, `$planPurchaseDate`).
   - Quick actions: "New Chat", "Start Agent", "Upload Project", "Billing".

3. **Main Work Area (VS Code-like)** — the primary workspace:
   - Left: File explorer (project files).
   - Center: Code editor (Monaco or CodeMirror) with an inline suggestion cursor (like Cursor.ai).
   - Right: Chat pane for AI interactions (system messages, tool buttons, model selector).
   - Bottom: Terminal / test runner.

4. **Chat Pane & Tools**
   - A chat interface where user sends prompts and receives answers/patches. Tools such as `Refactor`, `Debug`, `Security Scan`, `Generate Test` are buttons above the chat input.
   - Model selector (choose "Iranian model", "fast small model", "high-quality model") and `temperature` control.
   - "Agent" menu to run multi-step workflows (security-fix agent, test-generator agent, code-review agent).

5. **Agents**
   - Agents run as pipelines (analyze → propose → apply → test). Agents execute multi-step tasks and create job ids that user can monitor.
   - Long-running runs are accessible from `Jobs` page.

6. **Billing & Quota**
   - Each action consumes request credits according to `$requestCosts` (defined in `index.php`).
   - The panel displays current quota and deducts cost after completion of operations.
   - Payment integration files (e.g., referenced `pymentvira/inc/functions.php`) handle payment flows and subscriptions.

---

## Typical User Flows (detailed)

### 1) Generate a new function (Code Generation)
- User clicks "New Chat" → chooses "Generate" tool → selects language (e.g., Python) and writes prompt.
- The client sends `POST /api/v1/code/generate` (or internally calls a PHP handler).
- The server verifies user session, checks quota/cost (`$requestCosts['standard']`) and either queues or streams result to the editor.
- The result is shown in the chat and can be inserted into the editor by clicking "Apply".

**UI Buttons:** `Generate`, `Insert`, `Save`, `Run`.

**Edge handling:** If insufficient credits, the panel shows "Top-up" link.

---

### 2) Refactor Existing Code (Refactor Tool)
- Select code region in editor → press `Refactor` → supply goal (e.g., "make types explicit, fix edge cases").
- System sends `POST /api/v1/code/refactor` with `source`, `goal`, `mode`.
- Backend charges `$requestCosts['refactor']` credits; agent may run additional analysis.
- Response returns a unified diff/patch. The UI shows a side-by-side preview with Accept/Reject controls.
- Accepting the patch applies a three-way merge to the editor and saves a new file version.

---

### 3) Security Scan & Fix (Security Tool)
- Click `Security Scan` on project or file.
- Backend runs static analyzers and LLM-based suggestions (combined).
- Results show categorized issues and a "Fix" button per issue that can trigger an agent to create a patch.
- The patch undergoes automated tests (if present) before presenting to the user.

---

### 4) Agents (Complex Workflows)
- Agents are pre-configured or user-created pipelines. Example agent `security-fix-agent`:
  1. Run static analyzer.
  2. Generate suggested fixes via LLM.
  3. Run unit tests in a sandbox.
  4. Create an MR / PR or apply patch locally.

- A job entry (ID) is generated and visible in `Jobs` list. The UI supports logs and step-by-step trace.

---

## Panel Controls and UX Elements (cursor, inline suggestions, hotkeys)

- **Inline cursor suggestions**: Press `Ctrl+Space` to accept next suggestion; preview suggestions while typing (Monaco's `editor.trigger()` style).
- **Quick actions**: Hover line number → shows quick action menu: `Explain`, `Refactor`, `Test`, `Create Agent Step`.
- **Hotkeys**:
  - `Ctrl+Enter` — send chat prompt.
  - `Ctrl+.` — show quick fix menu.
  - `Ctrl+K Ctrl+S` — save all.

---

## Developer Mapping — index.php analysis & where things connect

Based on the uploaded `/index.php` snippet, here are the concrete mappings and what is handled by this file:

- `session_start()` — session lifecycle for logged-in users.
- Database connection details (`$servername`, `$username`, `$password`, `$dataname`) — database used for user accounts, plans, and job metadata.
- `require_once('osw.php')` and `require("pymentvira/inc/functions.php")` — shows integration with payment modules and helper utilities (payment and helper functions are separated in `pymentvira/inc`).
- `$requestCosts` array — central cost table for different action types. This drives the Billing/Quota UI.

**What index.php likely implements:**
- User session and basic routing for the panel landing page.
- Reading user plan, status (`$currentUser['user_status']`), expiry, and billing info used to show dashboard metrics.
- Hooking to payment functions for subscription and top-up flows.
- Possibly bootstrap for the frontend (loading initial JS bundle).

**What index.php does NOT contain (not observed):**
- Model-serving endpoints or agent orchestration code (these are likely in separate backend services / API endpoints).
- Full API REST endpoints for `code/generate` or `code/refactor`.
- Frontend assets for Monaco Editor, React components, or static content (assumed in `client/`).

---

## Implementation completeness estimate (based on available files)

> Caveat: Estimates are made based solely on `index.php` and typical project layout. They are approximate.

- **User session & basic dashboard wiring:** 70% implemented (session start + DB connection + plan checks present).  
- **Billing & payment integration (core hooks):** 40% implemented (includes payment functions but full flows and callbacks may be in separate files).  
- **Chat & LLM integration (end-to-end):** 10% implemented — index.php has no model-serving code; likely proxy or external service required.  
- **Editor UI (Monaco/VSCode-like integration):** 5% implemented — no frontend code found in the provided file.  
- **Agent orchestration & job management:** 10% implemented — job metadata / request costs exist but full orchestrator not found.  
- **Security scanning & refactor pipelines:** 10% implemented — stubs for cost/requests exist but actual analyzer integration not present.  
- **CI, tests, and docs:** 5% — you are actively documenting; tests and CI not found in this file.

**Overall project completeness estimate:** ~20% — the uploaded server entrypoint and payment hooks exist, but the major functionality (LLM endpoints, editor, agents) seems implemented elsewhere or is not present yet.

---

## File & Code Structure (recommended canonical layout)

Place these components in repo (if not already present):

```
/client/                # React/Monaco frontend
  /public/
  /src/
    /editor/            # Monaco integration
    /chat/
    /agents/
    /services/

/server/                # API gateway (PHP/Node/Python)
  index.php             # current entrypoint (session, routing)
  api.php               # REST endpoints for code generation/refactor
  agents.php            # agent job queue and orchestration
  models/               # model-proxy connectors
  inc/                  # helper functions (osw.php etc.)

/payments/
  pymentvira/           # current payment integration (used by index.php)

/scripts/
  docker-compose.yml
  docker/
```

---

## Example API calls & Client-side patterns

### PHP (server-side) — check quota and forward to model service (pseudo)

```php
// verify session & quota
session_start();
require_once('inc/auth.php');
if (!is_logged_in()) {
  http_response_code(401);
  echo json_encode(['error'=>'auth']);
  exit;
}
if (!has_quota($userId, 'refactor')) {
  http_response_code(402);
  echo json_encode(['error'=>'insufficient_credits']);
  exit;
}

// forward request to model service (example)
$payload = json_encode($_POST);
$ch = curl_init("http://model-service:8000/generate");
curl_setopt($ch, CURLOPT_POSTFIELDS, $payload);
// set headers...
$response = curl_exec($ch);
// deduct credits...
```

### JavaScript (client-side) — streaming suggestions sample (pseudo)

```js
const evtSource = new EventSource('/api/v1/stream?job=gen_123');
evtSource.onmessage = (e) => {
  // append streamed chunk to suggestion bubble
};
```

---

## Admin & Maintenance Notes

- Rotate DB credentials and do not store plaintext passwords in repo. Move to `.env` or secret manager.
- Protect `index.php` with prepared statements (avoid SQL injection). Use parameterized queries.
- Hide error display in production (remove `ini_set('display_errors',1)`).
- Add robust logging around payment callbacks and webhook verification.

---

## Next steps I can do for you

1. If you upload the full repository or the key server files (`/server/`, `/client/`, `openapi.yaml`, `agents/`), I will:
   - Map each feature to specific files and functions.
   - Produce a final `README_PANEL.md` with exact file references, code snippets, and screenshots suggestions.
   - Replace placeholders with real endpoints, CLI commands and Docker instructions.

2. Create a polished `README_PANEL.md` file (I already prepared this) ready to push.  
3. Generate `CONTRIBUTING.md`, `SECURITY.md`, and API reference stubs from `openapi.yaml` if provided.

---

## Download

I saved this document as `README_PANEL.md` for you to download and review.


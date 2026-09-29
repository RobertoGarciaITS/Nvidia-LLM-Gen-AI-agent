# NemoClaw Course Setup Preflight

**ID:** NVIDIA-NCL-COURSE-PREFLIGHT-001  
**Version:** 0.1  
**Status:** ACTIVE  
**Scope:** Course-level gate before lesson execution.

## Purpose

Separate the browser/model setup required by the DLI lessons from the later NemoClaw runtime setup. This prevents NemoClaw, OpenShell, and OpenClaw runtime checks from incorrectly blocking early browser lessons.

## Canonical source

- NVIDIA DLI course home: https://nvdli.github.io/NemoClawDLI/nemoclaw/index.html

## Dependency model

```text
COURSE SETUP
├── Browser / model routes
│   ├── chat API base URL
│   ├── chat model ID
│   ├── bearer credential (never record its value)
│   ├── DLI relay or reachable custom HTTPS endpoint
│   ├── embedding API base URL
│   ├── embedding model ID
│   ├── embedding credential (never record its value)
│   └── request handling: timeout / retries
├── Modules 1–2: browser learning path
└── NemoClaw runtime gate
    ├── NemoClaw blueprint
    ├── OpenShell sandbox
    ├── OpenClaw
    ├── inference provider/model compatibility
    └── Brev launchable or local equivalent
        └── required for the later runtime-focused modules
```

## Gate A — Browser / model route preflight

Before a lesson makes a chat-model request, record without secrets:

- chat API base URL;
- exact chat model ID;
- authentication present: YES/NO only;
- DLI relay enabled/disabled or custom endpoint;
- configured timeout;
- automatic retries setting;
- connectivity/model request result.

Before an embedding exercise, additionally record:

- embedding API base URL;
- exact embedding model ID;
- embedding authentication present: YES/NO only;
- embedding request result.

Chat and embedding routes are independent. A passing chat route does not imply a passing embedding route.

## Gate B — Failure evidence

Preserve:

- lesson and section;
- cell/example label;
- selected model ID;
- HTTP/error text;
- timestamp;
- partial output when present.

Never store API keys.

Classification:
- HTTP 401/403 → credential/access investigation;
- HTTP 429 → rate-limit investigation;
- HTTP 5xx → provider/relay investigation;
- timeout → no response headers or stream data within configured wait; diagnose before increasing retries.

For state-changing operations, verify whether the first attempt already changed state before retrying.

## Gate C — NemoClaw runtime preflight

Do not use the NemoClaw/OpenShell/OpenClaw runtime gate as a prerequisite for a browser-only lesson unless that lesson explicitly requires it.

Before the runtime-focused course path, record and verify:

- NemoClaw version;
- OpenShell version;
- OpenClaw version;
- model and inference provider;
- host OS / distribution / kernel / architecture;
- GPU if applicable;
- container/runtime driver;
- sandbox state;
- effective policy behavior;
- model connectivity;
- execution date.

## Acceptance criteria

A browser lesson may proceed when all dependencies it actually uses are PASS.

Allowed results:
- PASS
- PASS_WITH_OBSERVATIONS
- BLOCKED_CREDENTIAL
- BLOCKED_MODEL
- BLOCKED_PROVIDER
- BLOCKED_NETWORK
- BLOCKED_ENVIRONMENT
- FAILED_REQUIRES_ANALYSIS

A later runtime lesson additionally requires Gate C.

## Current execution state — 2026-09-28

- Course home/setup: READ
- Course setup architecture: VALIDATED_FROM_SOURCE
- Chat route values: PENDING_OBSERVATION
- Embedding route values: PENDING_OBSERVATION
- 01a runtime dependency on NemoClaw/OpenShell/OpenClaw: NOT_ESTABLISHED_AS_REQUIRED_BY_COURSE_HOME
- NemoClaw runtime preflight: DEFERRED_UNTIL_REQUIRED
- Next gate: observe and verify the configured chat route without exposing the API key.

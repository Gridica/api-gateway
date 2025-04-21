# Gridica API Gateway

Gridica API Gateway is the public-facing entrypoint of the Gridica decentralized inference network. It receives user requests, validates access, and forwards jobs to the internal control layer for execution.

## Overview

The gateway supports multiple request formats, including OpenAI-compatible and Gridica-native schemas. All incoming requests are normalized into internal job objects and assigned unique job IDs. Based on configuration, the gateway handles both synchronous and asynchronous workflows.

Access is key-based. Each request is matched against usage constraints, model permissions, and supported features such as streaming, polling, and batching.

## Responsibilities

- Accept inference requests over HTTPS
- Validate access keys and enforce rate/usage limits
- Normalize request bodies and route to job queue
- Return immediate results or job IDs based on mode
- Support both OpenAI-compatible and extended Gridica-native input formats

## Supported Modes

- **sync**: direct response for lightweight or single jobs
- **async / polling**: return `job_id`, result retrieved later
- **batch**: submit multiple tasks, each returns its own `job_id`
- **stream**: partial output (supported only in OpenAI-compatible format)

## Supported Task Types

- Text generation (completion/chat)
- Embeddings
- Image-to-text (captioning)
- Vision-chat (text + image, limited)
- Audio transcription (optional)
- TTS, video captioning (planned)

The gateway does not execute inference directly. It interfaces with the orchestration layer to assign jobs and deliver results.

## Development Status

This repository contains the specification and intake logic for the API Gateway. It is part of the Gridica control layer and will be extended as more request formats and client types are integrated.

## Resources

- [Project site](https://gridica.network)
- [Overview](https://gridica.gitbook.io/v1)
- [API gateway role](https://gridica.gitbook.io/v1/system-architecture/gridica-server-layer/api-gateway)

## License

MIT License

# AMD gateway reasoning catalog

`amd-gateway-reasoning.json` records the default and supported reasoning levels
verified through the AMD gateway's `/Unified/v1/responses` endpoint. It is consumed
by `yuychang/ai-cli-setup` when generating `~/.codex/models.json`; it does not change
the bundled OpenAI model catalog.

The levels were verified on November 17, 2026 with short synthetic requests and
invalid-value controls. Sol `low` and Qwen `medium` also completed streaming
requests with reasoning summaries enabled. These checks establish API
compatibility, not a reasoning-quality benchmark.

Models that accepted arbitrary invalid effort values are deliberately omitted:
GPT-oss 120B, Claude Fable/Opus/Sonnet/Haiku, GLM 5.3 Flash, and Gemini 4 Argon.
They retain their single configured effort until the gateway adapter's behavior
can be verified. Qwen does not accept `high`; Sol and Astra do not accept `none`.

To update the catalog, verify each model's accepted levels, confirm rejection of
invalid values, and keep its default among the supported levels. Do not copy
OpenAI's bundled levels to gateway models without verification. `ultra` is a
local Codex multi-agent alias and is not advertised as a gateway API value.

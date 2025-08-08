# Patch Notes

This document summarizes the changes in each patch.

## fix: remove read_file

**Description:** Removes the `read_file` tool from the tool filtering list in prompt conversion. Results from the `read_file` tool will now be included in the language model prompt.

**Link:** [bc5ec74](https://github.com/sameinc/ai/commit/bc5ec74bae7567435fbdba7d6c25f470f5f0fd6d)

## fix: ensure valid message structure in Google Generative AI conversion

**Description:** Prevents creation of empty messages by ensuring `assistant` messages are only added to Google Generative AI message list if they contain valid parts.

**Link:** [d3e57a4](https://github.com/sameinc/ai/commit/d3e57a4489bea98f954be124865b324103492935)

## fix: prevent processing of aborted requests in chat message updates

**Description:** Improves robustness of the `use-chat` hook by adding abortion check in `onUpdate` callback to prevent processing aborted requests during chat message updates.

**Link:** [6a88b90](https://github.com/sameinc/ai/commit/6a88b906cf50b7a71029d98f98ca873b3db8cd37)

## feat: implement non-blocking tool call execution with error handling and tracking

**Description:** Improves tool call handling in `process-chat-response` with non-blocking execution, error handling, and tracking. Prevents response stream blocking while waiting for tool calls and improves robustness.

**Link:** [c6ca786](https://github.com/sameinc/ai/commit/c6ca786435f9a0c8e37a424013fe225f602fa72b)

## feat: add disable_parallel_tool_use option to tool choices and provider options

**Description:** Introduces `disable_parallel_tool_use` option for Anthropic provider in tool choices and provider options. Allows disabling parallel tool execution for sequential scenarios.

**Link:** [b0850c2](https://github.com/sameinc/ai/commit/b0850c26d46e202f4bc58dcb80139419f9b00b44)

## fix: ensure cache control is applied correctly for the last message in prompt conversion

**Description:** Corrects cache control logic in prompt conversion to apply cache control only when processing the last message in the last block.

**Link:** [77038ab](https://github.com/sameinc/ai/commit/77038ab70ed77485ae006d73baab61c84f2d68be)

## feat: auto anthropic cache control

**Description:** Introduces automatic cache control for Anthropic provider. Allows cache configuration through `providerOptions` and auto-applies cache control to last tool definition and message, excluding 'thinking' steps.

**Link:** [38feefa](https://github.com/sameinc/ai/commit/38feefa7947a475047b3fba0609e8705c7185a9d)

## fix: step / error / generate_image

**Description:** Multiple fixes: 1) Prevents `generate_image` tool results from being sent to language model. 2) Improves error handling in `use-chat` hook by tracking error state. 3) Refactors `step` calculation for consistency.

**Link:** [3afbb7f](https://github.com/sameinc/ai/commit/3afbb7fa20309346d74c2279164821cae81c45a1)

## feat: extend tool result filtering in prompt conversion to include 'read_file' tool name

**Description:** Extends tool result filtering in prompt conversion to include 'read_file' tool name. Results from `read_file` tool will be excluded from language model prompt.

**Link:** [22af3e3](https://github.com/sameinc/ai/commit/22af3e35bcc126068f31ad11d1ac6cfc85b3bb50)

## feat: extend tool result filtering in prompt conversion to include 'deploy' tool name

**Description:** Extends tool result filtering to include 'deploy' tool name. Results from `deploy` tool will be excluded from language model prompt.

**Link:** [e294aad](https://github.com/sameinc/ai/commit/e294aad22407fd7f5a14818a77e43014979f6425)

## feat: extend tool result filtering in prompt conversion to include 'versioning' tool name

**Description:** Extends tool result filtering to include 'versioning' tool name. Results from `versioning` tool will be excluded from language model prompt.

**Link:** [433ba82](https://github.com/sameinc/ai/commit/433ba822d969f08296c0400b1fbbec55cfeb8826)

## feat: implement caching mechanism for user content in Google Generative AI model to enhance performance and session management

**Description:** Implements caching mechanism for user content in Google Generative AI model. Includes new settings for cached sessions, `cacheContents` method, and updates to `doGenerate` and `doStream` methods.

**Link:** [6b9aadef](https://github.com/sameinc/ai/commit/6b9aadef5e1c2e8b4a590c7eddf918a3214aadaa)

## refactor: streamline user message handling for tool responses in chat message conversion

**Description:** Refactors user message handling for tool responses in chat message conversion. Streamlines logic for converting tool results to user messages (for Azure OpenAI) and improves code clarity.

**Link:** [5ab5c88](https://github.com/sameinc/ai/commit/5ab5c88e776fa62b5dd990e015bf4164cd31d746)

## fix: update image MIME type detection to use a more robust method for Uint8Array data in prompt conversion

**Description:** Updates image MIME type detection with more robust method for Uint8Array data in prompt conversion. New `detectMimeType` function is more flexible for future MIME type detection.

**Link:** [d7699af](https://github.com/sameinc/ai/commit/d7699af7761f3f0172498c271210596240cf1222)

## feat: enhance chat message conversion to support OpenAI and Azure providers with improved tool result handling

**Description:** Enhances chat message conversion to support OpenAI and Azure OpenAI providers with improved tool result handling. Ensures correct formatting for each provider.

**Link:** [c61e67c](https://github.com/sameinc/ai/commit/c61e67cc90280950316d61c7f1f8ea07b5342d57)

## feat: add default case for unhandled message parts in chat message conversion

**Description:** Adds default case for unhandled message parts in chat message conversion. Ensures unhandled parts are serialized to JSON string to prevent errors.

**Link:** [62aedeb](https://github.com/sameinc/ai/commit/62aedebc079e43564eca1e12b3784fc6ae89971d)

## feat: improve image URL handling and refine tool result filtering in prompt conversion

**Description:** Improves image URL handling and refines tool result filtering. Prevents image downloads when model supports image URLs and ensures correct handling of image parts in tool responses.

**Link:** [7231d8f](https://github.com/sameinc/ai/commit/7231d8f57b53474e5846b03ad738dcd173d78ec9)

## feat: add handling for vertex_event type and improve error reporting for unsupported chunk types

**Description:** Adds handling for `vertex_event` type and improves error reporting for unsupported chunk types. Ensures graceful handling and more informative error messages.

**Link:** [f72a45c](https://github.com/sameinc/ai/commit/f72a45c18e5e85159f8055094f158d96c6ee5b12)

## feat: enhance tool result processing and improve image URL extraction in language model prompt conversion

**Description:** Enhances tool result processing and image URL extraction in prompt conversion. Refactors `downloadAssets` function and introduces `convertToolCallPartToLanguageModelPart` function for better tool call transformation.

**Link:** [690c74e](https://github.com/sameinc/ai/commit/690c74e25cbe1bfe21c5ff0f124abf4071fdcbbc)

## feat: add provider metadata support in chat API and data stream handling

**Description:** Adds `providerMetadata` support in chat API and data stream handling. Allows additional metadata from language model providers to pass through streaming and chat interfaces.

**Link:** [481f121](https://github.com/sameinc/ai/commit/481f121904ad241a2b7332e9350d9a27c492c299)

## refactor: simplify tool invocation result handling and remove exhaustive check for unsupported roles

**Description:** Simplifies tool invocation result handling and removes exhaustive check for unsupported roles. Makes `convertToCoreMessages` function more flexible for diverse message structures.

**Link:** [0f12931](https://github.com/sameinc/ai/commit/0f1293130fe6808674525c6ded89c804f340d10c)

## feat: add vertex_event type to anthropic messages schema and improve image data handling

**Description:** Adds `vertex_event` type support to Anthropic messages schema for better Vertex AI usage metadata handling. Improves image data handling and adds null checks for robustness.

**Link:** [6d4451c](https://github.com/sameinc/ai/commit/6d4451c1e8640ec6d66225af3f6ff25c18727b7b)

## feat: add provider options support in core message conversion

**Description:** Adds `providerOptions` support in core message conversion. Allows provider-specific options to be passed with messages for fine-grained control.

**Link:** [71778e3](https://github.com/sameinc/ai/commit/71778e37b9afa9e2effab0d96b74e70aaf7f111e)

## feat: remove logOriginalPrompt

**Description:** Removes `logOriginalPrompt` option and associated logging functionality from `run-tools-transformation.ts` and `stream-text.ts` files.

**Link:** [ceccbb9](https://github.com/sameinc/ai/commit/ceccbb95ec5dcc6077a8caf5b53c0e9801d1fa29)

## refactor: standardize tool call max tokens finish event type

**Description:** Refactors and standardizes event type from `tool_call_max_tokens_finish` to `tool-call-max-tokens-finish` across multiple files. Improves consistency and enhances error messages for `edit_code` tools.

**Link:** [d569255](https://github.com/sameinc/ai/commit/d569255d957e2d64b31ded7c1f15ad32097e3659)

## feat: enhance tool call max tokens finish with tool invocation details

**Description:** Enhances `tool_call_max_tokens_finish` event by including `toolInvocation` details. Provides comprehensive information about tool calls that exceed token limits and introduces `max-tokens` state.

**Link:** [e407e28](https://github.com/sameinc/ai/commit/e407e28c52ac38aa9371911ef982f24be805cb27)

## feat: add tool call max tokens finish stream part

**Description:** Introduces `tool_call_max_tokens_finish` stream part type to indicate when tool calls exceed maximum token limits. Updates `streamText` function and related types for better control and feedback.

**Link:** [dec37e2](https://github.com/sameinc/ai/commit/dec37e2ebd024bea7b5373990f7aea4f0c476ab7)

## feat: no build

**Description:** Modifies `pnpm-workspace.yaml` to exclude `packages/solid`, `packages/svelte`, and `packages/vue` directories from workspace. I don't want to build them when I build.

**Link:** [ebef3d7](https://github.com/sameinc/ai/commit/ebef3d7e5c71b14d1969fe1a5df535853dda8bba)

## feat: patch

**Description:** Reintroduces `logOriginalPrompt` option and associated logging functionality. Includes various fixes and refactorings across `use-chat.ts`, `process-chat-response.ts`, and `should-resubmit-messages.ts` for better message handling.

**Link:** [4c60f0a](https://github.com/sameinc/ai/commit/4c60f0aed22871a5df4a5df864fd5a6d73d70664)

## feat: add onToolCallMaxTokensFinish to streamText

**Description:** Introduces `onToolCallMaxTokensFinish` callback to `streamText` function and related UI utilities. Triggered when tool calls exceed maximum token limits, includes new stream part and type updates.

**Link:** [651a78c](https://github.com/sameinc/ai/commit/651a78cdb2617c7bd0f0e41a4a7ab53f0bd60c19)

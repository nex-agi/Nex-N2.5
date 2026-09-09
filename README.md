<div align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="./figures/NEX_logo-dark.svg">
    <img src="./figures/NEX_logo.svg" width="180" alt="Nex-AGI">
  </picture>

# Nex-N2.5

**Build agents that browse, code, and use computers.**

Multimodal mini & Pro · 1.6T-parameter text-only Max · Long-horizon agent tasks

[![Try Pro on OpenRouter](https://img.shields.io/badge/Try_Pro-OpenRouter-2563EB?style=for-the-badge)](https://openrouter.ai/nex-agi/nex-n2.5-pro:free) [![Try mini on OpenRouter](https://img.shields.io/badge/Try_mini-OpenRouter-2563EB?style=for-the-badge)](https://openrouter.ai/nex-agi/nex-n2.5-mini:free)

[Model weights](#open-source) · [API quickstart](#quick-start) · [Benchmarks](#performance) · [Self-hosting](#usage) · [Website](https://nex-agi.com/)

**English** | [简体中文](./README_zh-CN.md)

⭐ **Building agents? [Star this repo](https://github.com/nex-agi/Nex-N2.5) to keep the models, benchmarks, and deployment guides handy.**

</div>

Nex-N2.5 is Nex-AGI's model family for tasks that take many steps: searching the web, working with software, writing and testing code, and using tools. **mini and Pro** use visual feedback to interpret interfaces and check their actions. **Max** brings a 1.6-trillion-parameter Mixture-of-Experts (MoE) foundation to text-based coding, research, and tool use.

## Highlights

| Web research | GUI grounding | Computer use |
| :---: | :---: | :---: |
| **92.6** · BrowseComp | **87.4** · OSWorld-G | **82.2** · OSWorld-Verified |
| Nex-N2.5-Max | Nex-N2.5-Pro | Nex-N2.5-Pro |

Selected scores from the evaluations reported in this repository. Max on BrowseComp and Pro on OSWorld-G have the highest reported scores **among the models listed in our tables**. See the [full results and evaluation settings](#performance) for comparisons, harnesses, and score sources.

- **Build computer and browser agents.** mini and Pro combine visual understanding with actions and feedback, supporting workflows that need to inspect an interface and adjust the next step.
- **Connect coding and research tools.** The family supports function calling; coding evaluations use the open-source [NexAU agent framework](https://github.com/nex-agi/NexAU).
- **Try a hosted model or deploy weights.** Start with Pro or mini on OpenRouter. Download mini or Max for self-hosting; see the [release status](#open-source) for Pro.

## Quick start

### Try it in your browser

Open **[Nex-N2.5-Pro](https://openrouter.ai/nex-agi/nex-n2.5-pro:free)** or **[Nex-N2.5-mini](https://openrouter.ai/nex-agi/nex-n2.5-mini:free)** on OpenRouter. The hosted routes are currently listed as free; an OpenRouter account and its usage limits apply.

Try a coding task: *“Review this function for edge cases, propose a fix, and write tests that would catch the bug.”* Paste your function after the prompt.

### Make your first API call

Create an [OpenRouter API key](https://openrouter.ai/settings/keys), set `OPENROUTER_API_KEY`, and run this in Bash:

```bash
export OPENROUTER_API_KEY="your-api-key"

curl --fail-with-body https://openrouter.ai/api/v1/chat/completions \
  -H "Authorization: Bearer $OPENROUTER_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "nex-agi/nex-n2.5-pro:free",
    "messages": [
      {
        "role": "user",
        "content": "Write a Python function that merges overlapping intervals, with tests for empty input, touching intervals, and nested intervals."
      }
    ],
    "temperature": 0.7,
    "top_p": 0.95,
    "top_k": 40,
    "reasoning": {"effort": "medium"}
  }'
```

To try mini, change `model` to `nex-agi/nex-n2.5-mini:free`. Model IDs and route availability can change; check the [OpenRouter model catalog](https://openrouter.ai/api/v1/models). See the [API guide](https://openrouter.ai/docs/quickstart) for other languages and streaming.

For tasks that actually browse, click, or execute code, connect the model to an agent runtime and the relevant tools. A chat request alone does not run those actions. [NexAU](https://github.com/nex-agi/NexAU) is the framework used for our coding evaluations; NexCUA, our computer-use evaluation harness, is planned for open-source release.

## Choose a model

| Model | Designed for | Native inputs | Hosted access |
| --- | --- | --- | --- |
| **Nex-N2.5-mini** | Computer and browser agents with a smaller self-hosting footprint | Text + images | [OpenRouter](https://openrouter.ai/nex-agi/nex-n2.5-mini:free) |
| **Nex-N2.5-Pro** | Visual agent workflows, GUI grounding, and computer use | Text + images | [OpenRouter](https://openrouter.ai/nex-agi/nex-n2.5-pro:free) |
| **Nex-N2.5-Max** | Text-based research, coding, and tool use at 1.6T-parameter scale | Text only | Self-host |

Hosted providers may expose fewer input modalities than the underlying model. As of **2026-09-09**, OpenRouter lists Pro with text and image inputs, and mini with text input only.

## Open Source

Release status checked on **2026-09-09** against the Hugging Face file listings. The model cards list **Apache-2.0**; consult each model card and its license when using the weights.

| Model | Hugging Face status | Downloads / model card | Reference deployment |
| --- | --- | --- | --- |
| **mini** | Weights available | [Hugging Face](https://huggingface.co/nex-agi/Nex-N2.5-mini) · [ModelScope](https://modelscope.cn/models/nex-agi/Nex-N2.5-mini) | 1 node · 2 × H100 |
| **Pro** | Model card available; weights pending | [Hugging Face](https://huggingface.co/nex-agi/Nex-N2.5-Pro) · [ModelScope](https://modelscope.cn/models/nex-agi/Nex-N2.5-Pro) | 1 node · 8 × H100 |
| **Max** | Weights available | [Hugging Face](https://huggingface.co/nex-agi/Nex-N2.5-Max) · [ModelScope](https://modelscope.cn/models/nex-agi/Nex-N2.5-Max) | 2 nodes · 16 × H200 total |

These are reference configurations, not minimum hardware requirements. Find all three model cards in the [Hugging Face collection](https://huggingface.co/collections/nex-agi/nex-n25), or jump to the [Docker deployment commands](#docker-deployment).

## Performance

We evaluate Nex-N2.5 across coding, agentic workflows, computer use, and multimodal understanding.

![Nex-N2.5 Benchmark Overview: Text and Multimodal](./figures/Nex-N2.5-Benchmark-white.png)

The tables below compare **Nex-N2.5-mini**, **Nex-N2.5-Pro**, and **Nex-N2.5-Max** with leading models across our evaluation suite.<sup><a href="#benchmark-note-1">1</a>, <a href="#benchmark-note-2">2</a></sup> **Bold** marks the best result in each benchmark, including ties; — indicates unavailable data.<sup><a href="#benchmark-note-10">10</a></sup>

### Text Benchmarks

<!-- Keep benchmark rows first in each tbody; only section labels receive GitHub's alternating row background. -->
<table>
  <thead>
    <tr>
      <th align="left">Benchmark</th>
      <th align="center">Nex-N2.5-mini</th>
      <th align="center">Nex-N2.5-Pro</th>
      <th align="center">Nex-N2.5-Max</th>
      <th align="center">Claude Opus 5</th>
      <th align="center">GPT-5.6 Sol</th>
      <th align="center">Kimi-K3</th>
      <th align="center">GLM-5.3</th>
      <th align="center">DeepSeek-V4-Pro-0813<sup><a href="#benchmark-note-4">4</a></sup></th>
      <th align="center">Qwen3.8-Max</th>
    </tr>
    <tr>
      <th colspan="10" align="left">CODING<sup><a href="#benchmark-note-3">3</a></sup></th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Terminal-Bench 2.1</td><td align="center">73.4</td><td align="center">82.7</td><td align="center">86.1</td><td align="center"><b>89.1</b></td><td align="center">88.8</td><td align="center">88.3</td><td align="center">88.2</td><td align="center">87.9</td><td align="center">86.6</td></tr>
  </tbody>
  <tbody>
    <tr><td>SWE-Bench Pro</td><td align="center">43.8</td><td align="center">61.2</td><td align="center">65.7</td><td align="center"><b>79.2</b></td><td align="center">64.6</td><td align="center">63.3</td><td align="center">64.6</td><td align="center">55.4</td><td align="center">67.7</td></tr>
  </tbody>
  <tbody>
    <tr><td>DeepSWE v1.1</td><td align="center">36.1</td><td align="center">55.8</td><td align="center">65.6</td><td align="center"><b>73.7</b></td><td align="center">72.7</td><td align="center">67.5</td><td align="center">66.9</td><td align="center">62.8</td><td align="center">69.3</td></tr>
    <tr><th colspan="10" align="left">AGENTIC</th></tr>
  </tbody>
  <tbody>
    <tr><td>AutomationBench v1.0.6<sup><a href="#benchmark-note-5">5</a></sup></td><td align="center">32.3</td><td align="center">44.2</td><td align="center">50.2</td><td align="center"><b>50.3</b></td><td align="center">45.8</td><td align="center">46.7</td><td align="center">48.2</td><td align="center">43.2</td><td align="center">39.8</td></tr>
  </tbody>
  <tbody>
    <tr><td>Toolathlon Verified</td><td align="center">54.6</td><td align="center">68.5</td><td align="center">74.7</td><td align="center"><b>76.5</b></td><td align="center">74.9</td><td align="center"><b>76.5</b></td><td align="center">73.0</td><td align="center">74.1</td><td align="center">72.5</td></tr>
  </tbody>
  <tbody>
    <tr><td>GDPval-AA v2</td><td align="center">1446</td><td align="center">1628</td><td align="center">1713</td><td align="center"><b>1831</b></td><td align="center">1711</td><td align="center">1675</td><td align="center">1763</td><td align="center">1580</td><td align="center">1717</td></tr>
  </tbody>
  <tbody>
    <tr><td>Job Bench</td><td align="center">28.5</td><td align="center">41.4</td><td align="center">53.6</td><td align="center"><b>65.7</b></td><td align="center">45.4</td><td align="center">52.9</td><td align="center">58.2</td><td align="center">54.1</td><td align="center">53.4</td></tr>
  </tbody>
  <tbody>
    <tr><td>BrowseComp<sup><a href="#benchmark-note-6">6</a></sup></td><td align="center">83.4</td><td align="center">89.7</td><td align="center"><b>92.6</b></td><td align="center">90.8</td><td align="center">90.4</td><td align="center">91.2</td><td align="center">—</td><td align="center">—</td><td align="center">—</td></tr>
  </tbody>
</table>

### Multimodal Benchmarks

<table>
  <thead>
    <tr>
      <th align="left">Benchmark</th>
      <th align="center">Nex-N2.5-mini</th>
      <th align="center">Nex-N2.5-Pro</th>
      <th align="center">MiniMax-M3</th>
      <th align="center">Claude Opus 5</th>
      <th align="center">GPT-5.6 Sol</th>
      <th align="center">Kimi-K3</th>
      <th align="center">GLM-5.3-Flash</th>
      <th align="center">DeepSeek-V4-Flash-Vision</th>
      <th align="center">Qwen3.8-Max</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>OSWorld-Verified<sup><a href="#benchmark-note-8">8</a></sup></td><td align="center">71.2</td><td align="center">82.2</td><td align="center">75.2</td><td align="center">83.4</td><td align="center">83.2</td><td align="center">84.8</td><td align="center">62.3</td><td align="center">76.7</td><td align="center"><b>86.1</b></td></tr>
  </tbody>
  <tbody>
    <tr><td>OSWorld-2</td><td align="center">30.5</td><td align="center">56.4</td><td align="center">22.3</td><td align="center"><b>68.3</b></td><td align="center">62.7</td><td align="center">58.3</td><td align="center">—</td><td align="center">—</td><td align="center">46.7</td></tr>
  </tbody>
  <tbody>
    <tr><td>WebTest<sup><a href="#benchmark-note-8">8</a>, <a href="#benchmark-note-9">9</a></sup></td><td align="center">48.6</td><td align="center">52.8</td><td align="center">—</td><td align="center">—</td><td align="center"><b>54.0</b></td><td align="center">—</td><td align="center">—</td><td align="center">—</td><td align="center">52.3</td></tr>
  </tbody>
  <tbody>
    <tr><td>WebArena-Verified<sup><a href="#benchmark-note-8">8</a></sup></td><td align="center">63.4</td><td align="center">67.6</td><td align="center">—</td><td align="center">—</td><td align="center">69.7</td><td align="center"><b>71.6</b></td><td align="center">—</td><td align="center">62.3</td><td align="center">66.8</td></tr>
  </tbody>
  <tbody>
    <tr><td>OSWorld-G</td><td align="center">82.9</td><td align="center"><b>87.4</b></td><td align="center">—</td><td align="center">76.8</td><td align="center">77.7</td><td align="center">79.6</td><td align="center">83.3</td><td align="center">59.4</td><td align="center">84.9</td></tr>
  </tbody>
  <tbody>
    <tr><td>Vision2Web<sup><a href="#benchmark-note-7">7</a></sup></td><td align="center">52.9</td><td align="center">68.2</td><td align="center">59.0</td><td align="center">—</td><td align="center"><b>79.8</b></td><td align="center">—</td><td align="center">—</td><td align="center">—</td><td align="center">75.1</td></tr>
  </tbody>
  <tbody>
    <tr><td>SWE-MM</td><td align="center">25.5</td><td align="center">38.2</td><td align="center">—</td><td align="center"><b>59.4</b></td><td align="center">40.2</td><td align="center">37.3</td><td align="center">20.6</td><td align="center">39.2</td><td align="center">39.2</td></tr>
  </tbody>
  <tbody>
    <tr><td>OmniDoc</td><td align="center">89.7</td><td align="center">92.2</td><td align="center">91.6</td><td align="center">—</td><td align="center"><b>92.9</b></td><td align="center">91.1</td><td align="center">—</td><td align="center">—</td><td align="center">92.1</td></tr>
  </tbody>
</table>

<p id="benchmark-note-1"><sup>1</sup> <b>Score sources:</b> Where available, scores are drawn from official benchmark leaderboards and the latest evaluation reports published by model providers, including the Kimi-K3, Qwen3.8-Max, GLM-5.3, and HY4 reports. Results without a public source are obtained through our own evaluations.</p>
<p id="benchmark-note-2"><sup>2</sup> <b>Sampling parameters:</b> Our evaluations use <code>temperature = 0.7</code>, <code>top_p = 0.95</code>, and <code>top_k = 40</code>.</p>
<p id="benchmark-note-3"><sup>3</sup> <b>Evaluation harness:</b> Coding tasks are evaluated using the <a href="https://github.com/nex-agi/NexAU">NexAU</a> harness.</p>
<p id="benchmark-note-4"><sup>4</sup> <b>DeepSeek-V4-Pro:</b> Our evaluations use the DeepSeek-V4-Pro-0813 version.</p>
<p id="benchmark-note-5"><sup>5</sup> <b>AutomationBench:</b> We use the Public version.</p>
<p id="benchmark-note-6"><sup>6</sup> <b>BrowseComp:</b> We apply the Summary context-compaction strategy when the token usage exceeds 60% of the model’s context window.</p>
<p id="benchmark-note-7"><sup>7</sup> <b>Vision2Web:</b> We report the average score across the Frontend, Webpage, and Website categories, with Gemini-3.5-Flash as the VLM judge and GLM-5V-Turbo (Claude Code) as the GUI agent.</p>
<p id="benchmark-note-8"><sup>8</sup> Computer-use and browser-use benchmarks, including OSWorld, WebTest, and WebArena, are evaluated using our NexCUA harness. Grounding coordinates are normalized to a 0–1000 scale. The NexCUA project will be open-sourced soon.</p>
<p id="benchmark-note-9"><sup>9</sup> <b>WebTestBench:</b> These results are evaluated in <b>oracle mode</b>, using the ground-truth checklist to assess defect detection only, without checklist generation.</p>
<p id="benchmark-note-10"><sup>10</sup> <b>Notation:</b> Bold marks the best result in each benchmark, including ties; — indicates unavailable data.</p>

## Usage

### Docker Deployment

Use the prebuilt image **`nexagi/sglang:v0.5.18-nex-patch`**, which includes our customized SGLang fork. The following examples assume a Linux GPU host with Docker and NVIDIA Container Toolkit configured.

Download the model files, including the tokenizer, configuration, and matching `chat_template.jinja`. Replace `/path/to/your/model` with their absolute directory on the host. Docker mounts that directory at `/model`; all model and template paths in the container use `/model`.

#### Nex-N2.5-mini

Reference configuration: **1 node with 2 × H100**.

```bash
docker run --gpus all --shm-size 32g --ipc=host \
  -p 30000:30000 \
  -v /path/to/your/model:/model \
  nexagi/sglang:v0.5.18-nex-patch \
  python3 -m sglang.launch_server \
    --model-path /model \
    --tp 2 \
    --host 0.0.0.0 --port 30000 \
    --reasoning-parser qwen3 \
    --tool-call-parser qwen3_coder \
    --chat-template /model/chat_template.jinja \
    --mamba-scheduler-strategy extra_buffer
```

#### Nex-N2.5-Pro

Reference configuration: **1 node with 8 × H100**. Pro weights are pending on Hugging Face as of 2026-09-09. Use this configuration once the weights and matching chat template are available, placing the template at `/path/to/your/model/chat_template.jinja` on the host.

<details>
<summary>Show Pro deployment command</summary>

```bash
docker run --gpus all --shm-size 32g --ipc=host \
  -p 30000:30000 \
  -v /path/to/your/model:/model \
  nexagi/sglang:v0.5.18-nex-patch \
  python3 -m sglang.launch_server \
    --model-path /model \
    --tp 8 \
    --host 0.0.0.0 --port 30000 \
    --reasoning-parser qwen3 \
    --tool-call-parser qwen3_coder \
    --chat-template /model/chat_template.jinja \
    --mamba-scheduler-strategy extra_buffer
```

</details>

#### Nex-N2.5-Max

Reference configuration: **2 nodes with 16 × H200 total**. Place the model files on both nodes, set the node rank and head-node address, and run the command on each node. Both nodes must be able to reach the distributed initialization address.

<details>
<summary>Show Max multi-node deployment command</summary>

```bash
# Set these on each node before launching:
export NODE_RANK=0  # 0 on the head node; 1 on the second node
export MASTER_ADDR="192.0.2.10"  # Replace with the reachable IP of the head node

docker run --gpus all --shm-size 32g --network host \
  -v /path/to/your/model:/model \
  nexagi/sglang:v0.5.18-nex-patch \
  python3 -m sglang.launch_server \
    --model-path /model \
    --trust-remote-code \
    --host 0.0.0.0 \
    --port 8000 \
    --nnodes 2 \
    --node-rank "${NODE_RANK}" \
    --dist-init-addr "${MASTER_ADDR}:5000" \
    --tp 16 \
    --pp-size 1 \
    --dp 1 \
    --ep-size 16 \
    --attention-backend dsv4 \
    --kv-cache-dtype fp8_e4m3 \
    --page-size 256 \
    --moe-a2a-backend deepep \
    --moe-runner-backend deep_gemm \
    --moe-dense-tp-size 1 \
    --deepep-mode auto \
    --context-length 262144 \
    --mem-fraction-static 0.84 \
    --chunked-prefill-size 8192 \
    --enable-mixed-chunk \
    --disable-overlap-schedule \
    --max-running-requests 64 \
    --cuda-graph-max-bs-decode 64 \
    --cuda-graph-backend-decode full \
    --cuda-graph-backend-prefill disabled \
    --chat-template /model/chat_template.jinja \
    --reasoning-parser deepseek-r1 \
    --tool-call-parser qwen3_coder
```

</details>

### Send a request to your server

The examples expose an OpenAI-compatible endpoint at `http://localhost:30000/v1` for mini and Pro, or `http://localhost:8000/v1` on the Max head node. After the server is ready, query `/v1/models` to find its served model ID:

```bash
curl --fail-with-body http://localhost:30000/v1/models
```

Set `model` to that ID and send Chat Completions requests to your server's `/v1/chat/completions` endpoint.

### Recommended Sampling Parameters

Our evaluations use the following settings, which we also recommend for generation:

| Parameter | Value |
| --- | --- |
| `temperature` | `0.7` |
| `top_p` | `0.95` |
| `top_k` | `40` |

### Thinking Modes

**OpenRouter:** set `reasoning.effort` in your request, as in the [quickstart](#make-your-first-api-call). See OpenRouter's [reasoning controls](https://openrouter.ai/docs/guides/best-practices/reasoning-tokens) for gateway behavior.

**Self-hosted models:** use the controls supported by the downloaded chat template. The published mini and Max templates have different interfaces:

| Model / template | Control | Behavior |
| --- | --- | --- |
| [mini](https://huggingface.co/nex-agi/Nex-N2.5-mini/blob/main/chat_template.jinja) | `reasoning_effort="none"` | Respond without a reasoning trace. |
| mini | `reasoning_effort="medium"` (default) | Adaptive thinking. |
| mini | `reasoning_effort="high"` | Always enable thinking. |
| [Max](https://huggingface.co/nex-agi/Nex-N2.5-Max/blob/main/chat_template.jinja) | `enable_thinking` | Enable or disable thinking; defaults to `true`. |
| Max | `thinking_mode` | Controls reasoning history: `interleaved` (default), `full`, or `drop`. |

Pass template controls through your serving layer's supported chat-template arguments. Do not assume that an OpenRouter request field maps directly to a self-hosted template. For Pro self-hosting, consult its matching template when released.

### Function Calling

The deployment commands include `--tool-call-parser qwen3_coder`. Supply tool definitions in the request's `tools` field, execute returned tool calls in your application, and send the results back to the model to continue the task.

### Reasoning Parser

When the model produces a reasoning trace, configure SGLang to separate it from the final response:

- **Nex-N2.5-mini and Nex-N2.5-Pro:** `--reasoning-parser qwen3`
- **Nex-N2.5-Max:** `--reasoning-parser deepseek-r1`

The deployment commands include the appropriate parser. Parsing a reasoning trace and selecting a thinking mode are separate settings.

## Build with Nex-N2.5

Using Nex-N2.5 in an agent, a research workflow, or a deployment? [Share an example or report an issue](https://github.com/nex-agi/Nex-N2.5/issues). Include the model, runtime, and steps needed to reproduce your result so others can try it.

If this project is useful to you, **[give it a Star](https://github.com/nex-agi/Nex-N2.5)** and share the repository with someone building agents. Use GitHub's **Watch** menu if you would also like notifications about repository activity.

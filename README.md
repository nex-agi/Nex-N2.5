<div align="center">
<img src="./figures/NEX_logo.svg" width="20%"/>
</div>

---

<div align="center">
🤗 <a href="https://hf.co/collections/nex-agi/nex-n2.5"><b>Model</b></a>&nbsp&nbsp | &nbsp&nbsp
💻 <a href="https://github.com/nex-agi/Nex-N2.5"><b>Github</b></a>&nbsp&nbsp | &nbsp&nbsp
🧭 <a href="https://www.modelscope.cn/collections/nex-agi/Nex-N2.5"><b>ModelScope</b></a>&nbsp&nbsp | &nbsp&nbsp
🚀 <a href="https://nex-agi.com"><b>Nex-AGI</b></a>&nbsp&nbsp | &nbsp&nbsp
🔀 <a href="https://openrouter.ai/nex-agi/Nex-N2.5-Pro:free"><b>OpenRouter (Enjoy two weeks free starting June 9!)</b></a>
</div>

# Nex-N2.5

**An agentic model with Agentic Thinking.**

Today, we are officially releasing and open-sourcing our next-generation model, **Nex-N2.5** — an agent model built for real-world productivity scenarios. With first-tier coding and agentic capabilities, Nex-N2.5 keeps driving complex, long-horizon tasks forward in real environments to deliver stable, end-to-end results.

Over the past year, a paradigm shift led by Vibe Coding and Harness Engineering has been redefining the limits of LLM agents. From dialogue, to reasoning, to agents that execute long-horizon tasks with environmental feedback, the tasks models must handle keep growing harder, the contexts longer, and the environments more realistic. The core of next-generation model competition is no longer *whether a model can think*, but whether it can reliably and efficiently turn thinking into actions that are executable, verifiable, and iterable.

Rather than treating reasoning, tool use, and environment execution as separate capabilities, Nex-N2.5 unifies them through an **Agentic Thinking** framework that connects requirement understanding, task planning, code implementation, environmental feedback, evaluation and debugging, and continuous iteration into a single closed loop. The framework has two parts:

- **Adaptive Thinking** lets the model decide on its own when to think and how deeply — executing simple actions quickly while reasoning thoroughly on critical decisions.
- **Coherent Thinking** carries one consistent reasoning paradigm across general reasoning and diverse agentic tasks, staying consistent across tasks and modalities to enable stable capability transfer.

Across real agentic workflows — agentic coding, deep research, tool calling, and terminal execution — Nex-N2.5 reaches first-tier performance, with substantial gains over the previous-generation Nex-N1 on multiple authoritative benchmarks. In real productivity scenarios such as OpenClaw one-person-company workflows, end-to-end game development, and web and multimodal generation, it likewise demonstrates outstanding usability, robustness, and stability.

## Open Source

In keeping with our commitment to open source, we are releasing both **Nex-N2.5-Pro** and **Nex-N2.5-mini** as open-source models starting today.

- **Nex-N2.5-Pro:** [Hugging Face](https://huggingface.co/nex-agi/Nex-N2.5-Pro) | [ModelScope](https://www.modelscope.cn/models/nex-agi/Nex-N2.5-Pro)
- **Nex-N2.5-mini:** [Hugging Face](https://huggingface.co/nex-agi/Nex-N2.5-mini) | [ModelScope](https://www.modelscope.cn/models/nex-agi/Nex-N2.5-mini)
- **Early Access:** [SiliconFlow](https://cloud.siliconflow.cn/me/models?target=nex-agi%2FNex-N2.5-Pro)

We welcome developers and enterprises to integrate and try Nex-N2.5 and share their feedback.

## Performance

We evaluate Nex-N2.5 in real agentic workflows along three directions — agentic tasks, coding tasks, and general tasks — covering benchmarks across tool calling, search-based decision-making, software engineering, and terminal execution. Benchmark results will be added once the evaluations are complete.

Nex-N2.5 ships in two variants, both post-trained on the Qwen3.5 series: **Nex-N2.5-Pro** (built on `Qwen3.5-397B-A17B`) and **Nex-N2.5-mini** (built on `Qwen3.5-35B-A3B-Base`), covering different latency and quality trade-offs. The table below lists the benchmarks and comparison models in our evaluation suite. All scores are pending.

| Benchmark | **Nex-N2.5-mini** | **Nex-N2.5-Pro** | GPT-5.5 | Opus 4.7 | Kimi-K2.6 | GLM-5.1 | MiniMax M3 | DeepSeek-V4-Pro |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **Agent** |  |  |  |  |  |  |  |  |
| BrowseComp |  |  |  |  |  |  |  |  |
| GDPval |  |  |  |  |  |  |  |  |
| Toolathlon-Verified |  |  |  |  |  |  |  |  |
| AutomationBench |  |  |  |  |  |  |  |  |
| WildClawBench |  |  |  |  |  |  |  |  |
| WideSearch |  |  |  |  |  |  |  |  |
| TAU3 |  |  |  |  |  |  |  |  |
| **Coding & SWE** |  |  |  |  |  |  |  |  |
| SWE-Bench Pro |  |  |  |  |  |  |  |  |
| Terminal-Bench 2.1 |  |  |  |  |  |  |  |  |
| DeepSWE |  |  |  |  |  |  |  |  |
| SWE-Bench Verified |  |  |  |  |  |  |  |  |
| SWE Atlas QnA |  |  |  |  |  |  |  |  |
| SWE Atlas RF |  |  |  |  |  |  |  |  |
| SWE Atlas TW |  |  |  |  |  |  |  |  |
| **General & Reasoning** |  |  |  |  |  |  |  |  |
| GPQA Diamond |  |  |  |  |  |  |  |  |
| IFEval |  |  |  |  |  |  |  |  |
| Apex |  |  |  |  |  |  |  |  |

## Usage

### Local Deployment

> **Note:** For the best performance with Nex-series models, we recommend serving them with our customized `sglang` fork.

First, install our `sglang` fork:

```bash
# Use the customized `sglang` fork
git clone https://github.com/nex-agi/sglang.git
cd sglang

# Install the python packages
pip install --upgrade pip
pip install -e "python"
```

#### Nex-N2.5-Pro

Launch the server (example on two 8× H100 servers with CUDA 13.0):

```bash
# Multi-node (2 nodes). Run the same command on every node with:
#   <node-rank> = 0 on the head node, 1 on the other node
#   <node0-ip>  = IP of the head node (reachable from all others)
python -m sglang.launch_server \
  --model-path /path/to/your/model  \
  --tp 16 \
  --nnodes 2 \
  --node-rank <node-rank> \
  --dist-init-addr <node0-ip>:20000 \
  --reasoning-parser qwen3 \
  --tool-call-parser qwen3_coder \
  --mamba-scheduler-strategy extra_buffer
```

#### Nex-N2.5-mini

Launch the server (example on one 2× H100 server with CUDA 13.0):

```bash
python -m sglang.launch_server \
  --model-path /path/to/your/model  \
  --tp 2 \
  --reasoning-parser qwen3 \
  --tool-call-parser qwen3_coder \
  --mamba-scheduler-strategy extra_buffer
```

### Docker Deployment

We also provide a prebuilt Docker image with our customized `sglang` fork preinstalled: **`nexagi/sglang:v0.5.12`**. The launch command is the same as above.

#### Nex-N2.5-Pro

```bash
# Multi-node (2 nodes). Run the same command on every node with:
#   <node-rank> = 0 on the head node, 1 on the other node
#   <node0-ip>  = IP of the head node (reachable from all others)
docker run --gpus all --shm-size 32g --network host \
  -v /path/to/your/model:/model \
  nexagi/sglang:v0.5.12 \
  python3 -m sglang.launch_server \
    --model-path /model \
    --tp 16 \
    --nnodes 2 \
    --node-rank <node-rank> \
    --dist-init-addr <node0-ip>:20000 \
    --host 0.0.0.0 --port 30000 \
    --reasoning-parser qwen3 \
    --tool-call-parser qwen3_coder \
    --mamba-scheduler-strategy extra_buffer
```

#### Nex-N2.5-mini

Single node with 2× H100:

```bash
docker run --gpus all --shm-size 32g --ipc=host \
  -p 30000:30000 \
  -v /path/to/your/model:/model \
  nexagi/sglang:v0.5.12 \
  python3 -m sglang.launch_server \
    --model-path /model \
    --tp 2 \
    --host 0.0.0.0 --port 30000 \
    --reasoning-parser qwen3 \
    --tool-call-parser qwen3_coder \
    --mamba-scheduler-strategy extra_buffer
```

### Recommended Sampling Parameters

For the best generation quality, we recommend the following sampling parameters:

- `temperature`: 0.7
- `top_p`: 0.95
- `top_k`: 40

### Function Calling

Nex-series models support robust function-calling capabilities. To enable function calling, add the `--tool-call-parser qwen3_coder` flag when launching the server:

```bash
python -m sglang.launch_server --model-path /path/to/your/model --tool-call-parser qwen3_coder
```

### Reasoning Parser

Nex-series models emit explicit reasoning traces. Add the `--reasoning-parser qwen3` flag to parse the reasoning content separately from the final response. It can be combined with the function-calling parser above:

```bash
python -m sglang.launch_server --model-path /path/to/your/model --tool-call-parser qwen3_coder --reasoning-parser qwen3
```

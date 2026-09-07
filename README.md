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

**A next-generation family of agentic models built for long-horizon tasks in real-world environments.**

Today, Nex-AGI officially introduces **Nex-N2.5**, its next-generation family of agentic models.

Nex-N2.5 is available in three sizes: **mini**, **Pro**, and **Max**. Nex-N2.5-mini and Nex-N2.5-Pro continue to build on the multimodal foundations of Nex-N2, with focused improvements in computer use, web browsing, and visually grounded agentic capabilities. Nex-N2.5-Max is built on a 1.6-trillion-parameter, text-only Mixture-of-Experts (MoE) foundation model, marking our first complete post-training effort at trillion-parameter scale.

For long-horizon tasks in real-world environments, Nex-N2.5 further strengthens its ability to act continuously and self-correct through visual feedback. The models can operate computers and browsers, as well as autonomously execute and test programs. Vision is therefore no longer merely an input modality; it has become a critical interface through which an agent perceives its environment, verifies outcomes, and moves a task forward.

Building on this foundation, we have further expanded the range of agent training environments, task types, and productivity scenarios, while completing systematic post-training at trillion-parameter scale for the first time. Through broader task coverage and richer environmental feedback, Nex-N2.5 delivers further gains in scientific research, knowledge work, and complex productivity tasks. This work also provides valuable practical experience for training agentic capabilities in even larger models.

By jointly advancing model training, infrastructure, and real-world agent scenarios, Nex-AGI aims to continue driving progress in agentic intelligence.

## Open Source

Model weights for the Nex-N2.5 family will be released as open source, alongside hosted online services.

- **Nex-N2.5-Max:** [Hugging Face](https://huggingface.co/nex-agi/Nex-N2.5-Max) | [ModelScope](https://www.modelscope.cn/models/nex-agi/Nex-N2.5-Max)
- **Nex-N2.5-Pro:** [Hugging Face](https://huggingface.co/nex-agi/Nex-N2.5-Pro) | [ModelScope](https://www.modelscope.cn/models/nex-agi/Nex-N2.5-Pro)
- **Nex-N2.5-mini:** [Hugging Face](https://huggingface.co/nex-agi/Nex-N2.5-mini) | [ModelScope](https://www.modelscope.cn/models/nex-agi/Nex-N2.5-mini)
- **Early Access:** [SiliconFlow](https://cloud.siliconflow.cn/me/models?target=nex-agi%2FNex-N2.5-Pro)

We welcome developers and enterprises to integrate and try Nex-N2.5 and share their feedback.

## Performance

We evaluate Nex-N2.5 across coding, agentic workflows, computer use, and multimodal understanding.

The table below compares **Nex-N2.5-mini**, **Nex-N2.5-Pro**, and **Nex-N2.5-Max** with leading models across our evaluation suite. All scores are pending.

<table>
  <thead>
    <tr>
      <th align="left">Benchmark</th>
      <th align="center">Nex-N2.5-mini</th>
      <th align="center">Nex-N2.5-Pro</th>
      <th align="center">Nex-N2.5-Max</th>
      <th align="center">Claude Opus 5</th>
      <th align="center">GPT-5.6 Sol</th>
      <th align="center">Kimi K3</th>
      <th align="center">GLM-5.3</th>
      <th align="center">DeepSeek-V4-Pro-0813</th>
      <th align="center">Qwen3.8-Max</th>
    </tr>
    <tr>
      <th colspan="10" align="left">CODING</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Terminal-Bench 2.1</td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td></tr>
  </tbody>
  <tbody>
    <tr><td>SWE-Bench Pro</td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td></tr>
  </tbody>
  <tbody>
    <tr><td>DeepSWE v1.1</td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td></tr>
    <tr><th colspan="10" align="left">AGENTIC</th></tr>
  </tbody>
  <tbody>
    <tr><td>AutomationBench v1.0.6 (Public)</td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td></tr>
  </tbody>
  <tbody>
    <tr><td>Toolathlon-Verified</td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td></tr>
  </tbody>
  <tbody>
    <tr><td>GDPval-AA</td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td></tr>
  </tbody>
  <tbody>
    <tr><td>JobBench</td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td></tr>
  </tbody>
  <tbody>
    <tr><td>BrowseComp</td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td></tr>
    <tr><th colspan="10" align="left">MULTIMODAL</th></tr>
  </tbody>
  <tbody>
    <tr><td>OSWorld</td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td></tr>
  </tbody>
  <tbody>
    <tr><td>OSWorld-2</td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td></tr>
  </tbody>
  <tbody>
    <tr><td>WebTestBench</td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td></tr>
  </tbody>
  <tbody>
    <tr><td>WebArena</td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td></tr>
  </tbody>
  <tbody>
    <tr><td>OSWorld-G</td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td></tr>
  </tbody>
  <tbody>
    <tr><td>ScreenSpot-Pro</td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td></tr>
  </tbody>
  <tbody>
    <tr><td>Vision2Web</td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td></tr>
  </tbody>
  <tbody>
    <tr><td>SWE-bench Multimodal</td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td></tr>
  </tbody>
  <tbody>
    <tr><td>OmniDocBench</td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td></tr>
  </tbody>
  <tbody>
    <tr><td>CharXiv (Reasoning)</td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td><td align="center"></td></tr>
  </tbody>
</table>

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

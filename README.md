<div align="center">
<img src="./figures/NEX_logo.svg" width="20%"/>
</div>

---

<div align="center">
<p>
  💻 <a href="https://github.com/nex-agi/Nex-N2.5">GitHub</a>&nbsp; · &nbsp;
  🤗 <a href="https://huggingface.co/nex-agi/Nex-N2.5-Pro">Hugging Face</a>&nbsp; · &nbsp;
  🌐 <a href="https://nex-agi.com/">Website</a>&nbsp; · &nbsp;
  🔀 <a href="https://openrouter.ai/nex-agi/nex-n2.5-pro">OpenRouter (Pro)</a>
</p>
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

- **Nex-N2.5-Max:** [Hugging Face](https://huggingface.co/nex-agi/Nex-N2.5-Max) | [ModelScope](https://modelscope.cn/models/nex-agi/Nex-N2.5-Max)
- **Nex-N2.5-Pro:** [Hugging Face](https://huggingface.co/nex-agi/Nex-N2.5-Pro) | [ModelScope](https://modelscope.cn/models/nex-agi/Nex-N2.5-Pro)
- **Nex-N2.5-mini:** [Hugging Face](https://huggingface.co/nex-agi/Nex-N2.5-mini) | [ModelScope](https://modelscope.cn/models/nex-agi/Nex-N2.5-mini)
- **Hosted Access:** [OpenRouter (Nex-N2.5-Pro)](https://openrouter.ai/nex-agi/nex-n2.5-pro)
- **Websites:** [Global](https://nex-agi.com/) | [China](https://nex-agi.cn/)

We welcome developers and enterprises to integrate and try Nex-N2.5 and share their feedback.

## Performance

We evaluate Nex-N2.5 across coding, agentic workflows, computer use, and multimodal understanding.

The tables below compare **Nex-N2.5-mini**, **Nex-N2.5-Pro**, and **Nex-N2.5-Max** with leading models across our evaluation suite. **Bold** marks the best result in each benchmark, including ties; — indicates unavailable data.

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
      <th align="center">DeepSeek-V4-Pro</th>
      <th align="center">Qwen3.8-Max</th>
    </tr>
    <tr>
      <th colspan="10" align="left">CODING</th>
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
    <tr><td>AutomationBench v1.0.6</td><td align="center">32.3</td><td align="center">44.2</td><td align="center">50.2</td><td align="center">50.3</td><td align="center">45.8</td><td align="center">46.7</td><td align="center">48.2</td><td align="center">43.2</td><td align="center"><b>50.8</b></td></tr>
  </tbody>
  <tbody>
    <tr><td>Toolathlon Verified</td><td align="center">54.6</td><td align="center">68.5</td><td align="center">74.7</td><td align="center"><b>76.5</b></td><td align="center">74.9</td><td align="center"><b>76.5</b></td><td align="center">73.0</td><td align="center">74.1</td><td align="center">73.3</td></tr>
  </tbody>
  <tbody>
    <tr><td>GDPval-AA v2</td><td align="center">1446</td><td align="center">1628</td><td align="center">1713</td><td align="center"><b>1861</b></td><td align="center">1748</td><td align="center">1668</td><td align="center">1769</td><td align="center">1554</td><td align="center">1630</td></tr>
  </tbody>
  <tbody>
    <tr><td>Job Bench</td><td align="center">28.5</td><td align="center">41.4</td><td align="center">53.6</td><td align="center"><b>65.7</b></td><td align="center">45.4</td><td align="center">52.9</td><td align="center">58.2</td><td align="center">54.1</td><td align="center">64.0</td></tr>
  </tbody>
  <tbody>
    <tr><td>BrowseComp</td><td align="center">83.4</td><td align="center">89.7</td><td align="center"><b>92.6</b></td><td align="center">90.8</td><td align="center">90.4</td><td align="center">91.2</td><td align="center">—</td><td align="center">—</td><td align="center">—</td></tr>
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
    <tr><td>OSWorld-Verified</td><td align="center">71.2</td><td align="center">82.2</td><td align="center">75.2</td><td align="center">83.4</td><td align="center">83.2</td><td align="center">84.8</td><td align="center">62.3</td><td align="center">76.7</td><td align="center"><b>86.1</b></td></tr>
  </tbody>
  <tbody>
    <tr><td>OSWorld-2</td><td align="center">30.5</td><td align="center">56.4</td><td align="center">22.3</td><td align="center"><b>68.3</b></td><td align="center">62.7</td><td align="center">58.3</td><td align="center">—</td><td align="center">—</td><td align="center">46.7</td></tr>
  </tbody>
  <tbody>
    <tr><td>WebTest</td><td align="center">48.6</td><td align="center">52.8</td><td align="center">—</td><td align="center">—</td><td align="center"><b>54.0</b></td><td align="center">—</td><td align="center">—</td><td align="center">—</td><td align="center">52.3</td></tr>
  </tbody>
  <tbody>
    <tr><td>WebArena-Verified</td><td align="center">63.4</td><td align="center">67.6</td><td align="center">—</td><td align="center">—</td><td align="center">69.7</td><td align="center"><b>71.6</b></td><td align="center">—</td><td align="center">62.3</td><td align="center">66.8</td></tr>
  </tbody>
  <tbody>
    <tr><td>OSWorld-G</td><td align="center">82.9</td><td align="center"><b>87.4</b></td><td align="center">—</td><td align="center">76.8</td><td align="center">77.7</td><td align="center">79.6</td><td align="center">83.3</td><td align="center">59.4</td><td align="center">84.9</td></tr>
  </tbody>
  <tbody>
    <tr><td>Vision2Web</td><td align="center">52.9</td><td align="center">68.2</td><td align="center">59.0</td><td align="center">—</td><td align="center"><b>79.8</b></td><td align="center">—</td><td align="center">—</td><td align="center">—</td><td align="center">75.1</td></tr>
  </tbody>
  <tbody>
    <tr><td>SWE-MM</td><td align="center">25.5</td><td align="center">38.2</td><td align="center">—</td><td align="center"><b>59.4</b></td><td align="center">40.2</td><td align="center">37.3</td><td align="center">20.6</td><td align="center">39.2</td><td align="center">39.2</td></tr>
  </tbody>
  <tbody>
    <tr><td>OmniDoc</td><td align="center">89.7</td><td align="center">92.2</td><td align="center">91.6</td><td align="center">—</td><td align="center"><b>92.9</b></td><td align="center">91.1</td><td align="center">—</td><td align="center">—</td><td align="center">92.1</td></tr>
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

We also provide a prebuilt Docker image with our customized `sglang` fork preinstalled: **`nexagi/sglang:v0.5.18`**. The launch command is the same as above.

#### Nex-N2.5-Max

```bash
# Multi-node (2 nodes). Run the same command on every node with:
#   <node-rank> = 0 on the head node, 1 on the other node
#   <node0-ip>  = IP of the head node (reachable from all others)
docker run --gpus all --shm-size 32g --network host \
  -v /path/to/your/model:/model \
  nexagi/sglang:v0.5.18 \
  python3 -m sglang.launch_server \
    --model-path /path/to/your/model \
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
    --enable-hierarchical-cache \
    --hicache-ratio 4 \
    --hicache-write-policy write_through \
    --hicache-io-backend direct \
    --hicache-mem-layout page_first_direct \
    --chat-template /path/to/nex-n2.5-max/chat_template.jinja \
    --reasoning-parser deepseek-r1 \
    --tool-call-parser qwen3_coder
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

**Language:** [English](README.md) | [Русский](README.RU.md)

---

# Overview
This workflow aims for fully autonomous image generation. After the initial task input, the entire process of transforming that task into a final result is driven by LLMs, requiring no further human involvement.
# Features
1. Supports Flux 2 dev, Flux 2 Klein, and Qwen Image 25XX.
2. Three modes: creation, editing, and reference-based editing.
3. Up to 12 reference images<sup>1</sup>.
4. Initial task optimization.
5. Automated prompt generation and refinement.
6. Dual and triple image sampling support.
7. Result upscaling.

<sup>1</sup> Max 3 references for generation, max 12 for prompting.
# Model Requirements
## Minimum
1. Flux 2 Klein model suite.
2. [Tiny LLM](https://huggingface.co/mradermacher/Tiny-LLM-GGUF).
3. Any vision-capable LLM.

## Full Setup
1. Flux 2 dev, Flux 2 Klein, and Qwen Image 25XX model suites.
2. [Tiny LLM](https://huggingface.co/mradermacher/Tiny-LLM-GGUF).
3. Three separate vision-capable LLMs.
4. SeedVR2 model suite.

The workflow was tested using Gemma 4 26B A4B QAT, which performed the roles of all three LLMs used in the pipeline.
# Installation
1. Install ComfyUI.
2. Install LM Studio.
3. Download and install the required models in ComfyUI and LM Studio.<sup>2, 3</sup>
4. Install the following extensions in ComfyUI<sup>4</sup>:
   - [ComfyUI-KJNodes](https://github.com/kijai/ComfyUI-KJNodes)
   - [rgthree-comfy](https://github.com/rgthree/rgthree-comfy)
   - [ComfyUI-Easy-Use](https://github.com/yolain/ComfyUI-Easy-Use)
   - [ComfyUI-Impact-Pack](https://github.com/ltdrdata/ComfyUI-Impact-Pack)
   - [was-node-suite-comfyui](https://github.com/ltdrdata/was-node-suite-comfyui)
   - [ComfyUI-Unload-Model](https://github.com/SeanScripts/ComfyUI-Unload-Model)
   - [comfyui_LLM_party](https://github.com/heshengtao/comfyui_LLM_party)
5. Configure LM Studio:
   - Navigate to the Developer section.
   - In Server Settings, set the following:
      - Server Port --> 16001
      - Require Authentication --> Off
      - Just-in-Time Model Loading --> On
      - Only Keep Last JIT Loaded Model --> On
   - Start the server.

<sup>2</sup> The workflow may function with limited features if some models are missing.
<sup>3</sup> ComfyUI will likely show a pop-up asking to download missing models when loading the workflow.
<sup>4</sup> Automatic installation via ComfyUI Manager is also possible. Extensions --> Missing Nodes.
# Usage
0. For subsequent uses: Once the initial setup is complete, you only need to launch LM Studio and ensure the server is running.
1. Drag and drop the .json file (available in the Releases section) onto the ComfyUI workspace.
   It should look like this:
   ![Общий вид](https://imgur.com/ngbvBK0.png)
2. Navigate to the Workflow Configuration block.
   ![Блок настроек](https://imgur.com/1vbT09Z.png)
3. In the Step 0 block, select your previously downloaded models. To find the exact LLM identifiers, visit: http://127.0.0.1:16001/v1/models
4. Configure the workflow for your specific task using blocks Step 1 through Step 13. Each block contains its own set of instructions.
5. Navigate to the Image block.
   ![Блок изображений](https://imgur.com/dHVq5FK.png)
6. Add reference images if required.
7. Run the workflow.
8. Profit!

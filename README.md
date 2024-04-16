```bash
pip install -r requirements.txt
pip install -r reqs_optional/requirements_optional_langchain.txt
pip install -r reqs_optional/requirements_optional_gpt4all.txt
python generate.py --base_model=llama --prompt_type=llama2 --model_path_llama=https://huggingface.co/TheBloke/Llama-2-7B-Chat-GGML/resolve/main/llama-2-7b-chat.ggmlv3.q8_0.bin --max_seq_len=4096
```
#### Example Models
* [Highest accuracy and speed](https://huggingface.co/h2oai/h2ogpt-4096-llama2-70b-chat) on 16-bit with TGI/vLLM using ~48GB/GPU when in use (4xA100 high concurrency, 2xA100 for low concurrency)
* [Middle-range accuracy](https://huggingface.co/h2oai/h2ogpt-gm-oasst1-en-2048-falcon-40b-v2) on 16-bit with TGI/vLLM using ~45GB/GPU when in use (2xA100)
* [Small memory profile with ok accuracy](https://huggingface.co/TheBloke/Llama-2-13B-Chat-GGUF) 16GB GPU if full GPU offloading
* [Balanced accuracy and size](https://huggingface.co/h2oai/h2ogpt-4096-llama2-13b-chat) on 16-bit with TGI/vLLM using ~45GB/GPU when in use (1xA100)
* [Smallest or CPU friendly](https://huggingface.co/TheBloke/Llama-2-7B-Chat-GGUF) 32GB system ram or 9GB GPU if full GPU offloading
* [Best for 4*A10G using g5.12xlarge](https://huggingface.co/TheBloke/Llama-2-70B-chat-AWQ) AWQ LLaMa 70B using 4*A10G using vLLM

**GPU** mode requires CUDA support via torch and transformers. A 7B/13B model in 16-bit uses 14GB/26GB of GPU memory to store the weights (2 bytes per weight). Compression such as 4-bit precision (bitsandbytes, AWQ, GPTQ, etc.) can further reduce memory requirements down to less than 6GB when asking a question about your documents. (For more information, see [low-memory mode](docs/FAQ.md#low-memory-mode).)

**CPU** mode uses GPT4ALL and LLaMa.cpp, e.g. gpt4all-j, requiring about 14GB of system RAM in typical use.

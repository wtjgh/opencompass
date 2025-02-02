# Installation

1. Set up the OpenCompass environment:

   ```bash
   conda create --name opencompass python=3.10 pytorch torchvision pytorch-cuda -c nvidia -c pytorch -y
   conda activate opencompass
   ```

   If you want to customize the PyTorch version or related CUDA version, please refer to the [official documentation](https://pytorch.org/get-started/locally/) to set up the PyTorch environment. Note that OpenCompass requires `pytorch>=1.13`.

2. Install OpenCompass:

   ```bash
   git clone https://github.com/open-compass/opencompass.git
   cd opencompass
   pip install -e .
   ```

3. Install humaneval (Optional)

   If you want to **evaluate your models coding ability on the humaneval dataset**, follow this step.

   <details>
   <summary><b>click to show the details</b></summary>

   ```bash
   git clone https://github.com/openai/human-eval.git
   cd human-eval
   pip install -r requirements.txt
   pip install -e .
   cd ..
   ```

   Please read the comments in `human_eval/execution.py` **lines 48-57** to understand the potential risks of executing the model generation code. If you accept these risks, uncomment **line 58** to enable code execution evaluation.

   </details>

4. Install Llama (Optional)

   If you want to **evaluate Llama / Llama-2 / Llama-2-chat with its official implementation**, follow this step.

   <details>
   <summary><b>click to show the details</b></summary>

   ```bash
   git clone https://github.com/facebookresearch/llama.git
   cd llama
   pip install -r requirements.txt
   pip install -e .
   cd ..
   ```

   You can find example configs in `configs/models`. ([example](https://github.com/open-compass/opencompass/blob/eb4822a94d624a4e16db03adeb7a59bbd10c2012/configs/models/llama2_7b_chat.py))

   </details>

# Dataset Preparation

The datasets supported by OpenCompass mainly include two parts:

1. Huggingface datasets: The [Huggingface Datasets](https://huggingface.co/datasets) provide a large number of datasets, which will **automatically download** when running with this option.
2. Custom dataset: OpenCompass also provides some Chinese custom **self-built** datasets. Please run the following command to **manually download and extract** them.

Run the following commands to download and place the datasets in the `${OpenCompass}/data` directory can complete dataset preparation.

```bash
# Run in the OpenCompass directory
wget https://github.com/open-compass/opencompass/releases/download/0.1.8.rc1/OpenCompassData-core-20231110.zip
unzip OpenCompassData-core-20231110.zip
```

If you need to use the more comprehensive dataset (~500M) provided by OpenCompass, You can download it using the following command:

```bash
wget https://github.com/open-compass/opencompass/releases/download/0.1.8.rc1/OpenCompassData-complete-20231110.zip
unzip OpenCompassData-complete-20231110.zip
cd ./data
unzip *.zip
```

The list of datasets included in both `.zip` can be found [here](https://github.com/open-compass/opencompass/releases/tag/0.1.8.rc1)

OpenCompass has supported most of the datasets commonly used for performance comparison, please refer to `configs/dataset` for the specific list of supported datasets.

For next step, please read [Quick Start](./quick_start.md).

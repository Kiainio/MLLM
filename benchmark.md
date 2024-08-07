# MLLM Benchmark整理
## 一、常用Benchmark
### 1. LLaVA-Bench (In-the-Wild)
- 来源：``Visual Instruction Tuning`` (LLaVa; NeurIPS23; University of Wisconsin–Madison, Microsoft Research, Columbia University)
- 评测目标：模型在复杂任务上的能力和新领域上的泛用性
- 评测任务：对话、描述、推理
- 数据来源：COCO
- 标注：图像描述
- 输入：question, image
- 输出：answer
- 评测：调用GPT-4，对比text-only GPT-4结果对answer打分
- 示例
![LLaVa (wild)](srcs/benchmark/LLaVa.png)
- leaderboard: ShareGPT4V, LLaVa, InsturctBLIP

### 2. ScienceQA
- 来源：``Multimodal reasoning via thought chains for science question answering`` (NeruIPS22; University of California Arizona State University, Allen Institute for AI)
- 评测目标：在丰富领域上的推理思维链
- 数据来源：IXL Learning在线教育平台
- 标注：推理所需用到的知识，解释
- 输入：multi-choice question, image
- 输出：choice, explanation
- 评测：accuracy, 解释分数(BLEU-1/4, ROUGE-L, Similarity)
- 示例
![ScienceQA](srcs/benchmark/ScienceQA.png)
- leaderboard: LLaVa, CoT相关, ChatGPT, SAM（得分较低，排名54）

### 3. MME
- 来源：``MME: A Comprehensive Evaluation Benchmark for Multimodal Large Language Models`` (Tencent Youtu Lab, Xiamen University)
- 评测目标：感知识别、认知推理能力
- 数据来源：COCO, CTW1500 (OCR), 自拍摄图像, diffusion生成
- 标注：人工标注的instruction-answer对
- 输入：instruction, image
- 输出：yes/no
- 评测：accuracy
- 示例
![MME](srcs/benchmark/MME.png)
- leaderboard: Qwen-VL-Max, Gemini Pro, GPT-4V

### 4. MMBench
- 来源：``MMBench: Is Your Multi-modal Model an All-around Player?`` (Shanghai AI Laboratory, Nanyang Technological University, The Chinese University of Hong Kong, National University of Singapore, Zhejiang University)
- 评测目标：感知、推理等多层次能力
![MMBench_target](srcs/benchmark/MMBench_target.png)
- 数据来源
![MMBench_data](srcs/benchmark/MMBench_data.png)
- 标注：正确选项
- 输入：multi-choice question, image
- 输出：choice
- 评测：CircularEval, accuracy
- 示例
![MMBench_example](srcs/benchmark/MMBench_example.png)
- leaderboard: GPT-4o, GPT-4v, InternVL-Chat, Qwen-VL-Max

### 5. MM-Vet
- 来源：``MM-Vet: Evaluating Large Multimodal Models for Integrated Capabilities`` (National University of Singapore, Microsoft Azure AI)
- 评测目标：recognition, knowledge, OCR, spatial awareness, language generation, math
- 数据来源：187 online sources, 10 XCR, 3 ChestX-ray14
- 标注：人工标注，互联网获取，已有数据集标注
- 输入：instruction, image
- 输出：answer
- 评测：GPT-4根据上下文例子打分
![MM-Vet_eval](srcs/benchmark/MM-Vet_eval.png)
- 示例
![MM-Vet_example](srcs/benchmark/MM-Vet_example.png)
- leaderboard: OpenFlagmingo, BLIP-2, LLaVa, MiniGPT, LLaMA-Adapter, InstructBLIP

### 6. SEED-Bench
- 来源：``A benchmark for evaluating Multimodal LLMs using multiple-choice questions`` (v2 CVPR2024; Tencent AI Lab 2ARC Lab, Tencent PCG)
- 评测目标
![SEED-Bench_target](srcs/benchmark/SEED-Bench_target.png)
- 数据来源：CC3M, Something-Something-v2, Epic-kitchen 100, Breakfast
- 标注：提取视觉信息->生成问题答案对->人工筛选、标注
- 输入：multi-choice question, image/video
- 输出：choice
- 评测：将生成概率最高的选项作为模型答案，计算accuracy
- 示例
![SEED-Bench_example](srcs/benchmark/SEED-Bench_example.png)
- leaderboard
![SEED-Bench_leaderboard](srcs/benchmark/SEED-Bench_leaderboard.png)

### 7. MMMU
- 来源：``A Massive Multi-discipline Multimodal Understanding and Reasoning Benchmark for Expert AGI`` (v2 CVPR2024; IN.AI Research, University of Waterloo, The Ohio State University, Independent, Carnegie Mellon University, University of Victoria, Princeton University)
- 评测目标: college-level subject knowledge and deliberate reasoning
- 数据来源：college exams, quizzes, and textbooks
- 标注：人工标注
- 输入：question, image
- 输出：answer
- 评测：micro-averaged
- 示例
![MMMU_example](srcs/benchmark/MMMU_example.png)
- leaderboard: Gemini Ultra, GPT-4V, InternVL-Chat-V1.2, Qwen-VL-MAXLLaVA-1.6-34B

### 8. CMMMU
- 来源：``CMMMU: A Chinese Massive Multi-discipline Multimodal Understanding Benchmark`` (Multimodal Art Projection Research Community Hong Kong University of Science and Technology, University of Waterloo, Chinese Academy of Sciences, University of Chinese Academy of Sciences, Peking University, The Hong Kong Polytechnic University 7Waseda University, University of Manchester, 01.AI)
- 评测目标: college-level subject knowledge and deliberate reasoning
- 数据来源：college exams, quizzes, and textbooks
- 标注：人工标注
- 输入：question, image
- 输出：answer
- 评测：micro-averaged
- 示例
![CMMMU_example](srcs/benchmark/CMMMU_example.png)
- leaderboard: GPT-4V

### 9. GQA（重要）
- 来源：``GQA: A New Dataset for Real-World Visual Reasoning and Compositional Question Answering`` (Stanford University)
- 评测目标：object recognition, commonsense understanding and relation extraction
- 数据来源：VG (COCO, Flickr)
- 标注：scene graph
- 输入：question, image
- 输出：answer
- 评测：consistency, validity, plausibility, distribution, grounding, accuracy
- 示例
![GQA_example](srcs/benchmark/GQA_example.png)
- leaderboard: MoE-LLaVa

### 10. POPE（重要）
- 来源：``Evaluating Object Hallucination in Large Vision-Language Models`` (EMNLP'23; Renmin University of China, Beijing Key Laboratory of Big Data Management and Analysis Methods)
- 评测目标：物体幻觉
- 数据来源：COCO (可按照{"image": "COCO_val2014_000000131089.jpg", "objects": ["person", "baseball bat"]}格式自建)
- 标注：物体GT
- 输入：question ("Is there a/an <object> in the image?"), image
- 输出：yes/no
- 评测：accuracy, precision, recall, F1 score
- 示例
![POPE](srcs/benchmark/POPE.png)
- leaderboard: LLaVa, MiniGPT-4, InstructBLIP, InternLM-XComposer2

### 11. HallusionBench（可能重要）
- 来源：``HallusionBench: You See What You Think? Or You Think What You See? An Image-Context Reasoning Benchmark Challenging for GPT-4V(ision), LLaVA-1.5, and Other Multi-modality Models`` (CVPR2024; University of Maryland)
- 评测目标：emphasize nuanced understanding and interpretation of visual data
- 数据来源：人工选择
- 标注：人工标注
- 输入：question, image/video
- 输出：answer
- 评测：all accurarcy, figure accuracy, question pair accuracy
- 示例
![HallusionBench_example](srcs/benchmark/HallusionBench_example.png)
- leaderboard: GPT-4V, Gemini Pro Vision, Claude 3, LLaVA- 1.5, InternLM-XComposer2

### 12. RealWorldQA（重要）
- 来源：xAI
- 评测目标：真实世界空间理解
- 输入：question, image
- 输出：answer
- 评测：（%）
- 示例
![RealWorldQA_example](srcs/benchmark/RealWorldQA_example.png)
- leaderboard: Grok-1.5V, GPT-4V, Gemini Pro

## 二、评测方法
[A Toolkit for Evaluating Large Vision-Language Models](https://github.com/open-compass/VLMEvalKit)
<table>
<thead>
<tr>
<th>Dataset</th>
<th>Dataset Names (for run.py)</th>
<th>Task</th>
<th>Dataset</th>
<th>Dataset Names (for run.py)</th>
<th>Task</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="https://github.com/open-compass/mmbench/"><strong>MMBench Series</strong></a>: <br>MMBench, MMBench-CN, CCBench</td>
<td>MMBench_DEV_[EN/CN]<br>MMBench_TEST_[EN/CN]<br>MMBench_DEV_[EN/CN]<em>V11<br>MMBench_TEST</em>[EN/CN]_V11<br>CCBench</td>
<td>Multi-choice <br>Question (MCQ)</td>
<td><a href="https://github.com/MMStar-Benchmark/MMStar"><strong>MMStar</strong></a></td>
<td>MMStar</td>
<td>MCQ</td>
</tr>
<tr>
<td><a href="https://github.com/BradyFU/Awesome-Multimodal-Large-Language-Models/tree/Evaluation"><strong>MME</strong></a></td>
<td>MME</td>
<td>Yes or No (Y/N)</td>
<td><a href="https://github.com/AILab-CVC/SEED-Bench"><strong>SEEDBench_IMG</strong></a></td>
<td>SEEDBench_IMG</td>
<td>MCQ</td>
</tr>
<tr>
<td><a href="https://github.com/yuweihao/MM-Vet"><strong>MM-Vet</strong></a></td>
<td>MMVet</td>
<td>VQA</td>
<td><a href="https://mmmu-benchmark.github.io" rel="nofollow"><strong>MMMU</strong></a></td>
<td>MMMU_DEV_VAL/MMMU_TEST</td>
<td>MCQ</td>
</tr>
<tr>
<td><a href="https://mathvista.github.io" rel="nofollow"><strong>MathVista</strong></a></td>
<td>MathVista_MINI</td>
<td>VQA</td>
<td><a href="https://scienceqa.github.io" rel="nofollow"><strong>ScienceQA_IMG</strong></a></td>
<td>ScienceQA_[VAL/TEST]</td>
<td>MCQ</td>
</tr>
<tr>
<td><a href="https://cocodataset.org" rel="nofollow"><strong>COCO Caption</strong></a></td>
<td>COCO_VAL</td>
<td>Caption</td>
<td><a href="https://github.com/tianyi-lab/HallusionBench"><strong>HallusionBench</strong></a></td>
<td>HallusionBench</td>
<td>Y/N</td>
</tr>
<tr>
<td><a href="https://ocr-vqa.github.io" rel="nofollow"><strong>OCRVQA</strong></a>*</td>
<td>OCRVQA_[TESTCORE/TEST]</td>
<td>VQA</td>
<td><a href="https://textvqa.org" rel="nofollow"><strong>TextVQA</strong></a>*</td>
<td>TextVQA_VAL</td>
<td>VQA</td>
</tr>
<tr>
<td><a href="https://github.com/vis-nlp/ChartQA"><strong>ChartQA</strong></a>*</td>
<td>ChartQA_TEST</td>
<td>VQA</td>
<td><a href="https://allenai.org/data/diagrams" rel="nofollow"><strong>AI2D</strong></a></td>
<td>AI2D_TEST</td>
<td>MCQ</td>
</tr>
<tr>
<td><a href="https://huggingface.co/datasets/liuhaotian/llava-bench-in-the-wild" rel="nofollow"><strong>LLaVABench</strong></a></td>
<td>LLaVABench</td>
<td>VQA</td>
<td><a href="https://www.docvqa.org" rel="nofollow"><strong>DocVQA</strong></a>+</td>
<td>DocVQA_[VAL/TEST]</td>
<td>VQA</td>
</tr>
<tr>
<td><a href="https://www.docvqa.org/datasets/infographicvqa" rel="nofollow"><strong>InfoVQA</strong></a>+</td>
<td>InfoVQA_[VAL/TEST]</td>
<td>VQA</td>
<td><a href="https://github.com/Yuliang-Liu/MultimodalOCR"><strong>OCRBench</strong></a></td>
<td>OCRBench</td>
<td>VQA</td>
</tr>
<tr>
<td><a href="https://x.ai/blog/grok-1.5v" rel="nofollow"><strong>RealWorldQA</strong></a></td>
<td>RealWorldQA</td>
<td>MCQ</td>
<td><a href="https://github.com/AoiDragon/POPE"><strong>POPE</strong></a>+</td>
<td>POPE</td>
<td>Y/N</td>
</tr>
<tr>
<td><a href="https://github.com/core-mm/core-mm"><strong>Core-MM</strong></a>-</td>
<td>CORE_MM</td>
<td>VQA</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

## 三、测评结果
### LLaVa-1.5-7B
#### 1. LLaVA-Bench (In-the-Wild)
通过GPT-4进行评测，需要OpenAI_KEY。
#### 2. MME
##### 1）分数
| perception | reasoning | OCR | artwork | celebrity | code_reasoning | color | commonsense_reasoning | count | existence | landmark | numerical_calculation | position | posters | scene | text_translation |
|------------|-----------|-----|---------|-----------|----------------|-------|-----------------------|-------|-----------|----------|-----------------------|----------|---------|-------|------------------|
| 1516       | 302       | 132 | 119     | 132       | 60             | 170   | 117                   | 160   | 195       | 160      | 67                    | 153      | 136     | 157   | 58               |
##### 2）失败案例
###### color
假阳较多。
```
# MME_color/000000012120.jpg
Is there a blue court in the image? Please answer yes or no.	Yes |Yes
Is there a purple court in the image? Please answer yes or no.	No  |Yes

USER: Is there a purple court in the image? Please answer yes or no.
ASSISTANT: Yes, there is a purple court in the image.
USER: Please give an explanation of the answer.
ASSISTANT: The image features a purple tennis court where a tennis match is taking place.
USER: describe the picture
ASSISTANT:  The image is a tennis court with a purple surface, where a tennis match is taking place. There are several people on the court, including a woman who is holding a tennis racket, and a man who is also holding a tennis racket. The scene captures the intensity and action of the match, with the players actively engaged in the game.
```
![MME/color/000000012120.jpg](srcs/benchmark/MME/color/000000012120.jpg)
"a court"
![MME/color/000000012120_a court.jpg](srcs/benchmark/MME/color/000000012120_a_court.jpg)
"a blue court"
![MME/color/000000012120_a_blue_court.jpg](srcs/benchmark/MME/color/000000012120_a_blue_court.jpg)
"a purple court"
![MME/color/000000012120_a_purple_court.jpg](srcs/benchmark/MME/color/000000012120_a_purple_court.jpg)
```
# color/000000028993.jpg
Are there yellow poles in the image? Please answer yes or no.	Yes |No
Are there blue poles in the image? Please answer yes or no.	    No  |No

'please describe the picture'
'The image features a city street with four large, golden fire hydrants lined up along the sidewalk. These fire hydrants are placed at regular intervals, providing a sense of order and organization in the urban environment. \n\nIn addition to the fire hydrants, there are several people walking along the sidewalk, going about their daily activities. Some of them are closer to the foreground, while others are further away, creating a sense of depth and activity in the scene.'
'are there poles in the image? are they yellow?'
'Yes, there are poles in the image, and they are yellow.'
'are there poles in the image? are they blue?'
'Yes, there are poles in the image, and they are blue.'
```
![MME/color/000000028993.jpg](srcs/benchmark/MME/color/000000028993.jpg)
"poles"
![MME/color/000000028993_poles.jpg](srcs/benchmark/MME/color/000000028993_poles.jpg)
"yellow poles"
![MME/color/000000028993_yellow_poles.jpg](srcs/benchmark/MME/color/000000028993_yellow_poles.jpg)
"blue poles"
![MME/color/000000028993_blue_poles.jpg](srcs/benchmark/MME/color/000000028993_blue_poles.jpg)
```
# color/000000055072.jpg
Is there a brown giraffe in the image?  Please answer yes or no.	Yes |No
Is there a black giraffe in the image? Please answer yes or no.	    No  |No
```
![MME/color/000000055072.jpg](srcs/benchmark/MME/color/000000055072.jpg)
"a giraffe"
![MME/color/000000055072_a_giraffe.jpg](srcs/benchmark/MME/color/000000055072_a_giraffe.jpg)
"brown giraffe"
![MME/color/000000055072_a_brown_giraffe.jpg](srcs/benchmark/MME/color/000000055072_a_brown_giraffe.jpg)
"a black giraffe"
![MME/color/000000055072_a_black_giraffe.jpg](srcs/benchmark/MME/color/000000055072_a_black_giraffe.jpg)
```
# color/000000057597.jpg
Are there any red shoes in the image? Please answer yes or no.	    Yes |Yes
Are there any yellow shoes in the image? Please answer yes or no.	No  |Yes
```
![MME/color/000000057597.jpg](srcs/benchmark/MME/color/000000057597.jpg)
"shoes"
![MME/color/000000057597_shoes.jpg](srcs/benchmark/MME/color/000000057597_shoes.jpg)
"red shoes"
![MME/color/000000057597_red_shoes.jpg](srcs/benchmark/MME/color/000000057597_red_shoes.jpg)
"yellow shoes"
![MME/color/000000057597_yellow_shoes.jpg](srcs/benchmark/MME/color/000000057597_yellow_shoes.jpg)
```
# color/000000427034.jpg
Is there a brown and black dog in the image? Please answer yes or no.	Yes |Yes
Is there a brown and black dog in the image? Please answer yes or no.	No  |Yes
```
![MME/color/000000427034.jpg](srcs/benchmark/MME/color/000000427034.jpg)
"a dog"
![MME/color/000000427034_a_dog.jpg](srcs/benchmark/MME/color/000000427034_a_dog.jpg)
"a brown and black dog"
![MME/color/000000427034_a_brown_and_black_dog.jpg](srcs/benchmark/MME/color/000000427034_a_brown_and_black_dog.jpg)
"a brown and white dog"
![MME/color/000000427034_a_brown_and_white_dog.jpg](srcs/benchmark/MME/color/000000427034_a_brown_and_white_dog.jpg)
```
# color/000000530457.jpg
Are there any red flowers in the image? Please answer yes or no.	Yes |Yes
Are there any green flowers in the image? Please answer yes or no.	No  |Yes
```
![MME/color/000000530457.jpg](srcs/benchmark/MME/color/000000530457.jpg)
"flowers"
![MME/color/000000530457_flowers.jpg](srcs/benchmark/MME/color/000000530457_flowers.jpg)
"red flowers"
![MME/color/000000530457_red_flowers.jpg](srcs/benchmark/MME/color/000000530457_red_flowers.jpg)
"green flowers"
![MME/color/000000530457_green_flowers.jpg](srcs/benchmark/MME/color/000000530457_green_flowers.jpg)
###### commonsense reasoning
准确率较低，视觉层面上包含ocr、物体识别等。
```
#MME/commonsense_reasoning/0058.png
Can't I smoke here? Please answer yes or no.	Yes |No
May I smoke here? Please answer yes or no.	    No  |No

USER: Describe the picture
ASSISTANT: The image features a white wall with a sign posted on it, likely in a foreign language. The sign is placed near the top of the wall, and it appears to be a no-smoking sign. The wall is clean and devoid of any other decorations or signs. The overall setting seems to be a simple, uncluttered space.
USER: Can't I smoke here? Please answer yes or no.
ASSISTANT: No.
USER: May I smoke here? Please answer yes or no.
ASSISTANT: No.
```
![MME/commonsense_reasoning/0058.png](srcs/benchmark/MME/commonsense_reasoning/0058.png)
"a sign of 'no smoking'"
![MME/commonsense_reasoning/0058.png](srcs/benchmark/MME/commonsense_reasoning/0058_a_sign_of_no_smoking.png)
```
#MME/commonsense_reasoning/003.png
May I ask if in the game of finger-guessing game, did the right side of the picture win? Please answer yes or no.   Yes |Yes
May I ask if in the game of finger-guessing game, did the left side of the picture win? Please answer yes or no.   No  |Yes


USER: describe the picture
ASSISTANT: The image features two yellow hands, one on the left side and the other on the right side, placed side by side. The hands are positioned in a way that they appear to be punching, giving the impression of a boxing or fighting scene. The hands are the main focus of the image, with no other objects or elements visible.
USER: if this is a game of finger-guessing game, what do these two hands represent?      
ASSISTANT: If this is a game of finger-guessing, the two hands represent the fingers of the players who are participating in the game. The hands are placed side by side, and the objective of the game is to guess which finger belongs to which hand. The players take turns, and the goal is to correctly identify the fingers of the other player by feeling the hand without looking at it. This can be a fun and engaging activity for people of all ages, as it requires good observation skills and communication between the players.
USER: who will win the game in this picture? Left or right?
ASSISTANT:  In this image, it is not possible to determine who will win the game, as it is just a representation of the hands and not a real-life scenario. The outcome of the game would depend on the players' skills, luck, and strategy. In a real-life scenario, the players would need to communicate and cooperate to determine the correct fingers and ultimately win the game.
```
![MME/commonsense_reasoning/0003.png](srcs/benchmark/MME/commonsense_reasoning/0003.png)
```
commonsense_reasoning/0005.png
The office's normal closing time is 5 p.m. Now is afternoon. Should I continue to work at the time shown in the picture? Please answer yes or no.   Yes |Yes
The office's normal closing time is 5 p.m. Now is afternoon. Could I leave work at the time shown in the picture? Please answer yes or no.      No  |Yes

USER: describe the picture
ASSISTANT: The image features a person wearing a blue shirt and a blue and black watch on their left wrist. The watch has a blue face and is positioned towards the center of the person's arm. The person is also wearing a blue shirt, which complements the watch's color. The scene is set on a white surface, which provides a clean and minimalistic backdrop for the watch and the person.
USER: what time is it?
ASSISTANT: The time displayed on the watch is 10:10.
USER: can you read the time from the watch?
ASSISTANT:  Yes, the time on the watch is 10:10.
```
![MME/commonsense_reasoning/0005.png](srcs/benchmark/MME/commonsense_reasoning/0005.png)
```
commonsense_reasoning/0010.png
I am going to exercise and I want to choose a venue. Is the venue in the picture a good choice? Please answer yes or no.	Yes |Yes
I am going to study and I want to choose a venue. Is the venue in the picture a good choice? Please answer yes or no.	No  |Yes

USER: describe the picture
ASSISTANT: The image depicts a large gym with a variety of exercise equipment, including several treadmills, a row of bikes, and a couple of benches. The treadmills are placed in different areas of the gym, with some closer to the center and others near the edges. The bikes are arranged in a row, with some closer to the center and others towards the right side of the gym. The benches are located near the right side of the gym, with one closer to the center and the other further back.

The gym is well-lit, with a bright overhead light illuminating the space. The overall atmosphere of the gym is inviting and encourages physical activity.
USER: I am going to study and I want to choose a venue. Is the venue in the picture a good choice? Please answer yes or no.
ASSISTANT: Yes, the gym in the picture would be a good choice for studying. The bright and well-lit environment, along with the availability of exercise equipment, can create a conducive atmosphere for concentration and focus. Additionally, the presence of other people in the gym might provide a sense of motivation and accountability for those who are studying.
```
![MME/commonsense_reasoning/0010.png](srcs/benchmark/MME/commonsense_reasoning/0010.png)
###### count
```
#count/000000067213.jpg
Is there only one dog in the image? Please answer yes or no.	Yes |No (No, there are two dogs in the image.
)
Is there two dogs in the image? Please answer yes or no.	    No  |No
```
![MME/count/000000067213.jpg](srcs/benchmark/MME/count/000000067213.jpg)
![MME/count/000000067213_dog.jpg](srcs/benchmark/MME/count/000000067213_dog.jpg)
```
#count/000000236721.jpg
Are there two bananas in the image? Please answer yes or no.	Yes |Yes
Are there three bananas in the image? Please answer yes or no.	No  |Yes
```
![MME/count/000000236721.jpg](srcs/benchmark/MME/count/000000236721.jpg)
![MME/count/000000236721_banana.jpg](srcs/benchmark/MME/count/000000236721_banana.jpg)
```
#count/000000423944.jpg
Is there no person in this picture? Please answer yes or no.	    Yes |No
Are there two people appear in this image? Please answer yes or no.	No  |No
```
![MME/count/000000423944.jpg](srcs/benchmark/MME/count/000000423944.jpg)
![MME/count/000000423944_people.jpg](srcs/benchmark/MME/count/000000423944_people.jpg)
```
#count/000000430286.jpg
Are there three remotes in this image? Please answer yes or no.	    Yes |Yes
Are there only two remotes in this image? Please answer yes or no.	No  |Yes
```
![MME/count/000000430286.jpg](srcs/benchmark/MME/count/000000430286.jpg)
![MME/count/000000430286_remotes.jpg](srcs/benchmark/MME/count/000000430286_remotes.jpg)
```
#count/000000432468.jpg
Are there three zippers in the picture? Please answer yes or no.	Yes |Yes
Is there a zipper in the picture? Please answer yes or no.	        No  |Yes
```
![MME/count/000000432468.jpg](srcs/benchmark/MME/count/000000432468.jpg)
![MME/count/000000432468_zippers.jpg](srcs/benchmark/MME/count/000000432468_zippers.jpg)
```
#count/000000434479.jpg
Are there two pieces of pizza in this image? Please answer yes or no.       Yes |No (No, there is only one piece of pizza in the image.)
Is there only one piece of pizza in this image? Please answer yes or no.    No  |No
```
![MME/count/000000434479.jpg](srcs/benchmark/MME/count/000000434479.jpg)
![MME/count/000000434479_piece_of_pizza.jpg](srcs/benchmark/MME/count/000000434479_piece_of_pizza.jpg)
```
#count/000000450303.jpg
Are there six people appear in this image? Please answer yes or no.     Yes |No (No, there are only five people in the image.)
Are there seven people appear in this image? Please answer yes or no.	No  |No
```
![MME/count/000000450303.jpg](srcs/benchmark/MME/count/000000450303.jpg)
![MME/count/000000450303_people.jpg](srcs/benchmark/MME/count/000000450303_people.jpg)
```
#count/000000470121.jpg
Is there only one bottle in the image? Please answer yes or no.	Yes |Yes
Is there two bottles in the image? Please answer yes or no.	No  |Yes
```
![MME/count/000000470121.jpg](srcs/benchmark/MME/count/000000470121.jpg)
![MME/count/000000470121_bottle.jpg](srcs/benchmark/MME/count/000000470121_bottle.jpg)
###### existence
```
#MME/existence/000000009590.jpg
Is there a bottle in this image? Please answer yes or no.   Yes |No
Is there a scissors in this image? Please answer yes or no. No  |No
```
![MME/existence/000000009590.jpg](srcs/benchmark/MME/existence/000000009590.jpg)
###### position
假阳较多。
```
#MME/position/000000031248.jpg
Is there a sofa in the middle of potted plants in the image? Please answer yes or no.	        Yes |No
Is there a sofa in the right side of potted plants in the image? Please answer yes or no.	No  |Yes
```
![MME/position/000000031248.jpg](srcs/benchmark/MME/position/000000031248.jpg)
```
#position/000000056127.jpg
Is the light above the fire hydrant in the image? Please answer yes or no.	Yes |Yes
Is the light under the fire hydrant in the image?  Please answer yes or no.	No  |Yes
```
![MME/position/000000056127.jpg](srcs/benchmark/MME/position/000000056127.jpg)
```
#position/000000097994.jpg
Is the light above the computer in the image? Please answer yes or no.	Yes |Yes
Is the light under the computer in the image? Please answer yes or no.	No  |Yes
```
![MME/position/000000097994.jpg](srcs/benchmark/MME/position/000000097994.jpg)
```
#position/000000212800.jpg
Is the blue umbrella under the black umbrella? Please answer yes or no.	Yes |Yes
Is the blue umbrella above the black umbrella? Please answer yes or no.	No  |Yes
```
![MME/position/000000212800.jpg](srcs/benchmark/MME/position/000000212800.jpg)
```
position/000000450303.jpg
Is the monitor on top of a person? Please answer yes or no.	Yes |No
Is the monitor under the person? Please answer yes or no.	No  |No
```
![MME/position/000000450303.jpg](srcs/benchmark/MME/position/000000450303.jpg)
```
Is the person under the kite? Please answer yes or no.	Yes |Yes
Is the person above the kite? Please answer yes or no.	No  |Yes
```
![MME/position/000000477955.jpg](srcs/benchmark/MME/position/000000477955.jpg)
```
#position/000000530162.jpg
Is the big red and black umbrella on the top of people? Please answer yes or no.	Yes |Yes
Is the big red and black umbrella under people? Please answer yes or no.	No  |Yes
```
![MME/position/000000530162.jpg](srcs/benchmark/MME/position/000000530162.jpg)

```
#position/000000578922.jpg
Is the vase on the left of the toothbrush? Please answer yes or no.	Yes |Yes
Is the vase on the right of the toothbrush? Please answer yes or no.	No  |Yes
```
![MME/position/000000578922.jpg](srcs/benchmark/MME/position/000000578922.jpg)
###### scene
假阴较多。
```
#MME/scene/images/Places365_val_00000001.jpg
Is this picture captured in a place of greenhouse indoor? Please answer yes or no.	Yes |No
Is this picture captured in a place of waiting room? Please answer yes or no.	No  |No
```
![MME/scene/images/Places365_val_00000001.jpg](srcs/benchmark/MME/scene/images/Places365_val_00000001.jpg)
#### 3. MMBench
#### 4. MM-Vet
通过GPT-4进行评测，需要OpenAI_KEY。 
#### 5. SEED-Bench
##### 1）分数
| split | Overall | Instance Attributes | Instance Identity | Instance Interaction | Instance Location | Instances Counting | Scene Understanding | Spatial Relation | Text Understanding | Visual Reasoning |
|-------|---------|---------------------|-------------------|----------------------|-------------------|--------------------|---------------------|------------------|--------------------|------------------|
| none  | 0.66    | 0.67                | 0.69              | 0.71                 | 0.60              | 0.58               | 0.74                | 0.51             | 0.37               | 0.77             |
##### 2）失败案例
###### Scene Understanding
```
Which of the following can be inferred from the image?

The street is located in a mountainous region
The street is located in a rural area with a small population
The street is located in a densely populated urban area
The buildings in the street are of modern style and architecture

D   |C
```
![SEED-Bench/175.jpg](srcs/benchmark/SEED-Bench/175.jpg)
###### Instance Identity
```
Which of the following items are NOT visible in the image?

Trumpet
Drumsticks
Piano
Microphone

B   |A
```
![SEED-Bench/295.jpg](srcs/benchmark/SEED-Bench/295.jpg)
###### Instance Attributes
color, shape, ...
```
What color is the girl's shirt?
Maroon	Green	Pink	Blue
D   |C
```
![SEED-Bench/188.jpg](srcs/benchmark/SEED-Bench/188.jpg)
###### Instance Location
```
Where are the bride and groom positioned in the image?

They are sitting in front of a stained glass window
They are standing in front of a large stained glass window
They are sitting next to each other on a bench
They are standing at the altar with a priest

B   |D
```
![SEED-Bench/117.jpg](srcs/benchmark/SEED-Bench/117.jpg)
###### Instances Counting
```
How many people are in the image?

One
Two
Three
Four

C   |B
```
![SEED-Bench/319.jpg](srcs/benchmark/SEED-Bench/319.jpg)
###### Spatial Relation
```
What is the position of the cars on the street relative to the buildings?

Parked in front of the buildings
Driving down the street
Parked in the middle of the street
Parked along the sides of the street

D   |A
```
![SEED-Bench/46.jpg](srcs/benchmark/SEED-Bench/46.jpg)
###### Instance Interaction
```
What is the relation between the beach and the water in the image?
The beach is parallel to the water
The beach is perpendicular to the water
The beach is higher than the water
The beach is lower than the water

C   |D
```
![SEED-Bench/1974.jpg](srcs/benchmark/SEED-Bench/1974.jpg)
###### Visual Reasoning
```
What is the man pushing in the image?

A cart filled with fruits and vegetables
A shopping cart
A stroller with a child
A suitcase

A   |B
```
![SEED-Bench/331.jpg](srcs/benchmark/SEED-Bench/331.jpg)
#### 6. GQA
#### 7. POPE
##### 1）分数
| split       | Overall | acc | precision | recall |
|-------------|---------|-----|-----------|--------|
| Overall     | 86      | 87  | 92        | 81     |
| adversarial | 84      | 84  | 87        | 81     |
| popular     | 86      | 87  | 92        | 81     |
| random      | 88      | 89  | 96        | 81     |
##### 2）失败案例
###### adversarial
```
Is there a spoon in the image? Please answer yes or no.	Yes |No
```
![POPE/18.jpg](srcs/benchmark/POPE/18.jpg)
###### popular
```
Is there a chair in the image? Please answer yes or no. No  |Yes
```
![POPE/3.jpg](srcs/benchmark/POPE/3.jpg)
###### random
```
Is there a dog in the image? Please answer yes or no. No    |Yes
```
![POPE/136.jpg](srcs/benchmark/POPE/136.jpg)
#### 8. HallusionBench
通过GPT-4进行评测，需要OpenAI_KEY。
#### 9. RealWorldQA
##### 1）分数
0.54
##### 2）失败案例
count
```
How many bars are here?

There are two parallel bars in this photo.
There are three bars in the photo. two are the same height and one is higher.
There are two bars in this photo. one is high and one is low.

B   |A
```
![RealWorldQA/1.jpg](srcs/benchmark/RealWorldQA/1.jpg)
commonsense_reasoning
```
Are we required to stop?

Yes
No

A   |B
```
![RealWorldQA/6.jpg](srcs/benchmark/RealWorldQA/6.jpg)
color
```
What color is the nearest set of traffic lights in this scene?

Red
Green
Yellow

A   |B
```
![RealWorldQA/24.jpg](srcs/benchmark/RealWorldQA/24.jpg)
## 四、测评方法
```
python -m llava.serve.cli \
    --model-path liuhaotian/llava-v1.5-7b \
    --image-file IMAGE-PATH \
    --load-4bit
```
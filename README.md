## Introduction

With the rapid advancement of artificial intelligence (AI) and the growing complexity of input requirements in deep learning systems, Automatic Speech Recognition (ASR) has emerged as a widely used tool in numerous applications. ASR, a high-efficiency input method, can save an average of 20 minutes in our daily life compared to conventional methods such as typing[1]. Despite the notable successes of AI, especially, deep learning, in ASR tasks, these systems continue to face several challenges. Key challenges include robustness to noise, handling various accents and dialects, limited data resources, and difficulties adapting to new domains and speakers[2].

A promising approach to overcoming these challenges is through pre-training models on large, unlabeled datasets, which enables them to learn the underlying structure of languages. Self-supervised learning (SSL) has gained significant traction as a pre-training technique for ASR tasks, allowing models to capture rich acoustic and linguistic features from speech data without requiring labeled inputs. Wav2Vec2, an SSL technique, has shown notable improvement in ASR performance, especially in low-resource and multilingual settings[3]. Wav2Vec2 leverages vast amounts of unlabeled speech data to learn powerful representations, making it highly effective for ASR tasks involving low-resource languages. While conventional ASR models often rely on large labeled datasets from major languages like English[1], low-resource languages, such as Ika[5], Chinese, or Turkish (from the Covost v2 dataset), present greater challenges. In these cases, supervised training often produces erroneous or misleading results, particularly in sensitive domains or conversational speech scenarios[6]. Wav2Vec2, however, effectively mitigates these issues due to its robust architecture and ability to learn powerful representations from unlabeled speech audio.

The Wav2Vec2 model has demonstrated impressive performance in many ASR tasks by leveraging self-supervised learning (SSL) on large amounts of unlabeled data. However, its latent feature representations can be further optimized for specific downstream tasks, especially in low-resource settings. The BL-JUST method[7], which integrates joint self-supervised training and supervised fine-tuning, addresses this need. BL-JUST refines the Wav2Vec2 model by combining SSL with task-specific supervised learning (SL) in an iterative, two-step process. This approach enables Wav2Vec2 not only to learn general acoustic features but also to adapt these features for more effective performance on downstream ASR tasks.

In low-resource ASR tasks, where labeled data is often limited, the BL-JUST method becomes particularly valuable. By cycling between SSL and SL, BL-JUST enhances the model’s ability to generalize and adapt across different linguistic settings, making it well-suited for multilingual ASR challenges. This cyclic feedback mechanism allows Wav2Vec2 to incrementally improve its representations, making it more robust to dialectal variations, noise, and domain-specific requirements. BL-JUST's impact is especially significant for underrepresented languages, where traditional models often struggle. The combination of Wav2Vec2’s strong pre-training and BL-JUST’s task-specific fine-tuning enables the model to better handle low-resource languages like Dutch, Mongolian, and Arabic, as found in the Covost v2 dataset[8]. This integration demonstrates Wav2Vec2’s adaptability and performance improvements in low-resource, multilingual ASR tasks, addressing key challenges in the field[9,10].

The contributions of our method are twofold: first, we integrate BL-JUST with the Wav2Vec2 model to enhance the latent feature representations of Wav2Vec2. BL-JUST leverages recent advances in penalty-based optimization to address ASR challenges, while maintaining computational efficiency and ensuring convergence[7]; second, we demonstrate the model’s ability to generalize across multiple languages using the Covost v2 dataset, highlighting its performance in diverse multilingual settings[11].

By incorporating joint SSL and SL training steps, BL-JUST refines the learned feature representations of the Wav2Vec2 model beyond traditional fine-tuning, leading to superior performance in ASR tasks, particularly across a range of low-resource languages, compared to conventional approaches[4].

## Example Result

Three experiments were conducted to evaluate the model's performance in different learning rates, numbers of CNN and RNN layers, and low-resource datasets. The first example generated and compared WERs under different learning rate settings of BL-JUST using CNN-LSTM acoustic models on Librispeech. We used 3 CNN layers and 5 LSTM layers and kept them constant while changing the pre-training (α) and fine-tuning (β). The experiment result showed that when $\alpha = 10^{-3}$ and $\beta = 10^{-4}$, the WER was the lowest, and it was the optimal learning rates for the BL-JUST settings in this model. In the second experiment, we tested WERs under various number of CNN and LSTM layers settings of BL-JUST using CNN-LSTM acoustic models on Librispeech. As we increased the numbers oof CNN layers and LSTM layers, the WERs for Pre-training and Fine-tuning (PT+FT) and for BL-JUST both decreased while the number of parameters increased. For each numbers of CNN and LSTM layers, WER(PT+FT) was higher than WER(BL-JUST). As for the final experiment, we evaluated WERs of Wav2Vec2-JUST and Wav2Vec2 (FT) on Dutch, Mongolian, and Arabic languages using training datasets. For each low-resource language, the WER for Wav2Vec2 (FT) was higher than the one of Wav2Vec2-JUST. All the three methods demonstrate the effectiveness of our model on low-resource datasets using a combination of Wav2Vec2 architecture and BL-JUST on CNN-LSTM settings.

## Demonstration



## Installation

## Citation

[1] Jesin James, Deepa P Gopinath, et al. Advocating character error rate for multilingual asr evaluation. arXiv preprint arXiv:2410.07400, 2024.
[2] Geoffrey Hinton, Li Deng, Dong Yu, George E Dahl, Abdel-rahman Mohamed, Navdeep Jaitly, Andrew Senior, Vincent Vanhoucke, Patrick Nguyen, Tara N Sainath, and Brian Kingsbury. Deep neural networks for acoustic modeling in speech recognition: The shared views of four research groups. IEEE Signal processing magazine, 29(6):82–97, 2012.
[3] Alexei Baevski, Yuhao Zhou, Abdelrahman Mohamed, and Michael Auli. wav2vec 2.0: A framework for self-supervised learning of speech representations. Advances in neural information processing systems, 33:12449–12460, 2020.
[4] Ioannis Tsiamas, Gerard I Gállego, José AR Fonollosa, and Marta R Costa-jussà. Pushing the limits of zero-shot end-to-end speech translation. arXiv preprint arXiv:2402.10422, 2024.
[5] Uchenna Nzenwata and Daniel Ogbuigwe. Automatic speech recognition for the ika language. arXiv preprint arXiv:2410.00940, 2024.
[6] Samuele Cornell, Jordan Darefsky, Zhiyao Duan, and Shinji Watanabe. Generating data with text-to-speech and large-language models for conversational speech recognition. arXiv preprint arXiv:2408.09215, 2024.
[7] AFM Saif, Xiaodong Cui, Han Shen, Songtao Lu, Brian Kingsbury, and Tianyi Chen. Joint unsupervised and supervised training for automatic speech recognition via bilevel optimization. In ICASSP 2024-2024 IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP), pages 10931–10935. IEEE, 2024.
[8] Sheng Shi, Xuyang Cao, Jun Zhao, and Guoxin Wang. Joyhallo: Digital human model for mandarin. arXiv preprint arXiv:2409.13268, 2024.
[9] Yacouba Kaloga, Shakeel A Sheikh, and Ina Kodrasi. Multiview canonical correlation analysis for automatic pathological speech detection. arXiv preprint arXiv:2409.17276, 2024.
[10] Rishabh Jain, Andrei Barcovschi, Mariam Yahayah Yiwere, Dan Bigioi, Peter Corcoran, and Horia Cucu. A wav2vec2-based experimental study on self-supervised learning methods to improve child speech recognition. IEEE Access, 11:46938–46948, 2023.
[11] Yao-Fei Cheng, Hayato Futami, Yosuke Kashiwagi, Emiru Tsunoo, Wen Shen Teo, Siddhant Arora, and Shinji Watanabe. Task arithmetic for language expansion in speech translation. arXiv preprint arXiv:2409.11274, 2024.

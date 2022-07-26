# YoanoGAN
YoanoGAN (You Only Add Noise Once) is a generative adversarial network that uses a discriminator and a generator model to estimate correct distribution of noises to sample from and introduce to a medium with sole purpose of reducing the accuracy of any arbitrary classification model trained on noisy samples from the same medium.

Tensorboard integration supports many experiment metrics. These are:
- Generator Loss
- Discriminator Loss
- Generator output L2-norm
- Discriminator accuracy of noisy dataset
- Generator output visualization as image for pre-defined input seed (To observe semantic change throughout the experiment)
- Distribution and Histogram of Generator and Discriminator gradients throughout the experiment (To check for vanishing or exploding gradients)

The next phase of this project will be to mitigate mode collapse. The GAN architecture is conditional, which means it is highly likely to collapse into a single mode for every class. To mitigate this, class embeddings will be introduced to the generator model as styles similar to StyleGAN model. This implementation will be highly inspired from the recent research:

[**COLLAPSE BY CONDITIONING: TRAINING CLASS - CONDITIONAL GANS WITH LIMITED DATA**](https://arxiv.org/abs/2201.06578).

<img width="900" alt="Capture" src="https://user-images.githubusercontent.com/49740123/180964846-201551b2-2b69-4eb1-9e41-1b43facef56d.PNG">
The figure above is taken from the **Collapse by Conditioning** research paper. The model will be fairly close to the architecture of paper. The major difference is that since we want discriminator to predict the corresponding class of a sample, we cannot give the actual class as an embedding. Therefore, the loss function for the discriminator will be significantly different than the figure above


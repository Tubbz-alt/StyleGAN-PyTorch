# StyleGAN-PyTorch

This is a simple but complete pytorch-version implementation of Nvidia's Style-based GAN[3]. We've train this model on [our new anime face dataset](https://github.com/SiskonEmilia/Anime-Wifu-Dataset) and a subset of FFHQ, you can download our pre-trained model to evaluate or continue training by yourself.

## Preview

*Not available yet.*

## Versions

We provide you with two versions of implementations: the `SGAN.ipynb` for jupyter notebook with GUI and the `SGAN.py` for CLI only. 

With `SGAN.ipynb`, one can view the image generated by model every `n_show_loss` iterations, while the `.py` version will only save it to the folder you specify. Except that, there's no difference between these two versions.

## Parameters

As we did not provide you with any optional command parameters, you can only change them inside our code to match your requirement.

|Parameter|Description|
|:-:|:-:|
|n_gpu|number of GPUs used to train the model|
|device|default device to create and save torches|
|learning_rate|a dict to indicate learning rate at different stage of training|
|batch_size*|a dict to indicate batch size at different stage of training|
|mini_batch_size*|minimal batch size|
|n_fc|number of layers in the full-connected mapping network|
|dim_latent|dimension of latent space|
|dim_input|size of the first layer of generator|
|n_sample|how many samples will be used to train a single layer|
|DGR|how many times will discriminator be trained before training generator|
|n_show_loss|loss will be recorded every `n_show_loss` iterations|
|step|which layer to start training|
|style_mixing|layers to use 2nd style to evaluate|
|image_folder_path|path to the dataset folder that contains images|
|save_folder_path|path to the folder that generated images will be saved to|
|is_train|set to `True` if you want to train the model|
|is_continue|set to `True` if you want to load pre-trained model|

\*With suffix like '_2gpus', which means this parameter should be used (by removing the suffix) while using this number of GPUs. 

## Checkpoint

Our implementation support save trained model and load a existed checkpoint to continue training.

### Pre-trained model

*Not available yet.*

### Save model & continue training

When you train the model yourself, parameters of the model will be saved to `./checkpoint/trained.pth` every 1000 iterations. You can set `is_continue` to `True` to continue training from your pre-trained model.

## Changelog

- Working: Umi Iteration
  - TODO: Divide codes into files
  - TODO: Support evaluate-only mode
  - TODO: Support common metrics
  - 5/23: DEBUG: Leak of VRAM
  - 5/23: DEBUG: The change of alpha (used to decide the degree of crossover between different layers) is set to be linear[2].
  - 5/22: DEBUG: Now this model is able to train on multiple GPUs.
  - 5/22: DEBUG: Fix the bug that the adaptive normalization module does not participate in calculation and back-propagation.
- 5/16 - 5/19: Shiroha Iteration
  - 5/19: Construct [a new anime face dataset](https://github.com/SiskonEmilia/Anime-Wifu-Dataset)
  - 5/16: Able to continue training from a historic checkpoint
  - 5/16: Introduce style-mixing feature
  - 5/16: DEBUG: Fix the bug that the full connected mapping layer does not participate in calculation and back-propagation.
- 5/13 - 5/15: Kamome Iteration
  - 5/15: DEBUG: VRAM leak and shared memory conflict
  - 5/14: DEBUG: Parallel conflict on Windows (Due to the speed limit, we migrate to Linux platform)
  - 5/13: Introduce complete Progressive GAN[2] and its training method.
  - 5/12: Introduce R1 regularization[1] and constant input vector.
  - 5/12: Early implementation of Style-based GAN.

## References

[1] Mescheder, L., Geiger, A., & Nowozin, S. (2018). Which Training Methods for GANs do actually Converge? Retrieved from http://arxiv.org/abs/1801.04406

[2] Karras, T., Aila, T., Laine, S., & Lehtinen, J. (2017). Progressive Growing of GANs for Improved Quality, Stability, and Variation. 1–26. Retrieved from http://arxiv.org/abs/1710.10196

[3] Karras, T., Laine, S., & Aila, T. (2018). A Style-Based Generator Architecture for Generative Adversarial Networks. Retrieved from http://arxiv.org/abs/1812.04948
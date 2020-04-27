# Using the Pretrained Models

The magenta MusicVAE repository contained a number of pretrained models that I could experiment with before training my own model. I've documented my process below.

1. Download the .tar file for the model with ```cat-mel_2bar_big``` configuration at the following link: https://storage.googleapis.com/magentadata/models/music_vae/checkpoints/cat-mel_2bar_big.tar (Note: 1.7 GB large)

2. Sample new 2-bar music pieces from the latent space of this pre-trained model using the corresponding code in the ```COMMANDS.md``` file.

3. Interpolate between two of the newly generated 2-bar pieces using the corresponding code in the ```COMMANDS.md``` file.

The resulting MIDI files have been exported to the "results_sample" and the "results_interpolate" folders. By listening to these MIDI files, we can see that a number of short note sequences have been sampled from the latent space and that intermediate music progressions have been created via the interpolation commands.

Note: The ```music_vae_generate.py``` code is directly from the magenta repository and is only placed here for easy reference for the actual parameters and functionality of the generate function.

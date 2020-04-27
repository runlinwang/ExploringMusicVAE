# ExploringMusicVAE

## Inspiration

From learning about biologically-inspired models for novel machine learning methods, I came across the technique of using variational autoencoders (VAEs) to sample from an existing latent space. This sparked the idea of potentially creating new musical pieces using VAEs by sampling existing pieces.

I really wanted to explore this idea further for its potential therapeutic applications; certain types of music have been shown to suppress beta and gamma rhythms in the brain that are correlated with depression and anxiety. An effective VAE could create unique musical pieces that can reduce symptoms of depression and anxiety in patients, which would be incredibly valuable for helping some individuals improve their mental health.

## Approach

This project is oriented around utilizing a variational autoencoder framework to build a VAE model that can produce new music from existing samples. Using an autoencoder enables us to reduce the dimensionality of music, isolating key characteristics from the music which may be used to form new music. Specifically, a variational autoencoder was used to ensure that there was a distribution to draw new potential music from, reflecting the continuous nature of musical pieces. The VAE must also be recurrent/LSTM to support a musical sequence rather than discrete data, and it should be hierarchical to avoid any potential "posterior collapse" problem where the same music is simply regenerated.

With this criteria, I identified MusicVAE as the best suited existing framework for this project. MusicVAE is a framework developed under the magenta package, which relies heavily on TensorFlow. More information on how I used MusicVAE to interpolate between musical pieces, generate my own model, and sample new ones can be found in the README files in each of the respective folders listed below.

The music that I chose to use was a number of MIDI files qualitatively categorized as "calming" music by a MIDI music files repository. While I attempted to find EEG-linked music pieces that could be more directly relevant to the therapeutic application of reducing certain frequencies of brain waves, no such datasets were easily accessible or available publicly. A more clinically-oriented application of MusicVAE would ideally have correlated EEG data to these MIDI files; this project instead seeks to demonstrate the potential for MusicVAE to be used therapeutically and its specific implementation strategies.

All development took place locally, but for learning purposes I used some tutorials in Jupyter notebooks that can be found in the "resources" folder.

## Methodology

1. Learn more about the magenta/MusicVAE framework and commands, as well as VAEs in general through external resources. (found in the "resources" folder)
2. Explore the pretrained models for MusicVAE and their functionality. (all in "pretrained" folder)
  a. Interpolate musical sequences between arbitrary givens
  b. Sample new music from the pre-trained system
2. Use calming music data in rudimentary model (found in the "own_model" folder)
  a. Interpolating using the pretrained model but between our own musical sequences
  b. Training my own model on the calming music to sample new note sequences from

Please navigate to the respective folders to find more information about the specific methodology of my project at each stage.

## Results

For each of the above steps, music MIDI files have been generated using the MusicVAE models in various forms, and these MIDI files are shown in their respective folders.

By using the existing pre-trained model to interpolate between calm music samples, I was able to create a sequence of intermediate sequences between the two music samples that sounded melodically coherent. This is the most effective, direct way of creating a piece of music that shares the characteristics of two otherwise unrelated pieces.

In addition, after extensive tinkering and learning, I was able to create a working model that allowed us to successfully sample music from the latent space and create new music based on the characteristics of the training samples. However, this music was still relatively discordant and much less melodical than the interpolation samples. There are a number of reasons for this, including model training capacity and size of training set, that are discussed further in the REFLECTION.md document.

However, the actual samples created from the pretrained model also reflected some elements of being discordant. For example, when using the pretrained model in the .ipynb file, the music samples created did have elements of melodies but still had strange discordant elements, whether it be an irregular beat or contrasting note sounds. This indicates that the challenges I faced through sampling from my own model may be a common issue when using the sampling technique from MusicVAE model, suggesting limitations in the ability to sample unique music that sounds "normal" to human ears.

## Conclusion

In conclusion, the idea of using a variational autoencoder system to create new music from existing samples with specific characteristics is definitely valid and holds extensive potential for the future, but still faces a number of limitations today. Using rigorously pre-trained models to interpolate between two pieces of music with similar characteristics, such as sounding calm to human ears, produces many intermediate bars of music that successfully emulate the "calm" effect of music through computer-generated music sequences.

However, when attempting to sample from a latent space consisting of more than 2 musical pieces, it results in much more discordant pieces of music. The musical notes still resemble the original music pieces in some elements, but just feels far less smooth or calm than the originals.

As such, while the idea of using VAEs to generate music is solid in principle, more development of the actual sampling techniques and frameworks is required to produce music with similar characteristics to the original music, at least with smaller datasets and shorter pieces of music.

## Sources

The following sources were incredibly useful, either to learn more about VAE structures or provide source code or system packages information. They are cited here to ensure proper attribution of code/ideas to their respective owners.

https://github.com/tensorflow/magenta/tree/master/magenta/models/music_vae
https://magenta.tensorflow.org/music-vae
https://arxiv.org/pdf/1803.05428
https://machinelearningmastery.com/learning-rate-for-deep-learning-neural-networks/
https://stats.stackexchange.com/questions/267924/explanation-of-the-free-bits-technique-for-variational-autoencoders
https://github.com/tensorflow/magenta/issues/1369
https://github.com/MaybeShewill-CV/CRNN_Tensorflow/issues/311
https://support.apple.com/en-ca/guide/terminal/apdc52250ee-4659-4751-9a3a-8b7988150530/mac
https://groups.google.com/a/tensorflow.org/forum/#!topic/magenta-discuss/8nF8VwfVSuo
https://blogs.oracle.com/datascience/types-of-machine-learning-and-top-10-algorithms-everyone-should-know-v2
Bioai Deep Learning Safari Jupyter Notebook, received from Colin Conwell
MusicVAE Tutorial Jupyter Notebook, received from Magenta MusicVAE repository

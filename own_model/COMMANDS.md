# Commands

All of the following commands were run in this directory on the command line. By setting up the repositories in the same way as indicated in SETUP.md in the parent repository, these commands can be used on any local system as well. I learned these command features and largely based them off of those described from magenta GitHub and other online sources, referenced in the parent directory README.

### For generating compatible 2-bar length MIDI segments from cleaned MIDIs with 1 track:

```sh
music_vae_generate \
--config=cat-mel_2bar_big \
--checkpoint_file=path/to/cat-mel_2bar_big.tar \
--mode=interpolate \
--num_outputs=5 \
--input_midi_1=path/to/sample1.mid \
--input_midi_2=path/to/sample2.mid \
--output_dir=training_data
```
Note: This method uses a built-in system in the "music_vae_generate" function that automatically outputs compatible 2-bar snippets from incompatible longer MIDIs. This is the same function as that used for the pretrained model, except the function is to create compatible MIDIs for the rest of the model training process instead of actually generating interpolated music. Repeat this function for each sample MIDI that needs to be converted.

### For interpolating between the 2-bar snippets using the pretrained model:

```sh
music_vae_generate \
--config=cat-mel_2bar_big \
--checkpoint_file=path/to/cat-mel_2bar_big.tar \
--mode=interpolate \
--num_outputs=5 \
--input_midi_1=training_data/morning1.mid \
--input_midi_2=training_data/evergreen2.mid \
--output_dir=interpolate
```
Note: morning1.mid and evergreen2.mid could be replaced with any two of the training data MIDI files.

### For converting MIDIs into NoteSequences for TensorFlow:

```sh
INPUT_DIRECTORY=training_data
SEQUENCES_TFRECORD=notesequencesupdated.tfrecord

convert_dir_to_note_sequences \
--input_dir=$INPUT_DIRECTORY \
--output_file=$SEQUENCES_TFRECORD \
--recursive
```

### For training the model on my own data:

```sh
music_vae_train \
--config=cat-mel_2bar_big \
--run_dir=results/train \
--mode=train \
--examples_path=notesequencesupdated.tfrecord \
--hparams=max_seq_len=32, z_size=512, free_bits=0, max_beta=0.5, beta_rate=0.99999, batch_size=512, grad_clip=1.0, clip_mode='global_norm', grad_norm_clip_to_zero=10000, learning_rate=0.01, decay_rate=0.9999, min_learning_rate=0.00001
```
Note: Most significant changes in these commands are in the hyperparameters. While the vast majority of these hyperparameters align well with the recommended/default options for MusicVAE, I increased the initial learning rate to 0.01 to increase the speed that the model was training on my CPU. See ```REFLECTION.md``` in the parent directory for more about the challenges and reasoning behind using a CPU over a GPU.

### For sampling from my new model:

```sh
music_vae_generate \
--config=cat-mel_2bar_big \
--checkpoint_file=/path/to/model.ckpt \
--mode=sample \
--num_outputs=5 \
--output_dir=results/samples
```

# Commands

All of the following commands were run in this directory on the command line. By setting up the repositories in the same way as indicated in SETUP.md in the parent repository, these commands can be used on any local system as well.

### For sampling from the pretrained model:

```sh
music_vae_generate \
--config=cat-mel_2bar_big \
--checkpoint_file=path/to/cat-mel_2bar_big.tar \
--mode=sample \
--num_outputs=5 \
--output_dir=results_sample
```

### For interpolating between two samples using the pretrained model:

```sh
music_vae_generate \
--config=cat-mel_2bar_big \
--checkpoint_file=path/to/cat-mel_2bar_big.tar \
--mode=interpolate \
--num_outputs=5 \
--input_midi_1=path/to/sample1.mid \
--input_midi_2=path/to/sample2.mid \
--output_dir=results_interpolate
```
Note: Any two samples can be inputted as the input MIDI files, given that they only have notes on track 1 of the MIDI file and are exactly 2 bars in length.

# Sound Separator: ICA Demonstration

This project was intended to **study and demonstrate the use of Independent Component Analysis** [[1](https://www.sciencedirect.com/science/article/pii/S2210832718301819),[2](http://arnauddelorme.com/ica_for_dummies/),[3](http://efavdb.com/independent-component-analysis/)] for **separation of mixed recorded sound** to its original independent sources.

The recording of the audio signals and the **synchronization of their start times (based on their convolution) seemed to go well** (see screenshot below).
However, the **decomposition of the independent components** (using SKlearn's implementation of [FastICA](https://scikit-learn.org/stable/auto_examples/decomposition/plot_ica_blind_source_separation.html)) **yielded quite poor results**.
This could be caused by complex or internally-heterogeneous sources such as FOX-news or outside background noise (see the recording layout [here](https://github.com/ido90/SoundSeparator/blob/master/signal_separator-Copy1.ipynb#Recording-Layout)), which effectively cause more than N independent sources.
It is also possible that the recorded volume of the sources was not balanced enough, although few more recording attempts (including simplified ones) did not yield significantly better separation.

| ![](https://github.com/ido90/SoundSeparator/blob/master/signals_sync_demonstration.png) |
| :--: |
| The convolutions that were used to synchronize the recorded signals. |

As a fallback, separation of a toy example (see [here](http://www.cs.ubbcluj.ro/~csatol/mach_learn/) under "Independent Component Analysis of Recordings") was attempted.
Even though the source sounds are quite monotonous, homogeneous and unique, FastICA seemed to successfully reconstruct only 2 out of the 4.

Although the failure was not investigated far beyond this brief description,
I guess that out-of-the-box ICA is just not strong enough to do a good job on arbitrary and complex everyday-sounds (unless I terribly messed-up something in the few lines of code applying the ICA, which is always a reasonable possibility).

## Implementation and use

Due to regrettable ffmpeg issues, all used audio files are of WAV format, using the kind help of [this](https://audio.online-convert.com/convert-to-wav) online converter.

Since the results were not so promising, I did not bother converting the notebook into a module.
Thus, to apply it on a new input, one should copy the basic notebook, modify the paths variables in the beginning and run (as demonstrated [here](https://github.com/ido90/SoundSeparator/blob/master/signal_separator-Copy1.ipynb)).

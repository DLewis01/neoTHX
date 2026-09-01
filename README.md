# neoTHX
A THX like BRRRRRRRRAAAAAAAAAAAAAA tone
changing the target frequency, while the oscillator's actual frequency followed that target through a low-pass/one-pole smoothing process.
So mathematically you can think of each oscillator as approximately:
$$ f_n(t+1)=f_n(t)+\alpha\left(f_{target,n}(t)-f_n(t)\right) $$
where:
\(f_n\) = current oscillator frequency
\(f_{target,n}\) = currently assigned target
\(\alpha\) = smoothing coefficient
The smaller the smoothing coefficient, the more slowly the oscillator approaches its target.
That gives you the characteristic glissando rather than a sequence of discrete pitch jumps.

loop through the voices once per second, assigning each one another random pitch.
So you might get:
time       V1      V2      V3      V4
-----------------------------------------
0 sec      273     341     218     387
1 sec      301     229     366     274
2 sec      248     319     207     352
3 sec      335     211     298     381

smoothers prevent those changes from being instantaneous
At a predetermined point, the random behaviour stops.
The program effectively says:
STOP RANDOM TARGETS

Voice 1  → target frequency A
Voice 2  → target frequency B
Voice 3  → target frequency C
...
Voice 30 → target frequency D
But the oscillator doesn't jump to its final frequency.
The frequency smoother now causes every voice to glide toward its assigned final pitch.

based around a 150 Hz root,
| Target | Frequency |
| ------ | --------: |
| 1      |   37.5 Hz |
| 2      |     75 Hz |
| 3      |    150 Hz |
| 4      |    300 Hz |
| 5      |    600 Hz |
| 6      |    900 Hz |
| 7      |   1200 Hz |
| 8      |   1500 Hz |
| 9      |   1800 Hz |

37.5
  ×2
75
  ×2
150
  ×2
300
  ×2
600
  ×1.5
900
  ×4/3
1200
  ×1.25
1500
  ×1.2
1800

retained small amounts of detuning to produce beats

algorithmically faithful without being bit-for-bit identical to the original. The 200–400 Hz range, 30 voices, cello waveform, one-pole smoothing, random reassignment, 150-Hz-root final structure and deliberate residual detuning are directly supported by Moorer's accounts; some of the detailed target-frequency tables circulating today are reconstructions rather than Moorer's complete published source


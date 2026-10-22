# The Sound of a Name

A small generative project that turns any name into a **song** and a **picture**, using the Fibonacci sequence.

Type a name, press Play, and watch and listen. Every name makes something different.

**Live version:** https://2245310.github.io/the-sound-of-a-name/

## The idea

A name is the smallest piece of data a person carries. This project asks: can a set of simple rules give every name its own sound and look? Nothing in the song is chosen note by note. The rules choose, and the name is the input.

## How it works, in simple words

1. **Letters become numbers.** a = 1, b = 2 … z = 26. So the **m** in Maya is 13.
2. **Each number gets a loop.** The Fibonacci sequence goes 0, 1, 1, 2, 3, 5, 8, 13 … where each number is the two before it added together. If we only keep the remainder after dividing by a letter's number (this is called *mod*), the sequence always ends up repeating. So every letter gets its own repeating pattern. For m (mod 13) the pattern is 28 numbers long. For h (mod 8) it is 12.
3. **Each number in the loop is one beat of music.** The letters play one after another, and each letter's loop is played once.
4. **The whole name sets the mood.** The sum of the letters sets the speed and the key.
5. **The song is drawn as a record.** Each letter is a ring, each dot is a beat, and the shape of a dot shows what happens on that beat.

## The rules

| What | Where it comes from |
|---|---|
| Tempo | 80 + (sum of all letter numbers mod 80) BPM |
| Root note | sum of letter numbers mod 12 |
| Scale | first letter's number mod 6 (Ionian, Dorian, Phrygian, Lydian, Mixolydian, Aeolian) |
| Chord thickness | number of letters (how far the chord's saw waves are detuned, in cents) |
| Section length | the loop length, one bar per 4 beats, rounded up |
| Rest | loop value 0 |
| Bass note | loop value mod 7 (a scale note), one octave up for every 7 |
| Lead note | same note, two octaves up, played on the "and" of the beat; its length is value mod 3 |
| Chord | built on the loop value of the first beat of each bar |
| Extra hi-hats | when the value is a multiple of 3 |
| Ghost snare | when the value is a multiple of 5 |
| Chord wobble | speed: (n mod 4) + 1 cycles per bar; depth: n ÷ 26 |
| Pause between words | one bar of drums only |

**Fixed in every song:** 4/4 time, the drum skeleton (kick on every beat, snare on beats 2 and 4, hi-hat on the "and"), and the sound recipes.

**Random:** only a tiny change in timing and volume, controlled by a seed. It never changes the notes.

## Example: "maya ramesh"

- Letters: 13, 1, 25, 1, 18, 1, 13, 5, 19, 8, which add up to 104.
- Tempo 104 BPM, root G#, scale Dorian (13 mod 6 = 1).
- Loop lengths in beats: m 28, a 1, y 100, r 24, e 20, s 18, h 12.
- The song is 62 bars, about 2 minutes 23 seconds.

## How to read the picture

- Each **ring** is one letter. The first letter is in the middle.
- Read each ring **clockwise from the top**, one dot per beat.
- A dot closer to the inside of its ring has a smaller number.
- Short ticks mark the start of each bar.

| Shape | Meaning |
|---|---|
| Hollow circle | rest (value 0) |
| Filled circle | a note |
| Triangle | a note plus extra hi-hats |
| Square | a note plus a ghost snare |
| Diamond | a note plus both |

## How to run it

1. Download or clone this repository.
2. Open `index.html` in a browser (Chrome works well).
3. Type a name, press **Play**.
4. Use **New take** to change only the small timing feel, **Save PNG** to save the picture, and **Loop playback** to repeat.

No installation is needed.

## Known limits

- The letter **y** has a 100-beat loop, so it takes up a large part of any song that contains it.
- Fibonacci always starts 0, 1, 1, 2, 3, so long sections open in a similar way for every name.
- The lead and the chords are built from different parts of the loop, so some notes clash on purpose.

## Folder

- `index.html`: the whole project (sound, drawing and controls).
- `proposal/`: the A2 proposal.
- `sketches/` and `screenshots/`: early drawings and outputs.

## References

- Nadieh Bremer's Sony Music data art, for the circular, record-like layout.
- Brian Eno, *Music for Airports*, for the idea of loops that repeat and drift.
- Ryan Hedgecock's video on building musical sound from scratch, for the sound recipes (waves, LFOs, envelopes, unison, drums).

## Credits

Made by Maya. Built with the help of AI tools (Claude and Antigravity).

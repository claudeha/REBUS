# REBUS

REBUS - Electromagnetic Interactions

https://xname.cc/rebus

the composition api abstracts the common code between compositions

## platforms

### bela with rebus (antennas)

default mode, configured by

```
#define MODE MODE_REBUS
```

### bela with gui (mouse cursor)

change

```
#define MODE MODE_REBUS
```

to

```
#define MODE MODE_BELA
```

or add `CPPFLAGS=-DMODE=1` to bela make options

important notes:

- mouse cursor control is very low resolution in both time and space

- character of movement is completely different

- provided for development purposes only

### desktop with JACK (audio in port)

dive into git history to find this

### desktop with SNDFILE (audio file input)

dive into git history to find this

## scope

audio out x2, audio in x2, magnitude, phase

## audio recording

64MB/min (1GB/15mins) 6ch wav:

- audio out x2
- audio in x2
- magnitude
- phase

filename is named after current localtime and composition name

## composition API

in `project/render.cpp`

include:

```
#include <libraries/REBUS/REBUS.h>
```

implement:

```
const char *COMPOSITION_name = "will-be-put-in-wav-filename";
struct COMPOSITION { /* stuff here */ };
inline bool COMPOSITION_setup(BelaContext *context, COMPOSITION *C) { /* stuff here */ }
inline void COMPOSITION_render(BelaContext *context, COMPOSITION *C, float out[2], const float in[2], const float magnitude, const float phase) { /* stuff here */ }
inline void COMPOSITION_cleanup(BelaContext *context, COMPOSITION *C) { /* stuff here */ }
```

at the end of the file:

```
REBUS
```

(this macro instantiates the Bela API functions
so that they call the composition functions)

## libraries

run `make -C libraries install` to copy to bela.local

warning: there is no undo; make a backup first if desired

## examples

run `make -C examples install` to copy to bela.local

warning: there is no undo; make a backup first if desired

### composition-api

retriggered decaying complex oscillator

## projects

run `make -C projects zip` to create zip files for each project

then you can upload them to the Bela IDE with drag and drop

### boids

a flock of oscillators

### dub-terrain

beats, delays and filters

### i-spectral

extreme pitch shift turns motion into sound

### spectrifier

the original

### stringthing

spinning string drone physical model

### uneven-terrain

techno landscape with waveshaped beats
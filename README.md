# Transpose.js
A Javascript library for music transposition using simple JSON objects.

# Usage
Transpose.js allows you to create and edit individual notes, scales, and chords as JSON.

If you're trying to make a music based web app in the browser, Transpose.js
gives the data you need quickly in a simple format. 

### Creating Individual Note Objects

Notes are contain information about note name, MIDI note number, and octave. 

    var note = getNote("C");
    console.log(note)

Output: 

        {
            "name":"C",
            "midi":60,
            "octave":3
        }

By default, notes are initialized in the middle octave from C3 to B3.

Transpose.js follows the octave numbering convention for computer music
in which C3 = the MIDI note 60. 

In this convention, MIDI octave numbers range from from -2 to 8. An octave
below middle C is therefore C2, and so on.

### Shifting Individual Notes

    var note = getNote("C");
    var fifthDown = shiftNote(note, -5);

Output:

        {
            "name":"G",
            "midi":55,
            "octave":2
        }

### Creating Scales

You can create scales by passing in the name of the root node, and the mode of 
the scale:

    var scale = getScale("C", "Major");
    console.log(scale)

Output: 

    {
        "root":"C",
        "mode":"Major",
        "notes":[
              {
                 "name":"C",
                 "midi":60,
                 "octave":3
              },
              {
                 "name":"D",
                 "midi":62,
                 "octave":3
              },
              {
                 "name":"E",
                 "midi":64,
                 "octave":3
              },
              {
                 "name":"F",
                 "midi":65,
                 "octave":3
              },
              {
                 "name":"G",
                 "midi":67,
                 "octave":3
              },
              {
                 "name":"A",
                 "midi":69,
                 "octave":3
              },
              {
                 "name":"B",
                 "midi":71,
                 "octave":3
              }
       ]
    }

By default, you can enter the name of any diatonic mode when you create a scale:

    var prettyScale = getScale("E", "Lydian");

"Major" can be used interchangably with "Ionian",
"Minor" can be used interchangably with "Aeolian", and
"Dominant" can be used interchangably with "Mixolydian".

For example:

    var dom = getScale("G", "Dominant");
    var mix = getScale("G", "Mixolydian"); // same exact object as dom

### Creating modal scales for each scale degree

You can also get modal scales that correspond to each degree in an existing
scale. For example, we can get the modes 

    var scale = getScale("C", "Major");
    var modes = getModes(scale);
    console.log(modes)

Output 
    
    {  
       "name":"Modes of C Major",
       "modes":[  
          {  
                 "root":"D",
                 "mode":"Dorian",
                 "notes":[  
                    {  
                       "name":"D",
                       "midi":62,
                       "octave":3
                    },

                ...

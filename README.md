# Rock Band Overdrive Tool
Pass in a path to a song file, returns the optimal overdrive path in a file.

Pass in a band option flag and four song files (1 per instrument) to return the optimal band overdrive path.

Config file lists multipliers, point values, overdrive lengths, etc

Song file format just knows which instrument and the song. Each note knows how many base notes there are, how long the note is, if it is sustained (guitar/Bass only), if it grants OD and how much OD (account for sustained wammys too), if it can be activated on the note (drums and vox only (vox only during rests)). A note can be a rest.

Notes are divided into measures. Each measure has a time signature and self validates that the measure has all of its beats accounted for.

Errors give the relevant line numbers and a print out of the line.

Songs validate that every startOD has an endOD.

Everything in the song file is NOT case sensitive.

Indents are optional (just look for next measure or EOF) but things on a line need any amount of non-newline white space  between elements.

&#35; this is a comment

Example:

guitar

measure 4/4 &#35; the total ratio below should match this ratio (both are "1")
    1 1/4 sustain startODx1 &#35; the 1 stands for "1 note"
    0 1/4 &#35; 0 is effectively a rest
    3 1/8
    3 1/8
    2 1/16
    2 1/16
    2 1/16
    2 1/16

m 3/4 &#35; only need 3/4 now, can shorten to just m
    2 1/4 sustain endOD &#35; quarter note (still OD wammyable)
    1 1/16 &#35; 16th note
    1 1/16
    2 1/8 &#35; 8th note
    1 1/12 &#35; triplet
    1 1/12
    1 1/12

    &#35; total for above is 3/4, which matches our time signature of 3/4, so we're good.

m &#35; defaults to last time signature used
    ... &#35; rest of song below
    

Highly suggest recording a video of the song being played and using that to make the song file...
   


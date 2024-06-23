Whenever I make a sound I will label it as *sound*


## stack syntax
Play multiple layers in parallel
```
stack (
  s("[bd]!3 [bd]!3 ~ ~ bd"),
  s("hh ~ hh ~ ")
).cpm(60)
```


## *sound* beater 
```
stack (
  s("[bd]!3 [bd]!3 ~ ~ bd"),
  s("hh ~ hh ~ "),
  note ("c d e").sound("sawtooth")
).cpm(300)
```


## pick random element for single beat
```
<list(elements)>
```

## pick random element, play on all beats
```
("hh | bd | sd")
```


## display stacks
```
.pianoroll()
```



// "Vibra Chimes" @by Smooth_head_corner
n("[<0 1 3 5> .. <6 7 9>]*<1.5 3 2 2.5>")
.scale("<A4:ionian E3:pentatonic>")
.sound("[handchimes vibraphone]").att(saw.range(0, 0.1).fast(6))
.release(1).pan(rand).decay(rand.range(0.1, 2))
.sometimesBy(0.5, x=>x.jux(rev))
.speed(rand.range(1 , 1.02))
.vib(1).vibmod(.1)
.room(.5)
._pianoroll()

// @version 1.0




## *sound* drum beat

```
stack(
s("[bd <bd ~> hh ~ cp ~ bd ~  hh:4 bd <cp oh> ~ sd ~ hh:3 hh], [hh oh:2]*1")
    .bank("RolandTR909")
    .distort(6)
    .gain(0.5)
    .delay("<0.0001@3 0.2>:0.02:0.5")
    .room(saw.rangex(0.1,"<0.2 0.4 0.6 1>".slow(2)).slow(8))
    .end("[0.01|0.05|0.2]*8")
).cpm(50)
```



## *sound* combined stack
```
stack(
  s("[bd <bd ~> hh ~ cp ~ bd ~  hh:4 bd <cp oh> ~ sd ~ hh:3 hh], [hh oh:2]*1")
    .bank("RolandTR909")
    .distort(6)
    .gain(0.5)
    .delay("<0.0001@3 0.2>:0.02:0.5")
    .room(saw.rangex(0.1,"<0.2 0.4 0.6 1>".slow(2)).slow(8))
    .gain(slider(5,0,5))
    .end("[0.01|0.05|0.2]*8"),
  n("[<0 1 3 5> .. <6 7 9>]*<1.5 3 2 2.5>")
    .scale("<D4:dorian E3:locrian>")
    .sound("[handchimes vibraphone]").att(saw.range(0, 0.1).fast(6))
    .release(1).pan(rand).decay(rand.range(0.1, 2))
    .sometimesBy(0.5, x=>x.jux(rev))
    .speed(rand.range(1 , 1.02))
    .vib(1).vibmod(.1)
    .gain(slider(3,0,3))
    .room(.5),
  note("c*8").sub(note(24))
  .s("<wt_dbass>/4")
  .distort(4)
  .lpenv(-2).lpa(.1)
  .lpf(saw.range(400,4000).slow(32))
  .ftype('24db').lpq(4)
  .adsr(".01:.1:<0 .5>:.2")
  .gain(slider(5,0,5))
  .n(saw.range(0,20).round())
).cpm(slider(50,0,50)).pianoroll()
```
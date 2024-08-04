# camera spec per evb

* ref: http://amsdottorato.unibo.it/8628/1/rusci_manuele_tesi.pdf


## compare

* (1) WE-I(himax_) :  camera module : hm0360 : QVGA (S2) 2FPS 140 µA  
* [(2)onsemi arx3a0](arx3a0.md)

* (3) esp(eye/32cam) camera module : ov2640
* SparkFun Edge(Apollo3)
  * (4)OV7670    : 
  * (5)HM01B0    : <2mW at QVGA 30FPS


* [(6)AMS nanEYE](ams.md)

* [(7)opta](opta.md)



```
              PW      PW    FPS
LowPower
(1)HM0360            140µA  2
(2)arx3a0    3.2 mW         360       ; detect motion 
(5)HM01B0     1.1mW         30        ; QQVGA 30FPS.

toys
(3)ov2640     15mV/s
            125-140 mW
(4)OV7670

shortFocus
(6)nanEYE                             ; 1X1 ; 3mLine
(7)optaOsiris

```


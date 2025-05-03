# git app tree


```
/MAX78xxx-RefDes/maxrefdes178-FacialRecognition
===============================================

├── maxrefdes178_max32666
│   ├── db_gen
│   ├── gen_db.sh
│   ├── include
│   ├── Makefile
│   ├── maxrefdes178_max32666.ld
│   ├── run.sh
│   └── src
├── maxrefdes178_max78000_audio
│   ├── include
│   ├── Makefile
│   ├── maxrefdes178_max78000_audio.ld
│   ├── run.sh
│   └── src
├── maxrefdes178_max78000_common
│   ├── max78000_debug.h
│   ├── max78000_qspi_slave.c
│   ├── max78000_qspi_slave.h
│   ├── max78000_softmax.c
│   └── max78000_tornadocnn.h
├── maxrefdes178_max78000_video
│   ├── include
│   ├── Makefile
│   ├── maxrefdes178_max78000_video.ld
│   ├── run.sh
│   └── src
├── README.md
└── SDCardBinaries
    ├── database.bin
    ├── weights_2.bin
    └── weights_3.bin
```

The SD Card should contain three binaries: 

* "weights_2.bin" is used to load weights of the FaceID model, 

* "weights_3.bin" is used to load weights of the DotProducts 

* "database.bin" is used to keep track of the recorded people


# HelloWorld

* https://github.com/tensorflow/tensorflow/blob/master/tensorflow/lite/micro/examples/hello_world/README.md 

```
get the code:   
git clone https://github.com/tensorflow/tensorflow

Download related third party data
make -f tensorflow/lite/micro/tools/make/Makefile TARGET=himax_we1_evb third_party_downloads

Generate hello world project
make -f tensorflow/lite/micro/tools/make/Makefile generate_hello_world_make_project TARGET=himax_we1_evb TAGS=no_arc_mli


```

cd /tensor/tensorflow/tensorflow/lite/micro/tools/make/gen/himax_we1_evb_arc_default/prj/hello_world/make
make app

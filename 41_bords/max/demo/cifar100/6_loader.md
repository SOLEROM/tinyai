# Network Loader 

* creates C code that programs the MAX78000/MAX78002 (for embedded execution, or RTL simulation)
* the generated code contains sample input data and the expected output for the sample, as well as code that verifies the expected output

## ai8xize

input

```
(1) A quantized checkpoint file
(2) A YAML description of the network
(3) A NumPy “pickle”  .npy  file with sample input data
```

output

```
main.c  contains the wrapper code
        loads a sample input
        verifies the output for the sample input.  
        
cnn.c   contains functions that are generated for a specific network
        to load, configure, and run the accelerator.

```
* this split makes it easier to swap out only the network while keeping customized wrapper code intact;


### help

```
./ai8xize.py --help           
usage: ai8xize.py [-h] (--ai85 | --device device-name) [--avg-pool-rounding] [--simple1b] [-e | --rtl | --rtl-preload] [--rtl-preload-weights] [--pipeline | --no-pipeline] [--pll | --no-pll]
                  [--balance-speed | --max-speed | --clock-divider N] --config-file S [--checkpoint-file S] [--board-name S] [--display-checkpoint] --prefix S [--debugwait N] [--define S]
                  [--define-default-arm S] [--define-default-riscv S] [--eclipse-includes S] [--eclipse-variables S] [--eclipse-openocd-args S] [--overwrite] [--compact-data | --no-compact-data]
                  [--compact-weights] [--mexpress | --no-mexpress] [--mlator] [--unroll-mlator N] [--unroll-8bit N] [--unroll-wide N] [--softmax] [--unload | --no-unload] [--no-kat] [--boost S]
                  [--start-layer N] [--no-wfi] [--timer N] [--no-timer] [--energy] [--switch-delay N] [--output-width {8,32}] [--no-deduplicate-weights] [--no-warn-zero] [--c-filename S]
                  [--api-filename S] [--weight-filename S] [--sample-filename S] [--sample-input S] [--sample-output-filename S] [--sample-numpy-filename S] [--fifo] [--fast-fifo] [--fast-fifo-quad]
                  [--no-fifo-wait] [--fifo-go] [--slow-load N] [--debug-new-streaming] [--riscv] [--riscv-flash | --no-riscv-flash] [--riscv-cache | --no-riscv-cache] [--riscv-debug] [--riscv-exclusive]
                  [-v] [-L] [--no-log] [--no-progress] [--log-intermediate] [--log-pooling] [--short-log] [--log-filename S] [-D] [--debug-computation] [--debug-latency] [--no-error-stop] [--stop-after N]
                  [--skip-checkpoint-layers N] [--skip-yaml-layers N] [--stop-start] [--one-shot] [--repeat-layers N] [--clock-trim LIST] [--fixed-input] [--reshape-inputs] [--forever] [--link-layer]
                  [--read-ahead] [--calcx4] [--ext-rdy] [--weight-start N] [--ignore-bias-groups] [--kernel-format S] [--debug-snoop] [--snoop-loop] [--ignore-hw-limits] [--ignore-bn]
                  [--ignore-activation] [--ignore-energy-warning] [--ignore-mlator-warning] [--new-kernel-loader | --old-kernel-loader] [--weight-input S] [--bias-input S] [--input-csv S]
                  [--input-csv-format N] [--input-csv-retrace N] [--input-csv-period N] [--input-pix-clk N] [--input-sync] [--input-fifo] [--autogen S] [--autogen_list S] [--input-filename S]
                  [--output-filename S] [--output-config-filename S] [--output-data-filename S] [--output-weights-filename S] [--output-bias-filename S] [--output-pass-filename S] [--runtest-filename S]
                  [--legacy-test] [--legacy-kernels] [--test-bist] --test-dir S [--top-level S] [--queue-name S] [--timeout N] [--result-output] [--overlap-data] [--override-start N] [--increase-start N]
                  [--override-rollover N] [--override-delta1 N] [--increase-delta1 N] [--override-delta2 N] [--increase-delta2 N] [--ignore-streaming] [--allow-streaming] [--no-bias [[LIST]]]
                  [--streaming-layers LIST] [--powerdown] [--deepsleep] [--max-proc N] [--input-offset N] [--verify-writes] [--verify-kernels] [--mlator-noverify] [--write-zero-registers] [--init-tram]
                  [--zero-sram] [--pretend-zero-sram] [--zero-unused] [--apb-base N] [--ready-sel N] [--ready-sel-fifo N] [--ready-sel-aon N] [--input-split N] [--synthesize-input N]
                  [--synthesize-words N] [--max-verify-length N] [--no-version-check] [--version-check-interval HOURS] [--upstream REPO] [--yamllint S]

MAX7800X CNN Generator

optional arguments:
  -h, --help            show this help message and exit

Device selection:
  --ai85                set device to MAX78000
  --device device-name  set device

Hardware features:
  --avg-pool-rounding   round average pooling results (default: false)
  --simple1b            use simple XOR instead of 1-bit multiplication (default: false)

Embedded code:
  -e, --embedded-code   generate embedded code for device (default)
  --rtl, --rtl-sim      generate RTL sim code instead of embedded code (default: false)
  --rtl-preload         generate RTL sim code with memory preload (default: false)
  --rtl-preload-weights
                        generate RTL sim code with weight memory preload (default: false)
  --pipeline            enable pipeline (default: enabled where supported)
  --no-pipeline         disable pipeline
  --pll                 enable PLL (default: automatic)
  --no-pll, --apb       disable PLL (default: automatic)
  --balance-speed       balance data and weight loading speed and power (default: true)
  --max-speed           load data and weights as fast as possible (MAX78002 only, requires --pll, default: false)
  --clock-divider N     CNN clock divider (default: 1 or 4, depends on clock source)
  --config-file S       YAML configuration file containing layer configuration
  --checkpoint-file S   checkpoint file containing quantized weights
  --board-name S        set board name (default: EvKit_V1)
  --display-checkpoint  show parsed checkpoint data
  --prefix S            set test name prefix
  --debugwait N         set the delay in seconds before calling __WFI() (default: 2)
  --define S            additional #defines for Makefile and auto-generated Eclipse project files (default: None; use quotes to specify multiple, separated by space)
  --define-default-arm S
                        override default ARM #defines for Makefile and auto-generated Eclipse project files (default: 'MXC_ASSERT_ENABLE ARM_MATH_CM4'; use quotes to specify multiple, separated by space)
  --define-default-riscv S
                        override default RISC-V #defines for Makefile and auto-generated Eclipse project files (default: 'MXC_ASSERT_ENABLE RV32'; use quotes to specify multiple, separated by space)
  --eclipse-includes S  additional includes for auto-generated Eclipse project files (default: None)
  --eclipse-variables S
                        additional variables for auto-generated Eclipse project files (default: None)
  --eclipse-openocd-args S
                        set the OpenOCD arguments for auto-generated Eclipse project files (default: -f interface/cmsis-dap.cfg -f target/<part>.cfg)

Code generation:
  --overwrite           overwrite destination if it exists (default: abort)
  --compact-data        use memcpy() to load input data in order to save code space (default)
  --no-compact-data     inline input data loader (default: false)
  --compact-weights     use memcpy() to load weights in order to save code space
  --mexpress            use express kernel loading (default: true)
  --no-mexpress         disable express kernel loading
  --mlator              use hardware to swap output bytes (default: false)
  --unroll-mlator N     number of assignments per loop iteration for mlator output (default: 8)
  --unroll-8bit N       number of assignments per loop iteration for 8-bit output (default: 1)
  --unroll-wide N       number of assignments per loop iteration for wide output (default: 8)
  --softmax             add software softmax function (default: false)
  --unload              enable use of cnn_unload() function (default)
  --no-unload           disable use of cnn_unload() function (default: enabled)
  --no-kat              disable known-answer test generation (KAT) (default: enabled)
  --boost S             dot-separated port and pin that is turned on during CNN run to boost the power supply, e.g. --boost 2.5 (default: None)
  --start-layer N       set starting layer (default: 0)
  --no-wfi              do not use _WFI() (default: _WFI() is used)
  --timer N             use timer to time the inference (default: off, supply timer number)
  --no-timer            ignore --timer argument(s)
  --energy              insert instrumentation code for energy measurement
  --switch-delay N      set delay in msec after cnn_enable() for load switches (default: 0 on MAX78000, 10 on MAX78002)
  --output-width {8,32}
                        override `output_width` for the final layer (default: use YAML)
  --no-deduplicate-weights
                        do not reuse weights (default: enabled)
  --no-warn-zero        do not warn about all-zero data (default: warn)

File names:
  --c-filename S        C file name base (RTL sim default: 'test' -> 'test.c', otherwise 'main' -> 'main.c')
  --api-filename S      C library file name (default: 'cnn.c', 'none' to disable)
  --weight-filename S   weight header file name (default: 'weights.h')
  --sample-filename S   sample data header file name (default: 'sampledata.h')
  --sample-input S      sample data input file name (default: 'tests/sample_dataset.npy')
  --sample-output-filename S
                        sample result header file name (default: 'sampleoutput.h', use 'None' to inline code)
  --sample-numpy-filename S
                        save sample result as NumPy file (default: disabled)

Streaming and FIFOs:
  --fifo                use FIFOs to load streaming data (default: false)
  --fast-fifo           use fast FIFO to load streaming data (implies --fifo; default: false)
  --fast-fifo-quad      use fast FIFO in quad fanout mode (implies --fast-fifo; default: false)
  --no-fifo-wait        do not check the FIFO for available space (requires matching source speed to inference, default: false)
  --fifo-go             start processing before first FIFO push (default: false)
  --slow-load N         slow down FIFO loads (default: 0)
  --debug-new-streaming
                        modify streaming equation (default: false)

RISC-V:
  --riscv               use RISC-V processor (default: false)
  --riscv-flash         move kernel/input to Flash (implies --riscv; default: true)
  --no-riscv-flash      disable --riscv-flash
  --riscv-cache         enable RISC-V cache (implies --riscv and --riscv-flash; default: true)
  --no-riscv-cache      disable RISC-V cache
  --riscv-debug         enable RISC-V debug interface (implies --riscv; default: false)
  --riscv-exclusive     exclusive SRAM access for RISC-V (implies --riscv; default: false)

Debug and logging:
  -v, --verbose         verbose output (default: false)
  -L, --log             redirect stdout to log file (default)
  --no-log              do not redirect stdout to log file (default: false)
  --no-progress         do not display progress bars (default: show)
  --log-intermediate    log weights/data between layers to .mem files (default: false)
  --log-pooling         log unpooled and pooled data between layers in CSV format (default: false)
  --short-log, --log-last-only, --verbose-all
                        log data for output layers only (default: all layers)
  --log-filename S      log file name (default: 'log.txt')
  -D, --debug           debug mode (default: false)
  --debug-computation   debug computation -- SLOW (default: false)
  --debug-latency       debug latency calculations (default: false)
  --no-error-stop       do not stop on errors (default: stop)
  --stop-after N        stop after layer
  --skip-checkpoint-layers N
                        ignore first N layers in the checkpoint (default: 0)
  --skip-yaml-layers N  ignore first N layers in the yaml file (default: 0)
  --stop-start          stop and then restart the accelerator (default: false)
  --one-shot            use layer-by-layer one-shot mechanism (default: false)
  --repeat-layers N     repeat layers N times (default: once)
  --clock-trim LIST     comma-separated hexadecimal clock trim for IBRO,ISO,IPO; use0 to ignore a particular trim
  --fixed-input         use fixed 0xaa/0x55 alternating input (default: false)
  --reshape-inputs      drop data channel dimensions to match weights (default: false)
  --forever             after initial run, repeat CNN forever (default: false)
  --link-layer          always use the link layer feature (default: false)
  --read-ahead          set the rd_ahead bit (default: false)
  --calcx4              rearrange kernels and set the calcx4 bit (default: false)
  --ext-rdy             set ext_rdy bit (default: false)
  --weight-start N      specify start offset for weights (debug, default: 0)
  --ignore-bias-groups  do not force `bias_group` to use an active group (default: false)
  --kernel-format S     print format for kernels (default: '{0:4}')
  --debug-snoop         insert snoop register debug code (default: False)
  --snoop-loop          insert snoop loop (default: false)
  --ignore-hw-limits    ignore certain hardware limits (default: false)
  --ignore-bn           ignore BatchNorm weights in checkpoint file (default: false)
  --ignore-activation   ignore activations in YAML file (default: false)
  --ignore-energy-warning
                        do not show energy and performance hints (default: show)
  --ignore-mlator-warning
                        do not show mlator hints (default: show)
  --new-kernel-loader   use new kernel loader (default)
  --old-kernel-loader   use alternate old kernel loader
  --weight-input S      weight input file name (development only, default: 'tests/weight_test_dataset.npy')
  --bias-input S        bias input file name (development only, default: 'tests/bias_dataset.npy')

RTL simulation:
  --input-csv S         input data .csv file name for camera sim
  --input-csv-format N  format for .csv input data (555, 565, 888, default: 888)
  --input-csv-retrace N
                        delay for camera retrace when using .csv input data (default: 5)
  --input-csv-period N  period for .csv input data (default: 80)
  --input-pix-clk N     pixel clock for .csv input data (default: 9)
  --input-sync          use synchronous camera input (default: false)
  --input-fifo          use software FIFO to buffer input (default: false)
  --autogen S           directory location for autogen_list (default: None)
  --autogen_list S      file name for autogen_list
  --input-filename S    input .mem file name base (default: 'input' -> 'input.mem')
  --output-filename S   output .mem or .csv file name base (default: 'output' -> 'output-X.mem' or 'output.csv')
  --output-config-filename S
                        output config file name base (default: 'config' -> 'config.csv')
  --output-data-filename S
                        output data file name base (default: 'data' -> 'data.npy')
  --output-weights-filename S
                        output weights file name base (default: 'weights' -> 'weights.npy')
  --output-bias-filename S
                        output bias file name base (default: 'bias' -> 'bias.npy')
  --output-pass-filename S
                        output pass data file name base (default: None)
  --runtest-filename S  run test file name (default: 'run_test.sv')
  --legacy-test         enable compatibility for certain old RTL sims (default: false)
  --legacy-kernels      use old, less efficient kernel allocation for certain old RTL sims (default: false)
  --test-bist           test BIST by clearing every seventh kernel (default: false)
  --test-dir S          set base directory name for auto-filing .mem files
  --top-level S         top level name (default: 'cnn', 'None' for block level)
  --queue-name S        queue name (default: 'short')
  --timeout N           set RTL sim timeout (units of 1ms, default based on test)
  --result-output       write expected output to memory dumps instead of inline code (default: false)

Streaming tweaks:
  --overlap-data        allow output to overwrite input (default: warn/stop)
  --override-start N    override auto-computed streaming start value (x8 hex)
  --increase-start N    add integer to streaming start value (default: 2)
  --override-rollover N
                        override auto-computed streaming rollover value (x8 hex)
  --override-delta1 N   override auto-computed streaming delta1 value (x8 hex)
  --increase-delta1 N   add integer to streaming delta1 value (default: 0)
  --override-delta2 N   override auto-computed streaming delta2 value (x8 hex)
  --increase-delta2 N   add integer to streaming delta2 value (default: 0)
  --ignore-streaming    ignore all 'streaming' layer directives (default: false)
  --allow-streaming     allow streaming without use of a FIFO (default: false)
  --no-bias [[LIST]]    comma-separated list of layers where bias values will be ignored, or no argument for all layers (default: None)
  --streaming-layers LIST
                        comma-separated list of additional streaming layers (default: None)

Power saving:
  --powerdown           power down unused MRAM instances (default: false)
  --deepsleep           put ARM core into deep sleep (default: false)

Hardware settings:
  --max-proc N          override maximum number of processors
  --input-offset N      input offset (x8 hex, defaults to 0x0000)
  --verify-writes       verify write operations (toplevel only, default: false)
  --verify-kernels      verify kernels (toplevel only, default: false)
  --mlator-noverify     do not check both mlator and non-mlator output (default: false)
  --write-zero-registers
                        write registers even if the value is zero (default: do not write)
  --init-tram           initialize TRAM to 0 (default: false)
  --zero-sram           zero memories (default: false)
  --pretend-zero-sram   simulate --zero-sram, but block BIST (default: false)
  --zero-unused         zero unused registers (default: do not touch)
  --apb-base N          APB base address (default: device specific)
  --ready-sel N         specify memory waitstates
  --ready-sel-fifo N    specify FIFO waitstates
  --ready-sel-aon N     specify AON waitstates

Various:
  --input-split N       split input into N portions (default: don't split)
  --synthesize-input N  synthesize input data from first `--synthesize-words` words and add N to each subsequent set of `--synthesize-words` 32-bit words (default: false)
  --synthesize-words N  number of input words to use (default all or 8)
  --max-verify-length N, --max-checklines N
                        output only N output check lines (default: all)
  --no-version-check    do not check GitHub for newer versions of the repository
  --version-check-interval HOURS
                        version check update interval (hours), default = 24
  --upstream REPO       GitHub repository name for update checking
  --yamllint S          name of linter for YAML files (default: yamllint)

```

## run


Run  ai8xize.py  with the new network and the new sample data to generate embedded C code that can be 
compiled with the Arm and RISC-V compiler


generate demo in the  demos/ai85-mnist/
mkdir ../test1/demo

```
(ai8x-synthesize) $ python ai8xize.py --verbose --test-dir ../test1/demo --prefix ai85-cifar --checkpoint-file ../test1/best-q.pth.tar --config-file ../test1/cifar10-nas.yaml  --sample-input ../test1/sample_cifar10.npy --device MAX78000 --compact-data --softmax

Configuring device: MAX78000
Reading ../test1/cifar10-nas.yaml to configure network...
Reading ../test1/best-q.pth.tar to configure network weights...
Configuring data set: CIFAR10.
ai85-cifar...
Arranging weights... ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 100%
Storing weights...   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 100%
Creating network...  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 100%


```

```
../test1/demo
└── [4.0K]  ai85-cifar
    ├── [5.5K]  ai85-cifar.launch
    ├── [ 46K]  cnn.c
    ├── [3.6K]  cnn.h
    ├── [6.2M]  log.txt
    ├── [6.0K]  main.c
    ├── [ 15K]  Makefile
    ├── [ 383]  project.mk
    ├── [ 13K]  sampledata.h
    ├── [ 322]  sampleoutput.h
    ├── [4.1K]  softmax.c
    └── [938K]  weights.h

```


## PAPI How-To

### Machine Specs:
* Processor: 13th Gen Intel(R) Core(TM) i5-13400 (191, 0xbf)
    * RaptorLake family
* Linux Kernel: Linux 6.14.0-33-generic
* PAPI version installed: 7.2.1.0

### Setup Links:
* Installation How-To - https://github.com/icl-utk-edu/papi/wiki/Downloading-and-Installing-PAPI
* Before running PAPI with code:
``` 
#!bash
export PAPI_DIR=<you location where PAPI is installed>
i.e., export PAPI_DIR=$HOME/papi/src/install
export PATH=$PAPI_DIR/bin:$PATH
export LD_LIBRARY_PATH=$PAPI_DIR/lib:$LD_LIBRARY_PATH
```
* PAPI flags - for compilation
```
PAPI_INC = -I${PAPI_DIR}/include
PAPI_LIB = -L${PAPI_DIR}/lib -lpapi
```
#### PAPI preset events not defined for RaptorLake, use native events
Fix: https://github.com/icl-utk-edu/papi/issues/378

#### To view presets/native events exposed by PAPI

**Look at scripts at:**\
`~/papi/src/install/bin`\
**To view the presets:** \
`./papi_avail`\
**To view PAPI components that expose these events:**\
 `./papi_component_avail`\
**To view possible native events:**\
 `./papi_native_avail`\
**To check if native event present for current microarchitecture:**\
 `./papi_command_line <nativePerfEvent>`
> Example: `./papi_command_line perf::PERF_COUNT_HW_CACHE_L1D:MISS`

#### What a pain, not hurt yet
> https://web.eece.maine.edu/~vweaver/projects/perf_events/abi_breakage.html

#### L2.RQSTS
http://www.nacad.ufrj.br/online/intel/vtune/users_guide/mergedProjects/analyzer_ec/mergedProjects/reference_olh/mergedProjects/pmn/events/l2_rqsts.html

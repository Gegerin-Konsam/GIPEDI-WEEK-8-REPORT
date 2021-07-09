# GIPEDI-WEEK-8-Report
### Submitted by Gegerin Konsam
### ID FENGS173
- -----------------
### Syntax errors 
I tried writing different logics  to verify C algorithm before synthesis because the last time i ran an exponent code with full synthesise, the behavioural simulation terminated with a lot of errors. 

Later on I read through a book called "HLS BLUE BOOK" and found the following:
- in order to perform High Level Synthesis, specific header files with synthesizeable data types are required.
- The last exponent program did not work because the input data type was not synthesizeable.
- Tried using Matchlib.h libraries but could not run C simulation due to unknown argument errors { still troubleshooting}.

# Errors from Performance Estimates

#### Latency (clock cycles): 
    * Summary: 
    +-----+-----+-----+-----+---------+
    |  Latency  |  Interval | Pipeline|
    | min | max | min | max |   Type  |
    +-----+-----+-----+-----+---------+
    |   41|   41|   41|   41|   none  |
    +-----+-----+-----+-----+---------+

The minimum and maximum latency should be different since we would have some part of code taking more execution time than others.
hence, the obtained result is not realistic and is due to errors in the input data type and use of headerfiles.

# Interface

    * Summary: 
          +-----------+-----+-----+------------+--------------+--------------+
          | RTL Ports | Dir | Bits|  Protocol  | Source Object|    C Type    |
          +-----------+-----+-----+------------+--------------+--------------+
          |ap_clk     |  in |    1| ap_ctrl_hs |   cpp_math   | return value |
          |ap_rst     |  in |    1| ap_ctrl_hs |   cpp_math   | return value |
          |ap_start   |  in |    1| ap_ctrl_hs |   cpp_math   | return value |
          |ap_done    | out |    1| ap_ctrl_hs |   cpp_math   | return value |
          |ap_idle    | out |    1| ap_ctrl_hs |   cpp_math   | return value |
          |ap_ready   | out |    1| ap_ctrl_hs |   cpp_math   | return value |
          |ap_return  | out |   32| ap_ctrl_hs |   cpp_math   | return value |
          |x          |  in |   32|   ap_none  |       x      |    scalar    |
          +-----------+-----+-----+------------+--------------+--------------+

We can see here that the protocol for x (which is the input to the exponent module) has been taged "ap_none" this is due to a wrong data type used. the data type used was not synthesizeable. This led to the simulation errors although the program was verified at C level, it did not have any connetions with its actual hardware counterpart required for synthesis. 

# Task left

* rectify and find how to use ac_int<> (this header file should be used to define data types for synthesis)
* complete behaviorual simulation of exponential function using the ap and ac datatypes.
* compute tanh using 3 different libraries and compare the resource utilizations 
* successfully verify C algorithm and the RTL verification for final report. 

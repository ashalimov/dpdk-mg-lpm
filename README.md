# dpdk-mg-lpm
LPM implementation using multi-group classifiers.

# Build prerequirements

* Download and Install Intel DPDK version at least 2.0.1: 
```
$ wget http://fast.dpdk.org/rel/dpdk-2.1.0.tar.xz
$ sudo ./dpdk-2.1.0/tools/setup.sh
```

# Test cases description

Function setup_mg_lpm() constain all testing code snippets to reproduce experiments for LPM v4 and v6 cases.

Experiment lifecycle:

* Choose how many ipv4 or ipv6 groups lookup you want to do time measuring. Possible values are 20 groups for IPv4 case and 8 groups for IPv6 case. The prefix lenghts are stored in variables *DEPTH_TEST*.
* Go to setup_mg_lpm() and **comment** not needed code for your experiments: creating LPM group data structures, populating them with predefined FIBs, calling looks up, measure tsc cycles, and printing results.
* Compile using *make* util. _NOTE_: DPDK must be already setup up.
* Run *build/ipv6fib* binary.
* The binary stops immediatly after test code execution. The results are in the terminal: tsc and time to do pseudo-parallel lookup.

**Hint**: if you want to measure a baseline such as the number of cycles to do single LPM lookup with long prefix = 40 bits, just choose the group number = 1, and *set DEPTH_TEST = 40*.


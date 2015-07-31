# Container for Socketpref

SockPerf is a network testing tool oriented to measure network latency and also spikes of network latency.

	$ sockperf server -i 224.18.7.81 -p 5001

Then

	$ sockperf ping-pong -i 224.18.7.81 -p 5001 -m 16384 -t 10 --pps=max
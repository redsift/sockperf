# Container for Socketperf

[![Docker Repository on Quay.io](https://quay.io/repository/redsift/sockperf/status "Docker Repository on Quay.io")](https://quay.io/repository/redsift/sockperf)

	docker run -ti --rm quay.io/redsift/sockperf --help


SockPerf is a network testing tool oriented to measure network latency and also spikes of network latency.

# UDP tests

	$ docker run -ti --rm quay.io/redsift/sockperf server -i 224.18.7.81 -p 5001

Then

	$ docker run -ti --rm quay.io/redsift/sockperf ping-pong -i 224.18.7.81 -p 5001 -m 16384 -t 10 --pps=max
	
	
# Routing for Multicast

	ip route add 224.0.0.0/4 dev <private eth device>
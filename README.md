# Container for Socketperf

[![Docker Repository on Quay.io](https://quay.io/repository/redsift/sockperf/status "Docker Repository on Quay.io")](https://quay.io/repository/redsift/sockperf)

	docker run -ti --rm quay.io/redsift/sockperf --help


SockPerf is a network testing tool oriented to measure network latency and also spikes of network latency.

# Multicast UDP tests

	$ docker run -ti --rm --net=host quay.io/redsift/sockperf server -i 224.18.7.81 -p 5001

Then

	$ docker run -ti --rm --net=host quay.io/redsift/sockperf ping-pong -i 224.18.7.81 -p 5001 -m 16384 -t 10 --pps=max
	
Note the use of host networking, this is due to limitations with docker not being setup with multicast. A few workarounds exist on [this thread](https://github.com/docker/docker/issues/3043).

# Errors

	sockperf: No messages were received from the server. Is the server down?
	
# Routing for Multicast

Check your device of choice is routing multicast addresses.

	ip route add 224.0.0.0/4 dev <private eth device>
	
You should then see it listed via

	ip route
	
You will need to make this persistent on your distro e.g. an entry in `/etc/sysconfig/network-scripts/route-eth0`.
	
# iptables/firewalld

Ensure you are not blocking this traffic
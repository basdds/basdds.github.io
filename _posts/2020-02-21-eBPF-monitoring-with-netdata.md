---
layout: post
author: Bas
---
Today a new 'Netdata' version was released; version 1.20. [(release notes here)](https://blog.netdata.cloud/posts/release-1.20/){:target="_blank"}

As stated before, I use Netdata for monitoring the performance of my (private) VPS server(s) 

One of the most exiting new features in this new release is support for 'Linux eBPF monitoring'.

With [eBPF](https://lwn.net/Articles/740157/){:target="_blank"} you can monitor a lot of kernel functions in real time. 
Useful for debugging applications running on your linux machines.

I won't be able to test it just now (LTS kernel < required on my VPS now) but this might come in handy someday! 

Do not miss this note in the docs though: "Because it adds overhead to the system running it, the collector is also 
disabled by default"... 
 

A few links:

[The netdata blog post on eBPF](https://blog.netdata.cloud/posts/linux-ebpf-monitoring-netdata/){:target="_blank"} 

[The ebpf_process.plugin documentation](https://docs.netdata.cloud/collectors/ebpf_process.plugin/){:target="_blank"}

[Learn eBPF tracing](http://www.brendangregg.com/blog/2019-01-01/learn-ebpf-tracing.html){:target="_blank"}
 

p.s. "Haven't posted here in a month now, and again about netdata??" .... Yes I know! :-) 

In Kubernetes, HPA waits for at least 10% change in CPU/memory usage before adding or removing pods.

You cant control how sensitive it was to increase or decrease in usage.

For example,

If you set 70% as the usage target, Kubernetes would only scale up if it went above 77%, and scale down if it went below 63%.

Here is the problem with with fixed 10%?

Sometimes you want the system to react quickly when traffic spikes. Other times, you want it to be more cautious to avoid constant scaling up and down.

Now in Kubernetes v1.33, you can set separate tolerance levels for scaling up and scaling down.

HPA Tolerance Levels (alpha feature)
Note: Alpha APIs can change dramatically or be removed entirely between versions. It has minimal real-world testing and may have bugs that could impact your workloads.

To test this feature, you need to enable the HPAConfigurableTolerance feature gate in the cluster. Refer this guide to know more.

HPA Tolerance Levels is a new alpha feature in Kubernetes v1.33 that allows you to customize how sensitive your Horizontal Pod Autoscaler (HPA) is to metric changes

This means you can make HPA respond faster when traffic increases (scale up quickly) and wait longer when traffic slows down (avoid scaling down too fast).

Here is an example.
<img width="346" height="400" alt="image" src="https://github.com/user-attachments/assets/fcc404fb-dc88-4a52-8cc7-e88a76913351" />


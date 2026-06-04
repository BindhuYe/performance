With Horizontal Pod Autoscaler (HPA), a powerful controller that automatically adjusts the number of pod replicas in your Deployment based on real-time metrics like CPU or memory usage.

Here’s how the magic happens behind the scenes:
🔹 cAdvisor (Container Advisor)
 Runs on every node as part of the kubelet, collecting fine-grained resource usage (like CPU, memory) for each container.
🔹 metrics-server
 Aggregates metrics from all nodes (via cAdvisor) and exposes them to the Kubernetes API, enabling real-time decisions.
🔹 HPA Controller
 Watches the metrics and desired threshold (say, 70% CPU). If usage crosses the limit, it automatically tells the Deployment to scale up pods. If usage drops, it scales down.
🔹 Deployment
 Responds to the HPA’s instructions by adjusting the number of replicas, ensuring your app stays performant and cost-efficient.

✅ The result?
 Efficient scaling; up during peak traffic, down when idle. No manual intervention required.

You can scale not just on CPU/memory, but also on custom metrics or external metrics like request rate, latency, etc.

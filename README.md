```ansi
          [90m┌───────────[0m[95m[1m on-device tensor arena [0m[90m────────────┐[0m
  [96m0x0000[0m  [90m│ [0m[92m[1m▓ [0m[97membedded roots          since 2018          [0m[90m│[0m
  [96m0x0400[0m  [90m│ [0m[96m[1m▓ [0m[97mxv6 slab allocator      systems             [0m[90m│[0m
  [96m0x1000[0m  [90m│ [0m[95m[1m▓ [0m[97mlitert internal split   heterogeneous       [0m[90m│[0m
  [96m0x2000[0m  [90m│ [0m[93m[1m▓ [0m[97mopenvla projector       on-device ML        [0m[90m│[0m
  [96m0x3000[0m  [90m│ [0m[92m[1m▓ [0m[97mros2 manipulation       embodied            [0m[90m│[0m
          [90m└───────[0m[97m[1m single shared arena · zero-copy [0m[90m───────┘[0m
            [95m▲[0m [90mboundary tensor = [0m[1mme[0m
```

### `~/research/focus`

- **Memory-efficient runtime systems** — kernel-level allocation ideas (slab / paging) ported into on-device inference engines
- **Heterogeneous execution** — automatic CPU/GPU subgraph partitioning and zero-copy tensor flow in LiteRT / TFLite
- **On-device model optimization** — token compression and projector redesign for VLA models

---

### `~/projects`

**TFLite Internal Split** — *single-interpreter CPU/GPU partitioning*
Partitions a model into CPU/GPU subgraphs inside one interpreter via `first_delegate_node_index = k`, with an offline sweep for the latency-optimal cut. Boundary tensors share a single arena — no manual `memcpy`.
→ https://github.com/kchsugo/tflite_research

**OpenVLA Projector Optimization** — *on-device VLA efficiency*
Visual tokens 256 → 64 (~21% latency cut) and isolated the real cause of training collapse: **LayerNorm, not spatial mixing**. Multi-scale projector raises spatial info reaching the LLM (+31–34%, p < 0.02).
→ https://github.com/kchsugo/openvla-projector-study

**xv6 Custom Slab Allocator** — *kernel memory management*
Logical-chaining + fine-grained slab allocation to break the single-page limit — an intuition parallel to vLLM's PagedAttention.

**ROS2 Manipulation Pipeline** — *embodied execution*
pick–scan–place on a Doosan M0609 6-DOF arm with hand-eye calibration and closed-loop YOLO re-detection.

---

### `/proc/stack`

`C` · `C++` · `Python` · `CUDA` &nbsp;|&nbsp; Linux kernel (xv6) · slab / page allocation &nbsp;|&nbsp; LiteRT (TFLite) · token compression &nbsp;|&nbsp; ROS2 · MoveIt2 · hand-eye calibration


### `~/education`

- **Soongsil University** — B.S. in AI Convergence &nbsp;·&nbsp; *2021 – 2027*
- **Korea Digital Media High School** — IT-specialized track &nbsp;·&nbsp; *2018 – 2020*


### `contact`

[chanchan@soongsil.ac.kr](mailto:chanchan@soongsil.ac.kr) &nbsp;·&nbsp; School of AI Convergence, Soongsil University

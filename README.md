# Chanhyung Kim &nbsp;·&nbsp; 김찬형

**System-native Researcher for On-device AI** — *bridging the gap between the OS kernel and AI inference.*

School of AI Convergence, Soongsil University

```
        CPU partition                        GPU partition
     nodes 0..k-1 · systems             nodes k.. · ML / accel
   ┌───┐┌─────┐┌─────┐┌───────┐   ╎   ┌──────┐┌────────┐┌─────────┐
   │ C ││ C++ ││ xv6 ││ Linux │   ╎   │ CUDA ││ LiteRT ││ OpenVLA │
   └───┘└─────┘└─────┘└───────┘   ╎   └──────┘└────────┘└─────────┘
                                  k
        boundary tensor (shared)  ──►  Python glue · single arena
```

I make AI inference efficient on resource-constrained devices by porting OS-kernel-level
memory management into inference runtimes — the full on-device stack, from model internals
to action execution on real robot platforms.

---

### CPU side · systems

**xv6 Custom Slab Allocator** — *kernel memory management*
Logical-chaining + fine-grained slab allocation to break the single-page limit — an intuition parallel to vLLM's PagedAttention.

**TFLite Internal Split** — *single-interpreter CPU/GPU partitioning*
Partitions a model into CPU/GPU subgraphs inside one interpreter via `first_delegate_node_index = k`, with an offline sweep for the latency-optimal cut. Boundary tensors share a single arena — no manual `memcpy`.
→ https://github.com/kchsugo/tflite_research

### GPU side · ML / accel

**OpenVLA Projector Optimization** — *on-device VLA efficiency*
Visual tokens 256 → 64 (~21% latency cut) and isolated the real cause of training collapse: **LayerNorm, not spatial mixing**. Multi-scale projector raises spatial info reaching the LLM (+31–34%, p < 0.02).
→ https://github.com/kchsugo/openvla-projector-study

**ROS2 Manipulation Pipeline** — *embodied execution*
pick–scan–place on a Doosan M0609 6-DOF arm with hand-eye calibration and closed-loop YOLO re-detection.

---

### Stack

| | |
|---|---|
| **Languages** | C · C++ · Python · CUDA |
| **Systems** | Linux kernel (xv6) · slab / page allocation · memory profiling |
| **On-device ML** | LiteRT (TFLite) · token compression · memory-efficient inference |
| **Robotics** | ROS2 · MoveIt2 · manipulator control · hand-eye calibration |

### Education

- **Soongsil University** — B.S. in AI Convergence &nbsp;·&nbsp; *2021 – 2027*
- **Korea Digital Media High School** — IT-specialized track &nbsp;·&nbsp; *2018 – 2020*

### Contact

[chanchan@soongsil.ac.kr](mailto:chanchan@soongsil.ac.kr)

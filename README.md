<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=7C3AED&height=190&section=header&text=Chanhyung%20Kim&fontSize=52&fontColor=ffffff&fontAlignY=38&desc=System-native%20Researcher%20for%20On-device%20AI&descSize=18&descAlignY=60" width="100%"/>

*Bridging the gap between the OS kernel and AI inference.*

<br/>

[![Soongsil University](https://img.shields.io/badge/Soongsil%20University-School%20of%20AI%20Convergence-7C3AED?style=flat-square&logo=googlescholar&logoColor=white)](https://ssu.ac.kr)
[![Email](https://img.shields.io/badge/chanchan@soongsil.ac.kr-7C3AED?style=flat-square&logo=gmail&logoColor=white)](mailto:chanchan@soongsil.ac.kr)

</div>

---

I make AI inference efficient on resource-constrained devices by porting OS-kernel-level
memory management into inference runtimes. My work spans the full on-device stack —
from model-internal optimization to action execution on real robot platforms.

### 🔭 Research Focus

- **Memory-efficient runtime systems** — kernel-level allocation ideas (slab / paging) ported into on-device inference engines
- **Heterogeneous execution** — automatic CPU/GPU subgraph partitioning and zero-copy tensor flow in LiteRT / TFLite
- **On-device model optimization** — token compression and projector redesign for VLA models

---

### 🧩 Selected Work

**`TFLite Internal Split`** — *single-interpreter CPU/GPU partitioning*
> Partitions a model into CPU/GPU subgraphs inside **one** interpreter via `first_delegate_node_index = k`,
> with an offline sweep that locks in the latency-optimal cut. Boundary tensors share a single arena —
> no manual `memcpy` / zero-copy code needed.
>
> → https://github.com/kchsugo/tflite_research

**`OpenVLA Projector Optimization`** — *on-device VLA efficiency*
> Compressed visual tokens 256 → 64 (~21% latency cut, 331 → 260 ms) and isolated the real driver of
> training collapse: **normalization (LayerNorm), not spatial mixing**. Designed a multi-scale projector
> that significantly increases spatial information reaching the LLM (+31–34%, p < 0.02).
>
> → https://github.com/kchsugo/openvla-projector-study

**`xv6 Custom Slab Allocator`** — *kernel memory management*
> Logical-chaining + fine-grained slab allocation to break the single-page limit and minimize
> fragmentation — an intuition parallel to vLLM's PagedAttention.

**`ROS2 Manipulation Pipeline`** — *embodied execution*
> pick–scan–place on a Doosan M0609 6-DOF arm with hand-eye calibration and closed-loop
> YOLO re-detection for runtime coordinate correction.

---

### 🛠 Stack

<div align="center">

![C](https://img.shields.io/badge/C-7C3AED?style=flat-square&logo=c&logoColor=white)
![C++](https://img.shields.io/badge/C++-7C3AED?style=flat-square&logo=cplusplus&logoColor=white)
![Python](https://img.shields.io/badge/Python-7C3AED?style=flat-square&logo=python&logoColor=white)
![CUDA](https://img.shields.io/badge/CUDA-7C3AED?style=flat-square&logo=nvidia&logoColor=white)

![Linux Kernel](https://img.shields.io/badge/Linux%20Kernel%20(xv6)-9333EA?style=flat-square&logo=linux&logoColor=white)
![LiteRT](https://img.shields.io/badge/LiteRT%20/%20TFLite-9333EA?style=flat-square&logo=tensorflow&logoColor=white)
![ROS2](https://img.shields.io/badge/ROS2-9333EA?style=flat-square&logo=ros&logoColor=white)

</div>

| | |
|---|---|
| **Systems** | Linux kernel (xv6) · slab / page allocation · memory profiling |
| **On-device ML** | LiteRT (TFLite) · token compression · memory-efficient inference |
| **Robotics** | ROS2 · MoveIt2 · manipulator control · hand-eye calibration |

---

### 📌 Currently

- Extending single-interpreter CPU/GPU partitioning toward arbitrary node sets with a custom delegate
- Reading toward memory-efficient runtime systems for on-device LLM inference

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=kchsugo&show_icons=true&hide_border=true&title_color=7C3AED&icon_color=9333EA&text_color=555555&hide=contribs&hide_title=true" height="150"/>

</div>

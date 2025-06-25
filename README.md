# 🧠 MoE Spherical Partitions Visualizer

An interactive visualization tool for exploring the geometric structure of **Mixture of Experts (MoE)** networks on the 2-sphere **S²**.

[![Live Demo](https://img.shields.io/badge/🚀-Live%20Demo-blue)](https://antonioalvarezl.github.io/2025-MOE-LinearRoutingVisualizer/)
![Demo Screenshot](assets/demo.png)

## 🎯 What is this?

This tool visualizes the **spherical partitions** created by **(m,k)-MoE layers** - a fundamental component in modern neural architectures. Each point on the sphere S² represents a direction in 3D space, and the visualization shows:

- **🔴 Routing Regions**: Areas where the same **k experts** are active
- **🎨 MLP Sub-cells**: Fine partitions within routing regions based on ReLU activations  
- **⚫ Boundaries**: Thick lines separating different regions
- **◆ Routing Vectors**: The r_i vectors that define the partition

## 🚀 Quick Start

### Option 1: Try Online
Visit the **[Live Demo](https://antonioalvarezl.github.io/2025-MOE-LinearRoutingVisualizer/)** - no installation required!

### Option 2: Run Locally
```bash
git clone https://github.com/antonioalvarezl/2025-MOE-LinearRoutingVisualizer.git
cd 2025-MOE-LinearRoutingVisualizer
# Open index.html in your browser
python -m http.server 8000  # Or any local server
```

## 📊 Mathematical Background

### (m,k)-MoE Definition
For **m experts** and **granularity k**, an MoE layer computes:

```
f(x) = Σᵢ Gᵢ(x) Eᵢ(x)
```

Where:
- **Eᵢ**: Expert networks (MLPs)
- **G(x)**: Gating function selecting top-k experts
- **‖G(x)‖₀ = k**: Exactly k experts active

### Spherical Partition Structure
The sphere S² is partitioned into **two levels**:

1. **Routing Cells**: Regions where the same k experts are active
   - Bounded by hyperplanes: ⟨rᵢ - rⱼ, x⟩ = 0
   - Maximum cells: **C(m,k)** (binomial coefficient)

2. **MLP Sub-cells**: Within each routing cell, ReLU activations create:
   - Sub-partitions based on sign(Aᵢx) patterns
   - Maximum sub-cells per routing cell: **2ᵖ** (p = MLP width)

**Total maximum cells: 2ᵖ × C(m,k)**

## 🎮 Interactive Features

### Parameters
- **m (Experts)**: Number of routing vectors (1-15)
- **k (Granularity)**: Active experts per region (0-m)  
- **p (MLP Neurons)**: Neurons per expert MLP (0-12)
- **Resolution**: Sampling density (60-400 points)

### Special Cases
- **k=0**: No experts active (degenerate case)
- **p=0**: Only routing partitions, no MLP sub-cells
- **Canonical Mode**: Uses orthogonal vectors e₁, e₂, e₃ (m=3)

### Controls
- **🎲 New Random Config**: Generate fresh random partition
- **📊 Interesting Presets**: Load curated examples
- **🎯 Canonical Example**: Perfect orthogonal case
- **💾 Export Config**: Save as JSON for reproducibility
- **🔲 Toggle Boundaries**: Show/hide region boundaries

## 📁 Repository Structure

```
├── 📄 README.md                 # This file
├── 🌐 index.html               # Main visualization
├── 📚 docs/                    # Documentation
│   ├── theory.md               # Mathematical theory
│   ├── usage.md                # User guide
│   └── examples.md             # Example gallery
├── 📦 examples/                # Preset configurations
│   ├── canonical_3_2_3.json   # Canonical example
│   ├── voronoi_5_1_4.json     # Voronoi-like partition
│   ├── degenerate_k0.json     # k=0 case
│   └── routing_only_p0.json   # p=0 case
├── 🖼️ assets/                  # Screenshots & media
│   └── screenshots/
└── 📜 LICENSE                  # MIT License
```

## 🎨 Example Configurations

### 1. Canonical Orthogonal (m=3, k=2, p=3)
Perfect symmetry with e₁, e₂, e₃ vectors.
```bash
# Load: examples/canonical_3_2_3.json
```

### 2. Voronoi-like Partition (m=5, k=1, p=4)  
Each region has exactly one active expert.
```bash
# Load: examples/voronoi_5_1_4.json
```

### 3. Routing-Only Mode (m=6, k=2, p=0)
Pure routing partitions without MLP sub-cells.
```bash
# Load: examples/routing_only_p0.json
```

### 4. Degenerate Case (m=4, k=0, p=3)
No experts active anywhere.
```bash
# Load: examples/degenerate_k0.json
```

## 🔬 Research Applications

### Academic Use Cases
- **📖 Education**: Visualize MoE geometry for students
- **🔬 Research**: Validate theoretical predictions
- **📊 Analysis**: Study partition efficiency and complexity
- **🎯 Design**: Optimize MoE architectures

### Theoretical Insights
- **Partition Efficiency**: How many of the theoretical maximum cells are realized?
- **Boundary Structure**: Understand the geometric complexity
- **Scaling Laws**: How does complexity grow with m, k, p?
- **Canonical vs Random**: Compare structured vs random routing

## 🛠️ Technical Details

### Browser Compatibility
- **Chrome/Edge**: ✅ Full support
- **Firefox**: ✅ Full support  
- **Safari**: ✅ Full support
- **Mobile**: ✅ Touch controls

### Performance
- **Ultra resolution (400)**: Best quality, slower rendering
- **High resolution (150)**: Good balance (recommended)
- **Fast resolution (60)**: Real-time interaction

### Dependencies
- **Plotly.js**: 3D visualization engine
- **Pure HTML/CSS/JS**: No build system required

## 📚 Documentation

### Quick Links
- **[📖 Mathematical Theory](docs/theory.md)**: Deep dive into MoE geometry
- **[🎮 Usage Guide](docs/usage.md)**: Complete user manual
- **[🖼️ Example Gallery](docs/examples.md)**: Curated configurations
- **[🔗 API Reference](docs/api.md)**: Export format & integration

### Key Concepts
1. **Routing Cells**: Top-k expert selection creates polyhedral cones
2. **MLP Cells**: ReLU activations subdivide routing regions  
3. **Spherical Geometry**: Great circle intersections on S²
4. **Combinatorial Bounds**: Theoretical limits vs realized complexity

## 🤝 Contributing

We welcome contributions! Here's how to help:

### 🐛 Bug Reports
Found an issue? Please include:
- Browser and version
- Parameter configuration
- Expected vs actual behavior
- Screenshots if applicable

### ✨ Feature Requests
Ideas for improvements:
- Additional visualization modes
- Export formats (STL, OBJ, SVG)
- Animation capabilities
- Batch analysis tools

## 📜 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Mathematical Foundation**: Based on MoE partition theory
- **Visualization**: Powered by Plotly.js
- **Inspiration**: Modern neural architecture research
- **Community**: Feedback from researchers and educators

## 🔮 Future Plans

### Short Term
- [ ] **Animation Mode**: Show partition evolution
- [ ] **Comparison View**: Side-by-side configurations
- [ ] **Performance Metrics**: Quantitative analysis tools
- [ ] **Mobile Optimization**: Enhanced touch controls

### Long Term  
- [ ] **3D Export**: STL files for 3D printing
- [ ] **ML Integration**: TensorFlow/PyTorch connectivity
- [ ] **Batch Analysis**: Process multiple configurations
- [ ] **Educational Modules**: Guided tutorials

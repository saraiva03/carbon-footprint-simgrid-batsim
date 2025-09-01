# Carbon Footprint Plugin for SimGrid

This repository contains documentation and tutorials on how to use the **Carbon Footprint Plugin** in Batsim, a plugin developed to simulate and monitor CO₂ emissions associated with energy consumption of computational hosts in distributed systems.

The functional plugin code is available at: https://github.com/saraiva03/simgrid/tree/carbon-footprint-calc. The `host_carbon_footprint.cpp` file here is for reference/illustration only.

## 🚀 Installation and Configuration

### 1. Download SimGrid
```bash
# Clone the SimGrid fork with carbon footprint modifications
git clone https://github.com/saraiva03/simgrid/tree/carbon-footprint-calc
cd simgrid
```

### 2. Download Batsim
```bash
# Clone the Batsim fork with carbon footprint modifications
git clone https://github.com/saraiva03/batsim/tree/carbon-footprint-calc
cd batsim
```

**Compilation**: Build instructions are available in the official documentation of SimGrid and Batsim simulators.

## 🧪 Running Simulations

### In Batsim
```bash
# Start Batsim
batsim -p platforms/platform.xml -w workloads/workload.json --carbon-footprint

# In another terminal, run the scheduler
batsched -v
```

## 📚 Documentation

- **[API Reference](docs/API.md)**: description of plugin methods
- **[Basic Usage Tutorial](docs/tutorials/basic-usage.md)**: how to use the plugin in a simple example

## 🔗 Useful Links

- [SimGrid Documentation](https://simgrid.org/doc/latest/)
- [Batsim Documentation](https://batsim.readthedocs.io/)
- [SimGrid Fork with Carbon Footprint](https://github.com/saraiva03/simgrid/tree/carbon-footprint-calc)
- [Batsim Fork with Carbon Footprint](https://github.com/saraiva03/batsim/tree/carbon-footprint-calc)

---

**Note**: This plugin is under active development. The accuracy of models may vary depending on input parameters and specific environment configurations.


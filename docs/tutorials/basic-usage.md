# Tutorial: Basic Usage of Carbon Footprint Plugin

This guide describes how to prepare input files and run a simulation using the plugin. We do not include application code; familiarity with SimGrid is assumed. Build details are in the official SimGrid code.

## 📝 Step 1: Input Files

### 1.1 Platform XML

This file describes the simulation platform, including computational hosts, their energy characteristics, and carbon intensity.

Example file: [platform.xml example](https://github.com/saraiva03/batsim/blob/carbon-footprint-calc/platforms/carbon_footprint_platform_homogeneous.xml)

**Configuration explanation:**

- **`wattage_per_state`**: Energy consumption in watts for each pstate (idle:peak:max)
- **`wattage_off`**: Consumption when the host is turned off
- **`carbon_intensity`**: Carbon intensity in g/kWh

### 1.2 Workload File

The plugin works together with a workload file (a task/job file used by your orchestrator/simulator). This file defines the activities that generate energy consumption in the hosts described in `platform.xml`. 

Example file: [workload.json example](https://github.com/saraiva03/batsim/blob/carbon-footprint-calc/workloads/test_energy_minimal_load100.json)

## 💻 Step 2: Activating the Plugin via Command Line

### 2.1 In Batsim

To activate the carbon footprint plugin in Batsim, use the `--carbon-footprint` or `-C` flag:

```bash
# Basic command to activate the plugin
batsim -p platforms/platform.xml -w workloads/workload.json --carbon-footprint

# In another terminal, run the scheduler
batsched -v
```

## 🔍 Step 3: Dynamic Features

### 3.1 Changing Carbon Intensity

It is possible to change carbon intensity dynamically during simulation through the configuration method `sg_host_set_carbon_intensity(host, new_intensity)`. For this, it is necessary to pass via command line a trace-file containing the values to be changed, as well as the simulation time when this change occurs.

```bash
# 1. Activate the dynamic plugin
batsim -p platform.xml -w workload.json --carbon-footprint-dynamic <trace_file>

# 2. In another terminal, run the scheduler
batsched -v
```

### 3.2 Trace File Format

The trace file must contain carbon intensity changes in the format:

```
host_id	timestamp	carbon_intensity
```

**Example:**
```
conventional_host	100.5	40
renewable_host	200.0	15
conventional_host	300.0	30
```
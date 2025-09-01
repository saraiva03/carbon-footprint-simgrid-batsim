# API Reference - Carbon Footprint Plugin

Note: This reference describes the API exposed by the plugin. The `host_carbon_footprint.cpp` file in this repository is illustrative; the functional code is in the SimGrid fork where the plugin was integrated.

This documentation describes the complete API of the Carbon Footprint Plugin for SimGrid, based on the source code `host_carbon_footprint.cpp`.

## 🔧 Initialization

### `sg_host_carbon_footprint_plugin_init()`

Initializes the carbon footprint plugin. This function must be called before loading the platform and starting the workload, ensuring the registration of callbacks/extensions.

```cpp
void sg_host_carbon_footprint_plugin_init();
```

## 📥 Inputs and Operating Conditions

- Input files: `platform.xml` (host structure and energy properties) and a workload file compatible with your environment (defines loads/executions on hosts)
- Valid energy properties per host (e.g., `wattage_per_state`, `wattage_off`)
- `carbon_intensity` can be defined per host via XML; 

## 📊 Query Functions

### `sg_host_get_carbon_footprint()`

Returns the total carbon footprint emitted by the host up to the current moment.

```cpp
double sg_host_get_carbon_footprint(const_sg_host_t host);
```

### `sg_host_get_carbon_intensity()`

Returns the carbon intensity configured for the host.

```cpp
double sg_host_get_carbon_intensity(const_sg_host_t host);
```

## ⚙️ Configuration Functions

### `sg_host_set_carbon_intensity()`

Sets the carbon intensity for a specific host, including during simulation (dynamic adjustment).

```cpp
void sg_host_set_carbon_intensity(const_sg_host_t host, double carbon_intensity);
```

**Note**: This documentation is based on the source code `host_carbon_footprint.cpp`. For more detailed information about specific implementation, consult the source code directly.


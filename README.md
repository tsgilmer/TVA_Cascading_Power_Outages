# TVA_Cascading_Power_Outages
his project models cascading failures in a simplified representation of the Tennessee Valley Authority (TVA) electrical transmission network.  Using graph-based network modeling and Monte Carlo simulation, the project explores how local infrastructure failures can propagate through a regional power grid and cause large-scale outages.

---

## Project Overview

Power grids are complex interconnected systems where failures can spread rapidly through transmission networks. This project simulates cascading failures to understand:

• Which nodes frequently participate in cascading failures  
• Which infrastructure nodes trigger the largest outages  
• How blackout risk spreads across a regional power grid  

The model uses a simplified representation of TVA infrastructure including power plants, substations, dams, and grid hubs.

---

## Example Visualization

### TVA Network Model
![TVA Network](figures/network_map.png)

### Cascade Participation Heatmap
![Cascade Heatmap](figures/cascade_heatmap.png)

### Critical Blackout Trigger Map
![Trigger Map](figures/trigger_map.png)

### Blackout Probability Map
![Blackout Probability](figures/blackout_probability_map.png)

---

## Methodology

### Network Representation

The TVA grid is modeled as a graph:

G = (V, E)

Where:

V = infrastructure nodes  
E = transmission connections  

Nodes represent:

• Nuclear plants  
• Fossil plants  
• Hydroelectric dams  
• Substations  
• Regional grid hubs  

Edges represent high-voltage transmission connections between facilities.

The model is implemented using the **NetworkX** Python library.

---

### Cascade Failure Model

Cascades propagate using a probabilistic overload rule.

When a node fails:

1. Power flow redistributes to neighboring nodes  
2. Neighboring nodes may overload  
3. Overloaded nodes fail with probability *p*  
4. The cascade propagates until no new failures occur  

This process is implemented using a breadth-first propagation algorithm.

---

### Monte Carlo Simulation

To estimate system vulnerability statistically, the cascade model is executed across thousands of randomized simulations.

For each simulation:

1. A random node failure is introduced  
2. Cascading propagation is simulated  
3. Failed nodes are recorded  

This allows estimation of:

• cascade size distributions  
• node participation frequency  
• blackout probability across the grid  

---

## Key Findings

### Transmission Corridors Drive Cascades

Simulations reveal that cascading failures tend to propagate along major transmission corridors in the network.

The model consistently identifies a high-risk propagation path:

Memphis → Pickwick → Shoals → Browns Ferry → Huntsville → Chattanooga → Knoxville

This corridor roughly corresponds to the Tennessee River transmission backbone.

---

### Propagation Hubs Differ From Trigger Nodes

Nodes that frequently appear in cascading failures are not always the nodes that initiate failures.

Propagation hubs act as routing points where redistributed power flows concentrate during cascading events.

---

### Network Structure Drives Blackout Risk

Cascade behavior is strongly influenced by network topology. Nodes located on major routing paths exhibit significantly higher blackout probabilities.

---

## Technologies Used

Python  
NetworkX  
NumPy  
Pandas  
Matplotlib  

---

## Running the Simulation

Install dependencies:

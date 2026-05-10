# Index-Based Round Robin (IRR) Arbiter using SystemVerilog

## Overview
This project presents the design and functional verification of an Index-Based Round Robin (IRR) Arbiter using SystemVerilog for Network-on-Chip (NoC) router applications. The arbiter ensures fair and efficient allocation of shared resources among multiple requesters by dynamically rotating priority after each grant.

The project also implements a layered testbench methodology to verify the functionality of the arbiter under multiple request scenarios.

---

## Objectives
- Design an efficient Round Robin Arbiter
- Implement dynamic priority rotation
- Prevent starvation among requesters
- Generate valid one-hot grant signals
- Verify functionality using a layered SystemVerilog testbench

---

## Features
- Fair round-robin arbitration
- Dynamic priority update mechanism
- One-hot encoded grant generation
- Starvation prevention
- Layered verification environment
- Multiple functional test scenarios

---

## Technologies Used
- SystemVerilog
- Vivado
- Functional Verification
- Layered Testbench Methodology

---

## Project Structure

```text
IRR-Arbiter-SystemVerilog/
│
├── source/
│   └── irr_arbiter_project.sv
│
├── simulation/
│   ├── waveform.png
│   ├── simulation_output.txt
│   └── output.png
│
├── docs/
│   └── project_report.pdf
│
├── vivado_project/
│   └── likhitha.xpr
│
├── .gitignore
├── LICENSE
└── README.md
```

---

## Design Description

The file `irr_arbiter_project.sv` contains:
- Design modules
- Supporting modules
- Layered testbench

### Included Modules
1. `priority_reg_sf`
2. `irr_index_logic`
3. `irr_arbiter_top`
4. `transaction_store`
5. `generator`
6. `tb_irr_layered`

---

## Module Description

### priority_reg_sf
Stores and updates the arbitration priority after every successful grant.

### irr_index_logic
Determines the grant index (`g_id`) based on:
- Current priority
- Active request signals

### irr_arbiter_top
Top-level arbiter module responsible for:
- Integrating arbitration logic
- Generating one-hot grant signals
- Updating priority dynamically

### transaction_store
Stores request, grant, and grant ID values during verification.

### generator
Generates request patterns for simulation.

### tb_irr_layered
Layered SystemVerilog testbench used for functional verification.

---

## Working Principle
1. The arbiter continuously monitors request signals.
2. Based on the current priority, the next requester is selected.
3. A one-hot encoded grant signal is generated.
4. Priority rotates after every successful grant.
5. Multiple request scenarios are verified using the layered testbench.

---

## Verification Methodology

The project uses a layered verification approach including:
- Driver
- Monitor
- Checker
- Scoreboard mechanism

### Test Scenarios
- All requests active (`1111`)
- No requests (`0000`)
- Partial requests (`1001`)
- Single request cases
- Alternating request patterns (`0101` and `1010`)

---

## Simulation Results

### Expected Arbitration Sequence

For request pattern `1111`:

```text
0001 → 0010 → 0100 → 1000
```

### Verification Status

```text
PASS : All test cases passed
FAIL : 0
STATUS : ALL TESTS PASSED
```

The arbiter successfully demonstrated:
- Fair arbitration
- Correct priority rotation
- Proper one-hot grant generation
- Starvation prevention

---

## Waveform Output

Add simulation waveform image here.

```markdown
![Waveform](simulation/waveform.png)
```

---

## Applications
- Network-on-Chip (NoC) routers
- Bus arbitration
- Shared resource allocation
- Embedded systems
- Multi-master communication systems

---

## Advantages
- Fair resource allocation
- Prevents starvation
- Efficient arbitration mechanism
- Simple hardware implementation

---

## Limitations
- Minor delay may occur due to priority update logic
- Additional optimization may be required for larger systems

---

## How to Run the Project

### Using Vivado
1. Open Vivado
2. Create or open a project
3. Add `irr_arbiter_project.sv`
4. Run behavioral simulation
5. Observe waveform and console outputs

---

## References
1. IEEE Standard for SystemVerilog — IEEE Std 1800-2017
2. Masoud Oveis-Gharan and Gul N. Khan, *Index-based Round-Robin Arbiter for NoC Routers*
3. IEEE Embedded Systems Letters

---

## Authors
- M. Likhitha Reddy

---

## License
This project is licensed under the MIT License.

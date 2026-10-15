**Question 1**: Command used to create RISC_CORE.dlib

*   A. create_library -technology $TECH_FILE -ref_libs $REFERENCE_LIBRARY RISC_CORE.dlib
*   B. create_lib -technology $TECH_FILE -ref_libs $REFERENCE_LIBRARY RISC_CORE.dlib
*   C. create_dlib -technology $TECH_FILE -ref_libs $REFERENCE_LIBRARY RISC_CORE.dlib
*   D. create_ndm -technology $TECH_FILE -ref_libs $REFERENCE_LIBRARY RISC_CORE.dlib

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | `create_library` is not the standard Fusion Compiler command syntax. |
| $${\color{lightgreen}\text{B}}$$ | **`create_lib`** is the standard Synopsys Fusion Compiler / ICC2 command used to initialize a new design library container (`.dlib`) with technology and reference library bindings. |
| $${\color{red}\text{C}}$$ | `create_dlib` is not a valid Synopsys command. |
| $${\color{red}\text{D}}$$ | `create_ndm` is not a valid command for creating design libraries. |

</details>

---

**Question 2**: Changes that Design Mismatch Manager did to the design to achieve a successful link

*   A. Remove/disconnect pin, rename pin, create black box
*   B. Remove cells, designs & ports
*   C. Disconnect ports, remove blocks, disconnect pins
*   D. Remove designs

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | **Design Mismatch Manager (DMM)** resolves structural netlist/library binding mismatches by disconnecting or removing incompatible pins, renaming mismatched pin names, and stubbing missing references as black boxes. |
| $${\color{red}\text{B}}$$ | DMM does not indiscriminately purge entire design hierarchies or ports. |
| $${\color{red}\text{C}}$$ | DMM does not delete top-level design blocks. |
| $${\color{red}\text{D}}$$ | Incomplete and incorrect. |

</details>

---

**Question 3**: Which command is used to report mismatch summary for the specified designs and reference libraries

*   A. report_design_mismatch -verbose
*   B. report_data_mismatch -verbose
*   C. report_mismatch_configs -all
*   D. report_mismatch -verbose

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Incorrect command syntax. |
| $${\color{red}\text{B}}$$ | Incorrect command syntax. |
| $${\color{red}\text{C}}$$ | Reports mismatch configuration rules, not the design mismatch report itself. |
| $${\color{lightgreen}\text{D}}$$ | **`report_mismatch -verbose`** outputs the detailed summary report of all detected port, pin, and instance mismatches between the design and reference libraries. |

</details>

---

**Question 4**: Which command is used to get all leaf-cells in the current physical hierarchy

*   A. get_flat_cells -hierarchical
*   B. get_flat_cells \*I_SDRAM_IF\*sd_mux\*
*   C. get_cells \*/I_SDRAM_IF/sd_mux\*
*   D. get_cells -hierarchical

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | **`get_flat_cells -hierarchical`** flattens the view across the current physical hierarchy and returns strictly all leaf-level (non-hierarchical standard cell) instances. |
| $${\color{red}\text{B}}$$ | Filters by a specific name pattern rather than returning all leaf cells. |
| $${\color{red}\text{C}}$$ | Returns matching cell instances, which may include hierarchical sub-design blocks. |
| $${\color{red}\text{D}}$$ | Returns both hierarchical blocks and leaf cells across the hierarchy. |

</details>

---

**Question 5**: Physical representation of a port is

*   A. Pin
*   B. Terminal
*   C. Port
*   D. None

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Pins are the connection points on internal leaf instances/standard cells. |
| $${\color{lightgreen}\text{B}}$$ | In the Synopsys physical data model, a **terminal** is the physical realization/geometry (metal shape/pad connection) of a logical top-level boundary **port**. |
| $${\color{red}\text{C}}$$ | Port represents the logical object, not its physical shape representation. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 6**: Command used to get lib_cell attribute of a cell SGI30_764 object

*   A. report_attributes -application [get_lib_cell -of_objects [get_cells sgi30_764]]
*   B. report_attributes -application [get_attribute [get_cells sgi30_764] lib_cell]
*   C. report_attributes -application [get_cells SGI30_764]
*   D. Both a & b

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Valid command structure using `-of_objects`. |
| $${\color{red}\text{B}}$$ | Valid command structure retrieving the `lib_cell` object attribute directly. |
| $${\color{red}\text{C}}$$ | Reports attributes of the design cell instance, not of the underlying reference `lib_cell` object. |
| $${\color{lightgreen}\text{D}}$$ | **Both a and b** correctly query and report the attributes of the library cell (`lib_cell`) associated with the instance. |

</details>

---

**Question 7**: Which command is used to filter ICG's in certain power domain

*   A. get_cells -hierarchical -filter "power_domain == PDA && is_integrated_clock_gating_cell"
*   B. get_flat_cells -hierarchical -filter "power_domain != PDA && is_integrated_clock_gating_cell"
*   C. get_flat_cells -hierarchical -filter "power_domain == PDA && is_integrated_clock_gating_cell"
*   D. get_flat_cells -hierarchical -filter "power_domain == PDA\|\| is_integrated_clock_gating_cell"

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | `get_cells` searches hierarchical and leaf objects; in physical domains `get_flat_cells` directly targets placed leaf cells. |
| $${\color{red}\text{B}}$$ | Uses `!=` (not equal), which excludes domain PDA. |
| $${\color{lightgreen}\text{C}}$$ | **`get_flat_cells -hierarchical -filter "power_domain == PDA && is_integrated_clock_gating_cell"`** flattens the hierarchy and isolates leaf ICG instances belonging strictly to power domain PDA. |
| $${\color{red}\text{D}}$$ | Uses logical OR (`\|\|`), which captures non-ICG cells in PDA as well as ICGs outside PDA. |

</details>

---

**Question 8**: Find a command to set app-option in design

*   A. set_app_options –name time.disable_recovery_removal_checks –value true
*   B. set_app_options –list { time.disable_recovery_removal_checks true }
*   C. Both a & b
*   D. Only a

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Standard syntax using individual `-name` and `-value` arguments. |
| $${\color{red}\text{B}}$$ | Standard syntax using the `-list {option value}` pair convention. |
| $${\color{lightgreen}\text{C}}$$ | **Both a & b** are valid Synopsys Tcl syntaxes for setting application options via `set_app_options`. |
| $${\color{red}\text{D}}$$ | Fails to recognize the valid `-list` syntax. |

</details>

---

**Question 9**: Global scoped app-options

*   A. Apply to all blocks loaded in the current tool session, and are saved with the block(s)
*   B. Apply to the current block, and are saved with the block
*   C. Apply to all blocks loaded in the current tool session, and are not saved with the block(s)
*   D. All the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Global options are session-only and never saved into block databases. |
| $${\color{red}\text{B}}$$ | Describes block-scoped options. |
| $${\color{lightgreen}\text{C}}$$ | **Global-scoped application options** affect every block open in the current session and are strictly non-persistent (not saved with the block to disk). |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 10**: How can you check MV cells added during initial_map

*   A. check_mv_design
*   B. report_mv_design
*   C. check_mv_cells
*   D. report_mv_cells

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Checks UPF consistency and power rule integrity. |
| $${\color{red}\text{B}}$$ | Generates general multi-voltage architecture reports. |
| $${\color{red}\text{C}}$$ | Non-existent command. |
| $${\color{lightgreen}\text{D}}$$ | **`report_mv_cells`** prints a detailed table of all level shifters, isolation cells, and power switches inserted into the netlist. |

</details>

---

**Question 11**: What is the command to verify ICG cells are inserted ?

*   A. check_clock_gating
*   B. report_clock_gating
*   C. report_icg
*   D. get_icg

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Checks for clock gating structural rule violations. |
| $${\color{lightgreen}\text{B}}$$ | **`report_clock_gating`** displays the full gating summary, reporting inserted ICGs, gated register counts, and gating efficiency. |
| $${\color{red}\text{C}}$$ | Non-standard command syntax. |
| $${\color{red}\text{D}}$$ | Non-standard command syntax. |

</details>

---

**Question 12**: How to report unloaded registers

*   A. report_registers
*   B. report_unloaded_registers
*   C. get_unloaded_registers
*   D. check_unloaded_registers

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | **`report_registers`** (using `-unloaded` or reporting register classification tables) reports unloaded, constant, and dead registers in Fusion Compiler. |
| $${\color{red}\text{B}}$$ | Non-existent command. |
| $${\color{red}\text{C}}$$ | Non-existent command. |
| $${\color{red}\text{D}}$$ | Non-existent command. |

</details>

---

**Question 13**: Command to run only logic_opto stage in FC

*   A. compile_fusion -from logic_opto
*   B. compile_fusion -to logic_opto
*   C. compile_fusion -from logic_opto -to logic_opto
*   D. compile_fusion -from initial_map -to logic_opto

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Runs from `logic_opto` through the remainder of the flow. |
| $${\color{red}\text{B}}$$ | Runs from the beginning of `compile_fusion` up to `logic_opto`. |
| $${\color{lightgreen}\text{C}}$$ | Specifying **`-from logic_opto -to logic_opto`** bounds execution strictly to that single stage. |
| $${\color{red}\text{D}}$$ | Runs two stages (`initial_map` and `logic_opto`). |

</details>

---

**Question 14**: How do you check of standard cell count in your design?

*   A. report_qor
*   B. report_utilization
*   C. report_design
*   D. a&c

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | `report_qor` prints cell counts, design area, and timing metrics. |
| $${\color{red}\text{B}}$$ | Focuses on area utilization and site occupancy percentages. |
| $${\color{red}\text{C}}$$ | `report_design` summarizes structural instances, including total standard cell counts. |
| $${\color{lightgreen}\text{D}}$$ | **Both a & c** (`report_qor` and `report_design`) report standard cell counts in the design. |

</details>

---

**Question 15**: Through which command you find high fanout nets in the design

*   A. all_high_fanout
*   B. all_high_transitive_fanout -nets -threshold
*   C. report_high_fanout -nets
*   D. get_high_fanout -nets

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | **`all_high_fanout`** is the standard Synopsys command to query high-fanout nets meeting a specified fanout threshold (`-nets -threshold <num>`). |
| $${\color{red}\text{B}}$$ | Invalid command name. |
| $${\color{red}\text{C}}$$ | Non-existent command. |
| $${\color{red}\text{D}}$$ | Non-existent command. |

</details>

---

**Question 16**: If you want to know the count of scan chain inserted, till what stage you should run compile_fusion?

*   A. logic_opto
*   B. initial_drc
*   C. initial_opto
*   D. initial_map

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Scan chains are not yet synthesized or stitched. |
| $${\color{red}\text{B}}$$ | Precedes scan chain architecture. |
| $${\color{lightgreen}\text{C}}$$ | During **`initial_opto`**, scan chains are architected, placed, and stitched, allowing scan chain count verification. |
| $${\color{red}\text{D}}$$ | Registers are mapped, but scan chains are not stitched. |

</details>

---

**Question 17**: How you can find out what compile stages have been run?

*   A. report_optimization_history
*   B. get_optimization_history
*   C. check_optimization_history
*   D. report_optimization

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | **`report_optimization_history`** audits the block and prints a chronological report of all executed optimization and compile steps. |
| $${\color{red}\text{B}}$$ | Non-existent command. |
| $${\color{red}\text{C}}$$ | Non-existent command. |
| $${\color{red}\text{D}}$$ | Non-existent command. |

</details>

---

**Question 18**: How to confirm whether all cells are legalized or nor

*   A. report_legality
*   B. check_legality
*   C. report_legalization
*   D. check_legalization

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Non-existent command. |
| $${\color{lightgreen}\text{B}}$$ | **`check_legality`** checks placement legalization, reporting cell overlaps, off-pitch violations, site misalignments, or orientation errors. |
| $${\color{red}\text{C}}$$ | Non-existent command. |
| $${\color{red}\text{D}}$$ | Non-existent command. |

</details>

---

**Question 19**: What does compile_fusion try to optimize for?

*   A. Significant improvement in power
*   B. Time slack improvement
*   C. Both
*   D. None

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Incomplete on its own. |
| $${\color{red}\text{B}}$$ | Incomplete on its own. |
| $${\color{lightgreen}\text{C}}$$ | `compile_fusion` performs concurrent PPA optimization, simultaneously targeting **timing slack improvement and total power reduction**. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 20**: Recommended checks before compile_fusion

*   A. check_design
*   B. check_mv_design
*   C. compile_fusion -check_only
*   D. All

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Checks netlist and logical design connectivity. |
| $${\color{red}\text{B}}$$ | Validates multi-voltage power domains, level shifters, and isolation strategies. |
| $${\color{red}\text{C}}$$ | Dry-run check for compile readiness. |
| $${\color{lightgreen}\text{D}}$$ | **All of the above** are best-practice pre-compile verification checks. |

</details>

---

**Question 21**: What is the command to check congestion in the design?

*   A. report_congestion
*   B. check_congestion
*   C. get_congestion
*   D. All

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | **`report_congestion`** analyzes global routing cells (GRCs) and generates routing congestion reports and maps. |
| $${\color{red}\text{B}}$$ | Non-existent command. |
| $${\color{red}\text{C}}$$ | Non-existent command. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 22**: What is the command to load upf and commit upf

*   A. load_upf File_name
*   B. load_upf file_name and commit_upf
*   C. commit_upf
*   D. load_upf

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Loads syntax without resolving netlist objects. |
| $${\color{lightgreen}\text{B}}$$ | The full UPF integration flow requires **`load_upf <file>`** to read power intent, followed by **`commit_upf`** to bind intent to the netlist. |
| $${\color{red}\text{C}}$$ | Cannot commit without loading first. |
| $${\color{red}\text{D}}$$ | Incomplete. |

</details>

---

**Question 23**: Command which checks for violations in a multi voltage design ?

*   A. report_power
*   B. report_mv_design
*   C. check_mv_design
*   D. report_upf

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Calculates static and dynamic power consumption. |
| $${\color{red}\text{B}}$$ | Displays summary characteristics of the MV configuration. |
| $${\color{lightgreen}\text{C}}$$ | **`check_mv_design`** checks for multi-voltage violations, including missing level shifters, isolation rule breaches, and power state table inconsistencies. |
| $${\color{red}\text{D}}$$ | Echoes loaded UPF commands. |

</details>

---

**Question 24**: Command which inserts power management cells before compile stage

*   A. create_mv_cells
*   B. set_mv_cells
*   C. set_mv_cells [get_cells \*]
*   D. create_mv_cells -design

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | **`create_mv_cells`** explicitly instantiates and inserts UPF power-management cells (level shifters, isolation cells) prior to main compilation. |
| $${\color{red}\text{B}}$$ | Non-existent command. |
| $${\color{red}\text{C}}$$ | Non-existent command. |
| $${\color{red}\text{D}}$$ | Invalid syntax switch. |

</details>

---

**Question 25**: What is the purpose of report_incomplete_upf

*   A. Summary status of changes made by incomplete UPF flow
*   B. To identify potential issues with UPF and correct it for the next cycle of synthesis
*   C. Same as check_mv_design
*   D. a & b

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Summarizes architectural assumptions made by the incomplete UPF flow. |
| $${\color{red}\text{B}}$$ | Highlights missing constraints/supplies to be fixed for subsequent cycles. |
| $${\color{red}\text{C}}$$ | Performs distinct static design checking. |
| $${\color{lightgreen}\text{D}}$$ | **Both a & b** describe the diagnostic and reporting objectives of `report_incomplete_upf`. |

</details>

---

**Question 26**: Through which command you enable Incomplete UPF support before loading any UPF

*   A. set_app_options -name mv.incomplete_upf.enable -value true
*   B. set_app_options -name mv.incomplete_upf.enable -value false
*   C. set_app_options -name mv.incomplete_upf.enable
*   D. set_app_options -name mv.incomplete_upf.enable -none

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | Setting **`mv.incomplete_upf.enable` to `true`** allows FC to tolerate partially defined UPF intent without failing elaboration. |
| $${\color{red}\text{B}}$$ | Disables the feature. |
| $${\color{red}\text{C}}$$ | Incomplete syntax missing `-value`. |
| $${\color{red}\text{D}}$$ | Invalid syntax switch. |

</details>

---

**Question 27**: In what situations would you find auto-floorplan feature useful

*   A. When we know that floorplan available is not golden
*   B. When we don't know if floorplan provided to us is complete or not
*   C. To allow macros to be automatically placed in a reasonable location
*   D. All of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Useful when working with unverified/draft floorplans. |
| $${\color{red}\text{B}}$$ | Useful when evaluating incomplete floorplans. |
| $${\color{red}\text{C}}$$ | Generates automated macro placement for feasibility estimation. |
| $${\color{lightgreen}\text{D}}$$ | **All of the above** are situations where FC's auto-floorplanning is helpful. |

</details>

---

**Question 28**: what is the significance of the command "set_attribute [get_site_defs unit] symmetry Y"

*   A. This allows the tool to use a library cell and flip it on its Y-axis
*   B. This is automatically set and we don't need to use it
*   C. This allows the tool to use a library cell and flip it on its X-axis
*   D. None

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | Setting site symmetry to `Y` permits the placement engine to **mirror/flip standard cells across their Y-axis** to optimize routing and pin access while maintaining row legality. |
| $${\color{red}\text{B}}$$ | Foundry libraries may omit or require explicit symmetry overrides. |
| $${\color{red}\text{C}}$$ | X-axis flipping corresponds to symmetry `X`. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 29**: Some important preliminary manual checks before starting synthesis

*   A. don’t_touch & lib_cell purpose settings of library cells
*   B. Technology node setting (set_technology) & metal layer availability (set/report_ignored_layers)
*   C. Multi-core settings (set_host_options)
*   D. All of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Prevents mapping to prohibited cells and preserves logic. |
| $${\color{red}\text{B}}$$ | Configures node scaling and routing layer constraints. |
| $${\color{red}\text{C}}$$ | Configures compute resources and thread counts. |
| $${\color{lightgreen}\text{D}}$$ | **All of the above** are essential baseline sanity checks prior to synthesis. |

</details>

---

**Question 30**: Generation of die, core, rows, and tracks is controlled by ?

*   A. compile.auto_floorplan.initialize
*   B. compile.auto_floorplan.initialize -design
*   C. compile.auto_floorplan.initialize -nosplit
*   D. compile.auto_floorplan.initialize -verbose

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | **`compile.auto_floorplan.initialize`** is the application option that controls automatic synthesis and initialization of the die boundary, core area, site rows, and routing tracks. |
| $${\color{red}\text{B}}$$ | Invalid option syntax. |
| $${\color{red}\text{C}}$$ | Invalid option syntax. |
| $${\color{red}\text{D}}$$ | Invalid option syntax. |

</details>

---

**Question 31**: How do you check if your auto-floorplaning constraints reflect user intent

*   A. get_auto_floorplan_constraints
*   B. report_auto_floorplan_constraints
*   C. check_auto_floorplan_constraints
*   D. report_floorplan_constraints

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Returns constraint collections rather than formatted reports. |
| $${\color{lightgreen}\text{B}}$$ | **`report_auto_floorplan_constraints`** lists active auto-floorplanning parameter constraints (aspect ratio, utilization, core margins). |
| $${\color{red}\text{C}}$$ | Non-existent command. |
| $${\color{red}\text{D}}$$ | Does not report auto-floorplan parameters specifically. |

</details>

---

**Question 32**: How to control the guard band size of created voltage areas ?

*   A. set_shaping_options -guard_band_size
*   B. create_shaping_options -guard_band_size
*   C. set_shaping_options -guard_band
*   D. set_shaping_options -guard_band_size -all

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | **`set_shaping_options -guard_band_size`** defines channel clearance and guardband spacing around voltage areas during physical floorplanning. |
| $${\color{red}\text{B}}$$ | Non-existent command. |
| $${\color{red}\text{C}}$$ | Incomplete switch name. |
| $${\color{red}\text{D}}$$ | `-all` is an invalid switch for this command. |

</details>

---

**Question 33**: What is the command to get a collection of all auto-generated placement blockages?

*   A. report_placement_blockages -filter is_derived==true
*   B. get_placement_blockages -filter is_derived==true
*   C. get_placement_blockages -filter is_derived==false
*   D. report_placement_blockages -filter is_derived==false

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | `report_*` commands print human-readable text rather than returning Tcl collections. |
| $${\color{lightgreen}\text{B}}$$ | **`get_placement_blockages -filter "is_derived == true"`** returns a Tcl collection of blockages automatically generated by the tool (such as macro halo blockages). |
| $${\color{red}\text{C}}$$ | `is_derived == false` filters for user-defined blockages. |
| $${\color{red}\text{D}}$$ | `report_*` command; does not return an actionable Tcl object collection. |

</details>

---

**Question 34**: What app option will constrain the macro placement

*   A. make_macro_constraints
*   B. create_macro_constraints
*   C. set_macro_constraints
*   D. set_hard_macro_constraints

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Non-existent command. |
| $${\color{red}\text{B}}$$ | Non-existent command. |
| $${\color{lightgreen}\text{C}}$$ | **`set_macro_constraints`** configures physical constraints (margins, orientations, allowed locations) for automated macro placement. |
| $${\color{red}\text{D}}$$ | Non-existent command. |

</details>

---

**Question 35**: What command should be used to understand the reason behind un-gated registers

*   A. get_attribute [all_clock_gates] ungated
*   B. report_clock_gating -ungated
*   C. check_clock_gating -ungated
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Attribute does not exist. |
| $${\color{lightgreen}\text{B}}$$ | **`report_clock_gating -ungated`** identifies registers that were not clock-gated and reports the root cause (e.g., bitwidth below threshold, multi-cycle timing exceptions, user exclusions). |
| $${\color{red}\text{C}}$$ | Non-existent command. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 36**: Which command creates a collection of clock gate cells that meet the specified criteria ?

*   A. report_clock_icg
*   B. report_clock_gates
*   C. get_clock_gates
*   D. get_clock_icg

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Non-existent command. |
| $${\color{red}\text{B}}$$ | Reports clock gate information to the transcript. |
| $${\color{lightgreen}\text{C}}$$ | **`get_clock_gates`** returns a Tcl collection of clock gating instances matching specified filter criteria. |
| $${\color{red}\text{D}}$$ | Non-existent command. |

</details>

---

**Question 37**: How to find out what ICGs are enabled for insertion?

*   A. get_cells \* -filter valid_purposes=~\*cts\*
*   B. report_lib_cells \* -filter valid_purposes=~\*cts\*
*   C. check_lib_cells \* -filter valid_purposes=~\*cts\*
*   D. get_lib_cells -filter "clock_gating_integrated_cell==true && valid_purposes=~\*cts\*"

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Queries instantiated design cells rather than reference library cells. |
| $${\color{red}\text{B}}$$ | `report_lib_cells` does not take an inline `-filter` pattern in this format. |
| $${\color{red}\text{C}}$$ | Non-existent command. |
| $${\color{lightgreen}\text{D}}$$ | **`get_lib_cells -filter "clock_gating_integrated_cell == true && valid_purposes =~ *cts*"`** returns reference library cells configured as integrated clock gates and marked legal for CTS/clock insertion. |

</details>

---

**Question 38**: How to get a list of all the pins of one of the clock gates ?

*   A. report_pins -of_objects reg_file/rama_cg
*   B. get_pins -of_objects reg_file/rama_cg
*   C. check_pins -of_objects reg_file/rama_cg
*   D. None

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Non-existent command. |
| $${\color{lightgreen}\text{B}}$$ | **`get_pins -of_objects <cell_name>`** is the standard Synopsys accessor command to return all pin objects belonging to an instance. |
| $${\color{red}\text{C}}$$ | Non-existent command. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 39**: How to find the clock pins that are driven by one of the ICGs

*   A. all_connected [get_nets -of_objects reg_file/rama_cg/GCLK]
*   B. get_nets -of_objects reg_file/rama_cg/GCLK
*   C. all_connected [get_nets -of_objects reg_file/rama_cg]
*   D. all_connected [get_pins -of_objects reg_file/rama_cg/GCLK]

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | Querying the output net (`get_nets -of_objects <ICG>/GCLK`) and running **`all_connected`** returns all sink clock pins connected to that gated clock net. |
| $${\color{red}\text{B}}$$ | Returns only the net object itself. |
| $${\color{red}\text{C}}$$ | References the cell instead of its gated clock output pin. |
| $${\color{red}\text{D}}$$ | `all_connected` expects a net object, not a pin object. |

</details>

---

**Question 40**: How to find out what controls the ICGs?

*   A. all_fanout -flat -from reg_file/rama_cg/EN
*   B. all_fanin -flat -from reg_file/rama_cg/EN
*   C. all_fanin -flat -to reg_file/rama_cg/EN
*   D. all_fanout -flat -to reg_file/rama_cg/EN

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Fanout traces downstream driven logic, not the controlling inputs. |
| $${\color{red}\text{B}}$$ | `all_fanin` uses `-to`, not `-from`. |
| $${\color{lightgreen}\text{C}}$$ | Tracing the input enable pin backwards via **`all_fanin -flat -to reg_file/rama_cg/EN`** returns the logic cone controlling the clock gate. |
| $${\color{red}\text{D}}$$ | `all_fanout` uses `-from`, not `-to`. |

</details>

---

**Question 41**: How to prevent Fusion Compiler from merging the ICGs of a_ and b_rams with other ICGs ?

*   A. set_clock_gate_transformations [get_cells "reg_file/rama_cg reg_file/ramb_cg"] true -merge_equivalents true
*   B. set_clock_gate_transformations [get_cells "reg_file/rama_cg reg_file/ramb_cg"] true -merge_equivalents false
*   C. create_clock_gate_transformations [get_cells "reg_file/rama_cg reg_file/ramb_cg"] true -merge_equivalents false
*   D. create_clock_gate_transformations [get_cells "reg_file/rama_cg reg_file/ramb_cg"] true -merge_equivalents true

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | `-merge_equivalents true` enables merging. |
| $${\color{lightgreen}\text{B}}$$ | **`set_clock_gate_transformations ... -merge_equivalents false`** prevents Fusion Compiler from merging the targeted ICG cells with other functionally equivalent clock gates. |
| $${\color{red}\text{C}}$$ | Non-existent command. |
| $${\color{red}\text{D}}$$ | Non-existent command. |

</details>

---

**Question 42**: How you can find out the names of the pre-existing ICGs at any time by using ?

*   A. get_clock_gates pre_existing
*   B. check_clock_gates -origin pre_existing
*   C. report_clock_gates -origin pre_existing
*   D. get_clock_gates -origin pre_existing

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Missing the required `-origin` switch. |
| $${\color{red}\text{B}}$$ | Non-existent command. |
| $${\color{red}\text{C}}$$ | Non-existent command. |
| $${\color{lightgreen}\text{D}}$$ | **`get_clock_gates -origin pre_existing`** queries clock gates instantiated directly in the input RTL rather than inserted by the tool. |

</details>

---

**Question 43**: How you can find out the names of the tool inserted ICGs at any time by using ?

*   A. get_clock_gates -origin tool_inserted
*   B. report_clock_gates -origin tool_inserted
*   C. a & b
*   D. get_clock_gates tool_inserted

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | **`get_clock_gates -origin tool_inserted`** returns the collection of ICGs inserted automatically during synthesis and compile stages. |
| $${\color{red}\text{B}}$$ | Non-existent command. |
| $${\color{red}\text{C}}$$ | Option B is an invalid command. |
| $${\color{red}\text{D}}$$ | Missing the required `-origin` switch. |

</details>

---

**Question 44**: How to generate a timing report for the most critical tool-inserted ICG enable pin?

*   A. check_timing -to [get_clock_gate_pins -type enable \\ -of_objects [get_clock_gates -origin tool_inserted]]
*   B. report_timing -to [get_clock_gate_pins -type enable \\ -of_objects [get_clock_gates -origin tool_inserted]]
*   C. get_timing -to [get_clock_gate_pins -type enable \\ -of_objects [get_clock_gates -origin tool_inserted]]
*   D. None

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | `check_timing` checks constraint consistency, not timing slack. |
| $${\color{lightgreen}\text{B}}$$ | **`report_timing -to [get_clock_gate_pins -type enable -of_objects [get_clock_gates -origin tool_inserted]]`** queries the enable pins of all tool-inserted ICGs and reports the worst setup timing path ending on them. |
| $${\color{red}\text{C}}$$ | Non-existent command. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 45**: How to generate timing reports to the tool-inserted and pre-existing ICGs, and capture the latencies to their respective clock pins

*   A. report_timing -to clock_gate\*
*   B. check_timing -to clock_gate\*
*   C. get_timing -to clock_gate\*
*   D. get_timing -from clock_gate\*

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | **`report_timing -to clock_gate*`** targets the clock gating cells, reporting path timing and clock arrival latencies to their pins. |
| $${\color{red}\text{B}}$$ | Performs constraint checks, not timing path calculations. |
| $${\color{red}\text{C}}$$ | Non-existent command. |
| $${\color{red}\text{D}}$$ | Non-existent command. |

</details>

---

**Question 46**: How to generate a max-delay constraints report ?

*   A. report_constraint -max_delay -sig 2
*   B. report_constraint -delay -sig 2
*   C. get_constraint -max_delay -sig 2
*   D. None

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | **`report_constraint -max_delay -sig 2`** reports max_delay constraint violations formatted to two significant digits. |
| $${\color{red}\text{B}}$$ | `-delay` is an invalid switch for `report_constraint`. |
| $${\color{red}\text{C}}$$ | Non-existent command. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 47**: Which command is used to restrict what happens with existing clock gates ?

*   A. generate_clock_gate_transformations
*   B. create_clock_gate_transformations
*   C. set_clock_gate_transformations
*   D. get_clock_gate_transformations

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Non-existent command. |
| $${\color{red}\text{B}}$$ | Non-existent command. |
| $${\color{lightgreen}\text{C}}$$ | **`set_clock_gate_transformations`** configures whether existing clock gates can be merged, split, or removed during optimization passes. |
| $${\color{red}\text{D}}$$ | Queries transformation settings rather than configuring them. |

</details>

---

**Question 48**: Which app option enables self-gating ?

*   A. compile.clockgate.self_gating
*   B. compile.clock_gate.self_gating
*   C. compile.clockgate -self_gating
*   D. compile.clockgate -self

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | **`compile.clockgate.self_gating`** is the application option that enables automatic XOR-based self-gating insertion during compilation. |
| $${\color{red}\text{B}}$$ | Naming convention does not use an underscore in `clockgate`. |
| $${\color{red}\text{C}}$$ | Invalid option syntax. |
| $${\color{red}\text{D}}$$ | Invalid option syntax. |

</details>

---

**Question 49**: Which command controls self-gating globally?

*   A. create_self_gating_options
*   B. set_self_gating_options
*   C. generate_self_gating_options
*   D. None

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Non-existent command. |
| $${\color{lightgreen}\text{B}}$$ | **`set_self_gating_options`** configures global self-gating parameters (e.g., target register group size, fanout thresholds). |
| $${\color{red}\text{C}}$$ | Non-existent command. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 50**: Which command controls self-gating on specific objects ?

*   A. create_self_gating_objects
*   B. generate_self_gating_objects
*   C. set_self_gating_objects
*   D. None

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Non-existent command. |
| $${\color{red}\text{B}}$$ | Non-existent command. |
| $${\color{lightgreen}\text{C}}$$ | **`set_self_gating_objects`** applies self-gating inclusions and exclusions on designated design modules, cells, or registers. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

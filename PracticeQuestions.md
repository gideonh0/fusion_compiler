**Question 1**: What files are not saved in the design block, design library or reference library

*   A. RTL
*   B. Timing constraints, UPF
*   C. Technology files
*   D. Cell libraries (CLIBs) such as logic, timing, physical

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | RTL descriptions are parsed and elaborated into generic netlists and logic graphs stored inside the design library/block. |
| $${\color{red}\text{B}}$$ | Timing constraints (SDC/XDC) and UPF power intent are explicitly serialized and saved within the NDM block. |
| $${\color{red}\text{C}}$$ | The physical technology file (.tf) and rules are imported directly into the design/reference library container. |
| $${\color{lightgreen}\text{D}}$$ | **Cell libraries (CLIBs)** in NDM format remain external reference libraries (`-ref_libs`); they are linked or referenced by pointers rather than being physically copied and embedded inside the design block, design library, or other reference libraries. |

</details>

---

**Question 2**: First step in data-setup is to create______________

*   A. UPF
*   B. Design library
*   C. Modules
*   D. Block

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | UPF power intent cannot be read until a design library and active block container exist. |
| $${\color{lightgreen}\text{B}}$$ | **Creating the design library** (`create_lib`) is the mandatory foundational first step in Fusion Compiler to establish the database workspace container before importing technology, netlists, or constraints. |
| $${\color{red}\text{C}}$$ | Modules are logical structures read or elaborated only after the workspace exists. |
| $${\color{red}\text{D}}$$ | An individual block is created or opened inside an already established design library container. |

</details>

---

**Question 3**: To create a design library \___files to be specified

*   A. Reference libraries
*   B. Technology file
*   C. Both a & b
*   D. Only b

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Reference libraries alone lack layer definitions and manufacturing design rules. |
| $${\color{red}\text{B}}$$ | A technology file alone lacks standard cell logical, timing, and physical models. |
| $${\color{lightgreen}\text{C}}$$ | **Both reference libraries and a technology file** (or a tech reference library via `-use_technology_lib`) must be specified when creating a design library using `create_lib`. |
| $${\color{red}\text{D}}$$ | Incomplete specification. |

</details>

---

**Question 4**: When creating a design library, how to specify reference library paths?

*   A. Using absolute paths
*   B. Using relative paths
*   C. Both a&b
*   D. None

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Absolute paths are valid but not the only supported approach. |
| $${\color{red}\text{B}}$$ | Relative paths are valid but not the only supported approach. |
| $${\color{lightgreen}\text{C}}$$ | Fusion Compiler supports **both absolute and relative directory paths** for specifying `-ref_libs` during library creation. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 5**: With absolute reference library paths

*   A. If the design library moves, nothing changes – libraries still resolve
*   B. If the reference libraries move, you need to update the search path and rebind
*   C. Reference libraries need to move along with the design library
*   D. Both a&b

<details>
  <summary>Analysis</summary>
  
| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | True, but incomplete on its own. |
| $${\color{red}\text{B}}$$ | True, but incomplete on its own. |
| $${\color{red}\text{C}}$$ | Moving reference libraries in tandem is required for relative paths, not absolute paths. |
| $${\color{lightgreen}\text{D}}$$ | **Both a and b are correct**: Absolute paths maintain their bindings regardless of where the design library moves, but moving the referenced libraries breaks the path and mandates rebinding. |

</details>

---

**Question 6**: With relative reference library paths

*   A. Reference libraries need to move along with the design library
*   B. If they do not move along, you need to update the reference library paths
*   C. If the reference libraries move, you need to update the search path and rebind
*   D. Both a&b

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | True, but incomplete. |
| $${\color{red}\text{B}}$$ | True, but incomplete. |
| $${\color{red}\text{C}}$$ | Describes absolute rebinding behavior rather than relative movement rules. |
| $${\color{lightgreen}\text{D}}$$ | **Both a and b are correct**: Relative references maintain consistency only if relative hierarchy distance is preserved when directories move, otherwise path reconfiguration is necessary. |

</details>

---

**Question 7**: Fusion Compiler tool provides which of the following library analysis capabilities

*   A. Identify redundant, outlier, and equivalent cells in library cell families, which you can exclude from optimization during the subsequent steps in the implementation flow
*   B. Identify gaps in library cell families, which you can provide as feedback to your library vendor with the goal of improving the reference libraries
*   C. Compare the delay, power, area, and other characteristics of equivalent cells in different libraries or different versions of the same library
*   D. All of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Valid library analysis capability supported by FC. |
| $${\color{red}\text{B}}$$ | Valid library benchmarking capability supported by FC. |
| $${\color{red}\text{C}}$$ | Valid comparative analysis capability supported by FC. |
| $${\color{lightgreen}\text{D}}$$ | **All of the above** capabilities are built into Fusion Compiler's library analysis and audit utilities (`check_library`). |

</details>

---

**Question 8**: Linking of the design is done using

*   A. Analyze
*   B. Elaborate
*   C. set_top_module
*   D. Both a &b

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | `analyze` strictly checks syntax and translates RTL into an intermediate format. |
| $${\color{red}\text{B}}$$ | `elaborate` builds structural representations and generic gates. |
| $${\color{lightgreen}\text{C}}$$ | **`set_top_module`** specifies the root design and executes linking across design and reference libraries. |
| $${\color{red}\text{D}}$$ | Neither command links the design; they only prepare the design database before top-level linking. |

</details>

---

**Question 9**: save_lib command saves \____

*   A. All open blocks to disk
*   B. Only saves the current block to disk
*   C. Both a&b
*   D. None

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | **`save_lib`** commits and writes the entire library including **all open blocks** contained within that library to disk. |
| $${\color{red}\text{B}}$$ | Saving strictly the current active block is performed by `save_block`. |
| $${\color{red}\text{C}}$$ | Incorrect distinction between library-level and block-level commands. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 10**: What is the full form of DMM

*   A. Design Mismatch Method
*   B. Design Mismatch Manager
*   C. Design Multi Method
*   D. None

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Incorrect expansion. |
| $${\color{lightgreen}\text{B}}$$ | **Design Mismatch Manager (DMM)** is the tool feature that detects, reports, and auto-resolves interface and library discrepancies. |
| $${\color{red}\text{C}}$$ | Incorrect expansion. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 11**: General reasons for link failures

*   A. Missing ports
*   B. Logic references missing
*   C. Port name mismatch
*   D. All of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Missing module boundary ports cause unresolved connections. |
| $${\color{red}\text{B}}$$ | Missing reference definitions (leaf cells or sub-blocks) prevent resolving instances. |
| $${\color{red}\text{C}}$$ | Case or spelling mismatches on port names result in broken connectivity. |
| $${\color{lightgreen}\text{D}}$$ | **All of the above** are typical root causes of structural link failures in digital design flows. |

</details>

---

**Question 12**: autofix DMM configuration addresses \_____ issues

*   A. bus_bit_naming
*   B. missing_port
*   C. reference_name_case
*   D. All of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Addressed by DMM autofix rules. |
| $${\color{red}\text{B}}$$ | Addressed by DMM autofix rules. |
| $${\color{red}\text{C}}$$ | Addressed by DMM autofix rules. |
| $${\color{lightgreen}\text{D}}$$ | **All of the above** structural mismatch scenarios can be automatically patched via `set_dmm_config -autofix`. |

</details>

---

**Question 13**: Fusion Compiler can identify and act on mismatches between

*   A. Library definitions and instantiations
*   B. RTL top-level instantiations and sub-designs
*   C. Both a & b
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Mismatches between library pin definitions and netlist instances are detected. |
| $${\color{red}\text{B}}$$ | Port mismatches across hierarchical sub-block boundaries are detected. |
| $${\color{lightgreen}\text{C}}$$ | FC identifies and resolves discrepancies **both between libraries and instances and across hierarchical RTL modules**. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 14**: When missing a logical reference, auto_fix DMM configuration creates

*   A. Soft macro
*   B. Hard macro
*   C. Physical black box
*   D. Both a & c

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Incomplete on its own. |
| $${\color{red}\text{B}}$$ | Hard macros require concrete physical timing and layout data. |
| $${\color{red}\text{C}}$$ | Incomplete on its own. |
| $${\color{lightgreen}\text{D}}$$ | DMM can automatically stub an unresolved logical reference by creating a **soft macro or a physical black box** boundary. |

</details>

---

**Question 15**: The maximum length of any library or block name is \____

*   A. 255
*   B. 127
*   C. 1023
*   D. 63

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | In the Synopsys NDM database format, library and block container identifiers have a maximum length limit of **255 characters**. |
| $${\color{red}\text{B}}$$ | Lower than the tool specification limit. |
| $${\color{red}\text{C}}$$ | 1023 is not the container name constraint. |
| $${\color{red}\text{D}}$$ | Lower than the tool specification limit. |

</details>

---

**Question 16**: Ports are the inputs and outputs of the \____

*   A. Block
*   B. Standard cell
*   C. Nets
*   D. All of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | By definition in Synopsys tools, **ports** represent the external primary input, output, or inout connections of a **block/design**. |
| $${\color{red}\text{B}}$$ | Connections on standard cells are pins, not ports. |
| $${\color{red}\text{C}}$$ | Nets are interconnect wiring lines, not terminal objects. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 17**: Pins are the inputs and outputs of the \____

*   A. Block
*   B. Standard cell
*   C. Design
*   D. All of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Inputs/outputs of top-level blocks are ports. |
| $${\color{lightgreen}\text{B}}$$ | **Pins** are the connection terminals of instantiated leaf objects, such as **standard cells** and macros. |
| $${\color{red}\text{C}}$$ | Top-level design boundaries expose ports. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 18**: Application Options control the \_______ of FC’s commands

*   A. Behavior
*   B. Features
*   C. Both a & b
*   D. Timing constraints

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Incomplete on its own. |
| $${\color{red}\text{B}}$$ | Incomplete on its own. |
| $${\color{lightgreen}\text{C}}$$ | Application options (`set_app_options`) configure the underlying **behavior and optional features** of Fusion Compiler algorithms. |
| $${\color{red}\text{D}}$$ | Timing constraints are governed by SDC commands, not app options. |

</details>

---

**Question 19**: Application options use the following naming convention

*   A. category[.sub_category].option_name
*   B. category_subcategory_option_name
*   C. option_name.category[.subcategory]
*   D. None

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | FC application options follow a hierarchical dot-separated namespace format: **`category[.sub_category].option_name`** (e.g., `place.coarse.max_density`). |
| $${\color{red}\text{B}}$$ | Uses underscores instead of tool-standard dot notation. |
| $${\color{red}\text{C}}$$ | Inverted order of naming hierarchy. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 20**: Application options have \_____ scope

*   A. Block
*   B. Global
*   C. Either a or b
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Incomplete; some options are globally scoped. |
| $${\color{red}\text{B}}$$ | Incomplete; many options are block-level. |
| $${\color{lightgreen}\text{C}}$$ | Application options in Fusion Compiler are scoped as **either block-level or global-level**. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 21**: \____ app_option values are saved with the block

*   A. Global scoped
*   B. Block scoped
*   C. Both a & b
*   D. None

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Global-scoped options apply session-wide and are never written into the block database. |
| $${\color{lightgreen}\text{B}}$$ | **Block-scoped** application options are serialized and stored directly within the NDM block container upon running `save_block`. |
| $${\color{red}\text{C}}$$ | Global options are excluded from storage. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 22**: Global-scoped application options \___

*   A. Apply to all blocks loaded in the current tool session
*   B. Are not saved with the block(s)
*   C. Can be specified before any block is opened
*   D. All of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Valid characteristic of global options. |
| $${\color{red}\text{B}}$$ | Valid characteristic of global options. |
| $${\color{red}\text{C}}$$ | Valid characteristic of global options. |
| $${\color{lightgreen}\text{D}}$$ | **All of the above** statements are true regarding global application options. |

</details>

---

**Question 23**: Block-scoped application options \____

*   A. Apply to the current block
*   B. Are saved with the block
*   C. Are persistent across tool sessions
*   D. All of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | True: applies specifically to the active target block. |
| $${\color{red}\text{B}}$$ | True: committed to disk with the block. |
| $${\color{red}\text{C}}$$ | True: restored automatically whenever the block is reopened. |
| $${\color{lightgreen}\text{D}}$$ | **All of the above** statements are true regarding block-scoped options. |

</details>

---

**Question 24**: search_path application variable should \____

*   A. To be set again after restarting Fusion Compiler
*   B. Never saved with the block
*   C. Saved with the block
*   D. Both a & b

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | True, but incomplete on its own. |
| $${\color{red}\text{B}}$$ | True, but incomplete on its own. |
| $${\color{red}\text{C}}$$ | Incorrect; environment search paths are not saved inside design blocks. |
| $${\color{lightgreen}\text{D}}$$ | **Both a and b are correct**: `search_path` is a Tcl environment variable that is never saved within design blocks and must be initialized upon restarting the tool. |

</details>

---

**Question 25**: What is the limit on the name length for design objects such as nets, cells, pins, modules, and terminals

*   A. 255
*   B. 1023
*   C. 511
*   D. No limit

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | 255 applies to library and block container names. |
| $${\color{red}\text{B}}$$ | Often assumed based on legacy shells, but not a hard limit in modern NDM object naming. |
| $${\color{red}\text{C}}$$ | Incorrect numeric boundary. |
| $${\color{lightgreen}\text{D}}$$ | Fusion Compiler imposes **no architectural limit** on the string length of individual netlist design objects (nets, cells, pins, modules, and terminals). |

</details>

---

**Question 26**: Which of the following is user-defined objects

*   A. Clock
*   B. Ports
*   C. Cells
*   D. Pin

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | A **clock** is an abstract timing constraint object created explicitly by the designer via `create_clock`. |
| $${\color{red}\text{B}}$$ | Derived directly from the hardware design netlist/RTL interface. |
| $${\color{red}\text{C}}$$ | Instantiated physical/logical design entities. |
| $${\color{red}\text{D}}$$ | Standard cell boundary connections. |

</details>

---

**Question 27**: FC provides a full set of object classes and associated Tcl commands to create, remove, query, and modify all primary design data such as

*   A. Logical and Physical objects
*   B. Reference library objects
*   C. Timing data
*   D. All of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Netlist cells, nets, and physical shapes. |
| $${\color{red}\text{B}}$$ | Reference library cells, pins, and attributes. |
| $${\color{red}\text{C}}$$ | Clocks, scenarios, modes, and timing paths. |
| $${\color{lightgreen}\text{D}}$$ | **All of the above** classes are fully supported within the unified data model. |

</details>

---

**Question 28**: Rule based query should be turned on when \_____

*   A. Reading files that require translation
*   B. Resolve object name mismatches
*   C. Both a & b
*   D. None

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | True, but incomplete. |
| $${\color{red}\text{B}}$$ | True, but incomplete. |
| $${\color{lightgreen}\text{C}}$$ | Rule-based queries dynamically match object names during **file translation and structural naming mismatch resolution**. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 29**: How to allow the same constraints to be applied to a WVGTECH (unmapped) design

*   A. Using pin name synonyms definitions
*   B. Using module definitions
*   C. Both a & b
*   D. None

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | **Pin name synonyms** map generic GTECH pin nomenclature to targeted standard cell pin names, allowing uniform constraint application. |
| $${\color{red}\text{B}}$$ | Module definitions establish hierarchy, not pin-level functional equivalencies. |
| $${\color{red}\text{C}}$$ | Incorrect. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 30**: bounding_box attribute allows \____

*   A. Direct query coordinates
*   B. Filtering of the involved coordinates
*   C. Individual point of the bounding box
*   D. Both a & b

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | True, but incomplete. |
| $${\color{red}\text{B}}$$ | True, but incomplete. |
| $${\color{red}\text{C}}$$ | The attribute returns a bounding rectangle coordinate pair, not isolated scalar points. |
| $${\color{lightgreen}\text{D}}$$ | **Both a and b are correct**: `bounding_box` enables direct querying of object coordinates and spatial coordinate filtering. |

</details>

---

**Question 31**: which of the following is correct compile_fusion steps

*   A. initial_map -> logic_opt -> intial_place -> intial_drc -> initial_opto -> final_place -> final_drc
*   B. initial_map -> logic_opt -> intial_place -> initial_opto -> intial_drc -> final_place -> final_opto
*   C. initial_map-> intial_place -> logic_opt -> intial_drc -> initial_opto -> final_place -> final_opto
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Incorrect; the flow ends with `final_opto`, not `final_drc`. |
| $${\color{red}\text{B}}$$ | Misplaces `initial_drc` after `initial_opto` and misspells stages (`intial_*`, `logic_opt`). |
| $${\color{red}\text{C}}$$ | Places `initial_place` before `logic_opto`, which is fundamentally out of order. |
| $${\color{lightgreen}\text{D}}$$ | **None of the above** represents the true step sequence. The official, non-misspelled sequence is: `initial_map` $\rightarrow$ `logic_opto` $\rightarrow$ `initial_place` $\rightarrow$ `initial_drc` $\rightarrow$ `initial_opto` $\rightarrow$ `final_place` $\rightarrow$ `final_opto`. |

</details>

---

**Question 32**: ICG and MV cells are inserted in \___ step of compile_fusion

*   A. logic_opto
*   B. initial_drc
*   C. initial_map
*   D. initial_place

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | `logic_opto` handles boundary/boolean restructuring after mapping. |
| $${\color{red}\text{B}}$$ | `initial_drc` focuses on high-fanout buffering and design rules. |
| $${\color{lightgreen}\text{C}}$$ | **`initial_map`** maps RTL gating logic and UPF power strategies into instantiated Integrated Clock-Gating (ICG) and Multi-Voltage (MV) cells. |
| $${\color{red}\text{D}}$$ | Placement occurs after structural cell insertion. |

</details>

---

**Question 33**: By default, the design is ready to run which stage after we ran the command “compile_fusion”?

*   A. Place stage
*   B. CTS stage
*   C. route_auto
*   D. route_opt

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Placement is already executed internally within `compile_fusion`. |
| $${\color{lightgreen}\text{B}}$$ | Completing `compile_fusion` leaves cells placed, sized, and timing-optimized, making the design ready for **Clock Tree Synthesis (`clock_opt`)**. |
| $${\color{red}\text{C}}$$ | Routing requires a synthesized clock tree first. |
| $${\color{red}\text{D}}$$ | Post-route optimization happens after detailed routing. |

</details>

---

**Question 34**: Autofloor plan is enabled by defulat during \___ step of compile_fusion

*   A. logic_opto
*   B. initial_drc
*   C. initial_map
*   D. initial_place

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | In `compile_fusion`, automatic default floorplanning initializes during **`logic_opto`** if no prior physical floorplan exists, establishing dimensions for upcoming placement. |
| $${\color{red}\text{B}}$$ | Follows placement. |
| $${\color{red}\text{C}}$$ | RTL elaboration and technology mapping occur prior to auto-floorplan synthesis. |
| $${\color{red}\text{D}}$$ | Placement relies on the floorplan created in earlier stages. |

</details>

---

**Question 35**: How to to query the state of the block

*   A. Using report_optimization_history
*   B. Using report_design
*   C. Using report_qor
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | **`report_optimization_history`** specifically tracks and queries the execution state, completed optimization stages, and flow progression of the block. |
| $${\color{red}\text{B}}$$ | Reports design statistics, hierarchy, and boundary characteristics. |
| $${\color{red}\text{C}}$$ | Reports timing, area, power, and DRC metrics. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 36**: Which DFT flow FC does not support?

*   A. Pre-compile
*   B. Post-compile
*   C. Post place_opt
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Supported: RTL scan architecture planning. |
| $${\color{red}\text{B}}$$ | Supported: Gate-level scan chain insertion. |
| $${\color{lightgreen}\text{C}}$$ | **Post place_opt** scan insertion is not a supported flow methodology; scan chains must be defined/stitched during early compile/placement stages to avoid disrupting physical convergence. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 37**: When the design can contain unmapped cells after the compile_fusion command

*   A. Missing input and output ports
*   B. Missing the required cells in the library
*   C. User-specified restrictions on the required library cells
*   D. Only b&c

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Missing ports cause link/connectivity issues, not generic mapping failures. |
| $${\color{red}\text{B}}$$ | If functional equivalents do not exist in target libraries, GTECH cells remain unmapped. |
| $${\color{red}\text{C}}$$ | Heavy restrictions (`set_lib_cell_purpose -include none` or `dont_touch`) prevent mapping. |
| $${\color{lightgreen}\text{D}}$$ | **Only b & c** describe conditions that prevent generic logic from mapping to target gates. |

</details>

---

**Question 38**: Use of loading nxtgrd or TLUPlus Parasitic RC Models

*   A. Used for parasitic extraction
*   B. Used for parasitic net RC modeling
*   C. Used for pattern matching
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Full extraction is the broader signoff process. |
| $${\color{lightgreen}\text{B}}$$ | These models supply technological dielectric, capacitance, and resistance lookup tables **used for parasitic net RC modeling** during physical optimization. |
| $${\color{red}\text{C}}$$ | Unrelated to pattern matching. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 39**: The technology file does not contain the following information

*   A. Min spacing constraints
*   B. Routing direction
*   C. Minimum area constraints
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Present in technology files. |
| $${\color{lightgreen}\text{B}}$$ | Preferred **routing direction** is a track design attribute set in the floorplan/NDM design, not an inherent geometric foundry constraint defined in the technology file (`.tf`). |
| $${\color{red}\text{C}}$$ | Present in technology files. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 40**: Routing directions depends on \____

*   A. Technology file
*   B. Tluplus files
*   C. Physical standard cells
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | While tech files define layer characteristics, layer pin access requirements depend on standard cell layout. |
| $${\color{red}\text{B}}$$ | Defines parasitic RC tables. |
| $${\color{lightgreen}\text{C}}$$ | In modern standard cell design, metal track orientation and preferred routing directions directly accommodate the pin layout geometry of the **physical standard cells**. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 41**: An SVF file contains guidance on the following

*   A. Multibit transformations
*   B. Duplicate and merged registers
*   C. Fusion Compiler environment
*   D. All of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Captured in the SVF for formal verification. |
| $${\color{red}\text{B}}$$ | Captured in the SVF for formal verification. |
| $${\color{red}\text{C}}$$ | Tool environment setup is captured for Formality. |
| $${\color{lightgreen}\text{D}}$$ | **All of the above** non-functional logic operations are captured in the Formality SVF file. |

</details>

---

**Question 42**: initial_place step does the following

*   A. Performs logic delay optimization and wire-length driven placement
*   B. Performs buffering aware timing driven placement
*   C. Builds the high-fanout buffer trees
*   D. Incremental HFN buffering

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Wirelength-only placement does not account for virtual buffering. |
| $${\color{lightgreen}\text{B}}$$ | `initial_place` executes coarse placement while taking virtual buffer insertion and timing constraints into account (**buffering-aware timing-driven placement**). |
| $${\color{red}\text{C}}$$ | Dedicated buffer tree synthesis occurs in `initial_drc`. |
| $${\color{red}\text{D}}$$ | Occurs later in DRC cleanup. |

</details>

---

**Question 43**: initial_opto step does the following

*   A. Performs auto-floorplanning
*   B. Builds the high-fanout buffer trees
*   C. Scan chains architected and stitched
*   D. Performs final, incremental timing- and congestion-driven placement

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Occurs in early stages. |
| $${\color{red}\text{B}}$$ | Executed in `initial_drc`. |
| $${\color{lightgreen}\text{C}}$$ | During `initial_opto`, **scan chains are architected, partitioned, and stitched** across the design to match the placed logic topology. |
| $${\color{red}\text{D}}$$ | Final incremental placement refinement occurs in `final_place`. |

</details>

---

**Question 44**: How to restrict the usage of specific DesignWare components

*   A. Using set_lib_cell_purpose
*   B. Using set_synlib_dont_use
*   C. Using set_dont_use
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Targets library standard cells, not synthetic DesignWare parts. |
| $${\color{lightgreen}\text{B}}$$ | **`set_synlib_dont_use`** prevents the synthesis compiler from inferring or utilizing specified DesignWare/synthetic library parts. |
| $${\color{red}\text{C}}$$ | Deprecated/standard cell command. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 45**: initial_drc step does the following

*   A. Performs auto-floorplanning
*   B. Builds the high-fanout buffer trees
*   C. Scan chains architected and stitched
*   D. Performs final, incremental timing- and congestion-driven placement

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Occurs early in `logic_opto`. |
| $${\color{lightgreen}\text{B}}$$ | **`initial_drc`** resolves electrical design rule violations (max_transition, max_capacitance) primarily by **building high-fanout buffer trees (HFNS)**. |
| $${\color{red}\text{C}}$$ | Occurs in `initial_opto`. |
| $${\color{red}\text{D}}$$ | Occurs in final placement stages. |

</details>

---

**Question 46**: what does CLIB NDM cell library contain?

*   A. Logic/timing/power data of library cell
*   B. Physical data
*   C. Design & layout data
*   D. All of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Captured in logical `.db` views. |
| $${\color{red}\text{B}}$$ | Captured in `.frame` physical views. |
| $${\color{red}\text{C}}$$ | Pin access geometries and blockage structures. |
| $${\color{lightgreen}\text{D}}$$ | An NDM CLIB unifies **all logical, timing, power, physical, and layout data** into a single library format. |

</details>

---

**Question 47**: What are the tools usable to create logic library .db

*   A. Library Compiler
*   B. Library Manager
*   C. Fusion Compiler
*   D. A or b

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Dedicated standalone compiler for `.db`. |
| $${\color{red}\text{B}}$$ | Comprehensive library management and database tool. |
| $${\color{red}\text{C}}$$ | P&R implementation tool; consumes rather than creates standalone `.db`. |
| $${\color{lightgreen}\text{D}}$$ | Both **Library Compiler (LC) and Library Manager (LM)** can compile source Liberty (`.lib`) files into `.db`. |

</details>

---

**Question 48**: What does a liberty model .lib contain?

*   A. Logical DRC constraints
*   B. Non linear delay model for timing
*   C. CCS timing models
*   D. All of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Defines max_transition and max_capacitance. |
| $${\color{red}\text{B}}$$ | Defines table lookup NLDM delay and transition models. |
| $${\color{red}\text{C}}$$ | Defines current-source based CCS timing and noise models. |
| $${\color{lightgreen}\text{D}}$$ | **All of the above** modeling data can be present inside modern `.lib` characterization files. |

</details>

---

**Question 49**: What makes CLIB specific to a technology?

*   A. Characterization is done for that technology
*   B. CLIBS are associated with a specific .tf file
*   C. Cell height and width are captured based on units associated with particular technology
*   D. The .lib captures the technology node clearly

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Liberty characterization focuses on electrical behavior, but technology uniqueness in NDM relies on physical binding. |
| $${\color{lightgreen}\text{B}}$$ | An NDM CLIB is strictly bound to and compiled with a **specific technology file (`.tf`)**, which locks it to the physical layer stack. |
| $${\color{red}\text{C}}$$ | Dimensions are geometrical values dependent on the tech rules. |
| $${\color{red}\text{D}}$$ | `.lib` files can omit process metal details. |

</details>

---

**Question 50**: Why do I need a frame view when there is a GDS/Cell view

*   A. .frame captures data relevant only for P&R
*   B. .frame captures minimal data that optimizes usage of process memory and runtime
*   C. There is no need for .frame
*   D. A & b

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Frame views omit transistor details, exposing only pins and blockages. |
| $${\color{red}\text{B}}$$ | A smaller footprint improves memory usage and throughput. |
| $${\color{red}\text{C}}$$ | Frame views are essential for efficient place-and-route. |
| $${\color{lightgreen}\text{D}}$$ | **Both a and b are correct**: Frame views contain only data required for P&R, optimizing memory consumption and runtimes. |

</details>

---

**Question 51**: When CLIB is used in Fusion compiler, which of the below files are not needed?

*   A. db
*   B. Frame
*   C. a & b
*   D. Need both

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Incomplete. |
| $${\color{red}\text{B}}$$ | Incomplete. |
| $${\color{lightgreen}\text{C}}$$ | Because the NDM CLIB already encapsulates both logical timing (`.db`) and physical layout (`.frame`), **neither separate .db nor .frame files are needed**. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 52**: If the library name in the .db and .ndm is different. Querying commands such as get_libs/get_lib_* command

*   A. Can still use the name as in .db and .ndm interchangeably
*   B. Can use only the name as in .db
*   C. Can use only name as in .ndm
*   D. Can't use either of them

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | Fusion Compiler maintains internal alias mappings between legacy Liberty header names (`.db`) and NDM container names, allowing them to be used **interchangeably**. |
| $${\color{red}\text{B}}$$ | Incorrect limitation. |
| $${\color{red}\text{C}}$$ | Incorrect limitation. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 53**: If we don't have a pre-assembled CLIB file, what can you do to proceed with synthesis using FC?

*   A. Use library manager to create a CLIB
*   B. Use .db, .frame and ASCII tech file to create CLIB on the fly
*   C. Either a or b
*   D. Use library compiler to pre-assemble CLIB

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Valid offline generation route. |
| $${\color{red}\text{B}}$$ | Valid automated on-the-fly flow inside FC. |
| $${\color{lightgreen}\text{C}}$$ | You can proceed by **either creating a CLIB via Library Manager beforehand or letting FC assemble it on the fly** from source files. |
| $${\color{red}\text{D}}$$ | Library Compiler does not compile physical frame views into CLIBs. |

</details>

---

**Question 54**: If you create the clib on the fly..

*   A. For subsequent stages after synthesis, discard clib and use clib preassembled using LM
*   B. Continue with synthesis flow but database can't be saved
*   C. CLIB created on the fly can be considered equivalent to CLIB preassembled using LM
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Discarding is unnecessary because the CLIB is production-grade. |
| $${\color{red}\text{B}}$$ | Databases built with on-the-fly CLIBs save without issue. |
| $${\color{lightgreen}\text{C}}$$ | An **on-the-fly CLIB is functionally identical and fully equivalent** to one built in Library Manager. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 55**: How should .frame and .lib be introduced to FC when the CLIB is created on the fly?

*   A. Provide both in the link_library application variable
*   B. Provide both in the create_lib -ref_libs
*   C. Provide .frame in create_lib -ref_libs and .db in the link_library application variable
*   D. Provide .db in create_lib -ref_libs and .frame in link_library application variable

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Frame files cannot be loaded via `link_library`. |
| $${\color{red}\text{B}}$$ | `.db` logic files cannot be directly listed in `-ref_libs`. |
| $${\color{lightgreen}\text{C}}$$ | In on-the-fly assembly, physical layout references (**`.frame`**) are passed to `create_lib -ref_libs`, while logical timing models (**`.db`**) are supplied via `link_library`. |
| $${\color{red}\text{D}}$$ | Swaps the correct input interfaces. |

</details>

---

**Question 56**: While auto-assembling CLIBs if FC doesn't find the .frame provided in create_lib -ref_libs

*   A. FC errors out immediately
*   B. FC has an app option which can be set so that it can look at a central location as a back up
*   C. FC first looks at the central location before considering assembling it locally
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | FC checks fallback search paths before throwing a fatal error. |
| $${\color{red}\text{B}}$$ | Secondary to tool priority. |
| $${\color{lightgreen}\text{C}}$$ | When configured for shared library usage, **FC first inspects the designated central library cache/repository** to locate pre-existing frames before falling back to local assembly. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 57**: create_clock is a

*   A. Mode specific constraint
*   B. Corner specific constraint
*   C. Scenario specific constraint
*   D. Global constraint

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | Clocks represent functional waveforms and periods associated directly with a design **mode** (e.g., Mission, Scan, Test). |
| $${\color{red}\text{B}}$$ | Corners define physical PVT parameters, not clock periods. |
| $${\color{red}\text{C}}$$ | A scenario pairs a mode with a corner, but the clock definition belongs to the mode. |
| $${\color{red}\text{D}}$$ | Clocks vary across modes and are not uniform global constants. |

</details>

---

**Question 58**: set_voltage is a

*   A. Mode specific constraint
*   B. Corner specific constraint
*   C. Scenario specific constraint
*   D. Global constraint

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Voltage is a physical condition, not a functional operational mode. |
| $${\color{lightgreen}\text{B}}$$ | Power supply operating voltage is tied to physical operating **corners** (PVT). |
| $${\color{red}\text{C}}$$ | Handled at the corner level. |
| $${\color{red}\text{D}}$$ | Can differ across multiple multi-voltage power domains and PVT corners. |

</details>

---

**Question 59**: set_input/output_delay and set_driving_cell are

*   A. Mode specific constraint
*   B. Corner specific constraint
*   C. Scenario specific constraint
*   D. Global constraint

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Driving cell characteristics depend on external operating corner conditions. |
| $${\color{red}\text{B}}$$ | I/O delays depend on external functional clock cycles. |
| $${\color{lightgreen}\text{C}}$$ | External delays and driving cells depend on both functional frequency and PVT drive characteristics, making them **scenario-specific constraints**. |
| $${\color{red}\text{D}}$$ | Not uniform across the design. |

</details>

---

**Question 60**: set_ideal_network is a

*   A. Mode specific constraint
*   B. Corner specific constraint
*   C. Scenario specific constraint
*   D. Global constraint

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Primarily acts across the entire object. |
| $${\color{red}\text{B}}$$ | Not governed by PVT variations. |
| $${\color{red}\text{C}}$$ | Applies beyond a single scenario. |
| $${\color{lightgreen}\text{D}}$$ | **`set_ideal_network`** sets an attribute directly on structural ports/pins/nets, treating that network as ideal **globally** across all modes and corners. |

</details>

---

**Question 61**: When you read mixed mode constraints and used the tool to remove duplicate constraints, what command do you use to verify the constraints as understood by the tool?

*   A. report_scenarios
*   B. write_script
*   C. check_timing
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Reports the status of scenario configurations, not SDC commands. |
| $${\color{lightgreen}\text{B}}$$ | **`write_script`** (or `write_script -format sdc`) exports the consolidated, deduplicated SDC constraints stored in memory for verification. |
| $${\color{red}\text{C}}$$ | Identifies missing constraints or unconstrained paths rather than dumping active constraints. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 62**: How to report single worst setup timing path from each & every active corner/mode/scenario?

*   A. report_timing -report_by corner|mode|scenario|group
*   B. report_timing -report_by corner -corners *
*   C. report_timing -report_by scenario -scenario * {
*   D. Run (a) and (b) one after the other

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | Using **`report_timing -report_by corner|mode|scenario|group`** systematically iterates and isolates the single worst timing path across each specified category. |
| $${\color{red}\text{B}}$$ | Reports strictly by corners, missing isolated mode/scenario breakdowns. |
| $${\color{red}\text{C}}$$ | Contains broken syntax (`{`). |
| $${\color{red}\text{D}}$$ | Unnecessary repetition. |

</details>

---

**Question 63**: If a design has multiple scenarios compile_fusion will optimize which scenario?

*   A. The last defined scenario
*   B. All scenarios
*   C. All active scenarios
*   D. First defined scenario

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Ignores concurrent MCMM optimization. |
| $${\color{red}\text{B}}$$ | Inactive scenarios are ignored during optimization. |
| $${\color{lightgreen}\text{C}}$$ | Fusion Compiler's multi-corner multi-mode (MCMM) engine concurrently optimizes **all active scenarios** (`active == true`). |
| $${\color{red}\text{D}}$$ | Ignores concurrent MCMM optimization. |

</details>

---

**Question 64**: What is the way to understand the active/in-active status of scenarios?

*   A. report_scenarios
*   B. get_scenarios -filter "active"
*   C. a or b
*   D. Only a

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Generates a readable summary table of active/inactive configurations. |
| $${\color{red}\text{B}}$$ | Programmatically queries scenarios matching the active filter. |
| $${\color{lightgreen}\text{C}}$$ | You can use **either `report_scenarios` or `get_scenarios -filter "active"`** to verify scenario status. |
| $${\color{red}\text{D}}$$ | Omits the programmatic method. |

</details>

---

**Question 65**: In what format is pocv sigma available?

*   A. LVF format
*   B. Library side file
*   C. a or b
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Embedded directly within standard cell Liberty Variation Format libraries. |
| $${\color{red}\text{B}}$$ | Loaded via external side files. |
| $${\color{lightgreen}\text{C}}$$ | POCV sigma coefficients can be provided via **either embedded LVF Liberty format or an external library side file**. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 66**: What is the advantage of computing infeasible path?

*   A. Identifies paths affected by unreasonable input/output constraints
*   B. Identifies missing false/multicycle path constraints
*   C. Applies path margins to infeasible paths and prevents tool from spending runtime on such paths
*   D. All of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Highlights unrealistic external budgets. |
| $${\color{red}\text{B}}$$ | Identifies unconstrained false or multicycle paths. |
| $${\color{red}\text{C}}$$ | Prevents wasted runtime and area on paths that cannot be closed. |
| $${\color{lightgreen}\text{D}}$$ | **All of the above** are direct benefits of early infeasible path detection. |

</details>

---

**Question 67**: What additional information is shown in report_timing when used with -variation option?

*   A. sensit values
*   B. Mean values
*   C. RMS delta delay
*   D. All of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Shows sensitivity values per stage. |
| $${\color{red}\text{B}}$$ | Shows mean delay components. |
| $${\color{red}\text{C}}$$ | Shows statistical standard deviation / RMS delays. |
| $${\color{lightgreen}\text{D}}$$ | **All of the above** variation parameters are exposed when running `report_timing -variation`. |

</details>

---

**Question 68**: From where does the tool use the distance-based derates?

*   A. LVF files
*   B. Side files
*   C. a or b
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Distance-based variation can be modeled in advanced LVF libraries. |
| $${\color{red}\text{B}}$$ | Distance derate tables are frequently supplied via dedicated side files (`read_ocv`). |
| $${\color{lightgreen}\text{C}}$$ | Distance-based derates can be sourced from **either LVF models or external side files**. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 69**: set_pvt_configuration command can be used for what purpose?

*   A. To define the scenarios usable for synthesis
*   B. To define the best case and worst case PVT settings
*   C. To provide the settings for selectively loading the libraries thus optimizing for memory and runtime
*   D. All of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Scenarios are created with `create_scenario`. |
| $${\color{red}\text{B}}$$ | Operating conditions define best/worst settings. |
| $${\color{lightgreen}\text{C}}$$ | **`set_pvt_configuration`** controls PVT configuration mapping to **selectively load only necessary library characterization tables**, reducing host memory footprint and runtime. |
| $${\color{red}\text{D}}$$ | Incorrect generalization. |

</details>

---

**Question 70**: What is the best way to specify the PVT operating conditions?

*   A. Using set_process_number, set_voltage, set_temperature
*   B. set_operating_conditions
*   C. A is recommended over b, but either can be used
*   D. B is recommended over a

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Explicit parameters represent the preferred methodology. |
| $${\color{red}\text{B}}$$ | Monolithic legacy approach. |
| $${\color{lightgreen}\text{C}}$$ | **Using distinct commands (`set_temperature`, `set_voltage`, `set_process_number`) is recommended over legacy `set_operating_conditions`**, though both are accepted. |
| $${\color{red}\text{D}}$$ | Inverts tool recommendations. |

</details>

---

**Question 71**: If the PVT settings user provides doesn’t match the PVT characteristics of the libraries..

*   A. Tool errors out
*   B. Tool finds the nearest VT match
*   C. We can tune to tool for behavior described in a or b
*   D. Tool will synthesize for an assume PVT setting

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Can occur, depending on settings. |
| $${\color{red}\text{B}}$$ | Can occur, depending on interpolation settings. |
| $${\color{lightgreen}\text{C}}$$ | FC provides application options to **tune the behavior to either error out immediately or interpolate/snap to the nearest library match**. |
| $${\color{red}\text{D}}$$ | Arbitrary assumptions without configuration are not permitted. |

</details>

---

**Question 72**: What is the full form of CCD

*   A. Clock correlation & data optimization
*   B. Concurrent clock & data optimization
*   C. Compile clock & data
*   D. None

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Incorrect expansion. |
| $${\color{lightgreen}\text{B}}$$ | **CCD** stands for **Concurrent Clock and Data** optimization. |
| $${\color{red}\text{C}}$$ | Incorrect expansion. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 73**: CCD technique is same as

*   A. Creating Bounds Clock and Data path cells
*   B. Useful skew
*   C. HFNS
*   D. Data path optimization

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Bound creation is a placement clustering technique. |
| $${\color{lightgreen}\text{B}}$$ | CCD adjusts clock insertion delays across registers to borrow slack from non-critical paths to fix timing violations, which is mathematically and functionally **useful skew**. |
| $${\color{red}\text{C}}$$ | High-fanout synthesis buffers high-load nets, not skew balancing. |
| $${\color{red}\text{D}}$$ | Incomplete; CCD optimizes both clock and data concurrently. |

</details>

---

**Question 74**: When Useful Skew Computations Occur

*   A. initial_opto
*   B. final_opto
*   C. final_place
*   D. Both a&b

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Useful skew is initially calculated and budgeted during `initial_opto`. |
| $${\color{red}\text{B}}$$ | Useful skew targets are refined after final placement during `final_opto`. |
| $${\color{red}\text{C}}$$ | Skew updates are calculated during optimization passes, not placement steps. |
| $${\color{lightgreen}\text{D}}$$ | **Both a and b are correct**: Useful skew computations and adjustments occur during `initial_opto` and `final_opto`. |

</details>

---

**Question 75**: How FC handles useful skew for macros?

*   A. Simply defines critical macro skew banks
*   B. Separate skew optimization algorithm (before CCD opt)
*   C. Both a & b
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Defines critical macro skew banks to bound insertion delay. |
| $${\color{red}\text{B}}$$ | Executes an independent macro skewing algorithm before general standard-cell CCD. |
| $${\color{lightgreen}\text{C}}$$ | **Both a and b are correct**: FC defines dedicated macro skew banks and uses a separate, specialized optimization pass for macro interfaces prior to standard CCD. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 76**: Which of the below path groups are addressed during CCD?

*   A. Works on non-memory paths
*   B. Works on memory to non-memory paths
*   C. Works on memory paths
*   D. All of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Standard register-to-register paths. |
| $${\color{red}\text{B}}$$ | SRAM-to-register interface paths. |
| $${\color{red}\text{C}}$$ | Pure memory-to-memory datapath buses. |
| $${\color{lightgreen}\text{D}}$$ | CCD operates across **all of the above** registered path groups. |

</details>

---

**Question 77**: If you specify a path group name without a scenario name during CCD Optimization

*   A. Only the path group in the specified scenario is skipped
*   B. All path groups with the name specified from all scenarios are skipped
*   C. Both a & b
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Requires an explicit scenario name. |
| $${\color{lightgreen}\text{B}}$$ | Omitting a scenario qualifier applies the exclusion globally: **all path groups with that name across every active scenario are skipped**. |
| $${\color{red}\text{C}}$$ | Mutually exclusive. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 78**: If you specify a path group name with a scenario name during CCD Optimization

*   A. Only the path group in the specified scenario is skipped
*   B. All path groups with the name specified from all scenarios are skipped
*   C. Both a & b
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | Explicitly defining the scenario targets the exclusion strictly to **that specified path group within that specific scenario**. |
| $${\color{red}\text{B}}$$ | Applies when no scenario is specified. |
| $${\color{red}\text{C}}$$ | Mutually exclusive. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 79**: Which command prints slacks of critical endpoints and allows you to analyze the timing paths of previous and following stages ?

*   A. report_ccd_timing
*   B. report_timing
*   C. check_ccd_timing
*   D. get_timing

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | **`report_ccd_timing`** evaluates multi-stage register pipeline chains, displaying arrival latencies, useful skew targets, and adjacent-stage slacks. |
| $${\color{red}\text{B}}$$ | Reports isolated timing paths without pipeline chain context. |
| $${\color{red}\text{C}}$$ | Diagnostic sanity checker, not a detailed timing path reporter. |
| $${\color{red}\text{D}}$$ | Non-existent command. |

</details>

---

**Question 80**: Default CCD Optimization performs ______

*   A. Improving "data path hold time" by using method useful skew
*   B. Improving "data path setup time" by using method useful skew
*   C. Improving "clock path setup time" by using method useful skew
*   D. Improving "clock path hold time" by using method useful skew

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Hold violations are traditionally repaired post-CTS via delay buffer insertion. |
| $${\color{lightgreen}\text{B}}$$ | Default CCD optimization focuses on **improving data path setup time using useful skew** without violating hold constraints. |
| $${\color{red}\text{C}}$$ | Clock paths are the mechanism, not the target being closed. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 81**: Why always-on buffers should be added ?

*   A. To allow always-on routing for MV designs
*   B. To disable always-on CTS for MV designs
*   C. To allow always-on CTS for MV designs
*   D. To disable always-on routing for MV designs

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Always-on refers to cell power rail connectivity, not routing topology. |
| $${\color{red}\text{B}}$$ | Always-on buffers enable CTS, rather than disabling it. |
| $${\color{lightgreen}\text{C}}$$ | In multi-voltage power-gated designs, **always-on buffers enable continuous clock tree synthesis (CTS)** across sleep domains without losing clock integrity when a power domain shuts down. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 82**: By default, CCD skews for ______ timing

*   A. Only internal registers/FFs
*   B. All registers including boundary FFs
*   C. Only boundary FFs
*   D. None

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Boundary FFs are kept stable under custom options, but default flows cover the full registered netlist. |
| $${\color{lightgreen}\text{B}}$$ | By default, the CCD engine is globally active across **all registers, including boundary flip-flops**, borrowing slack wherever constraints permit. |
| $${\color{red}\text{C}}$$ | Skewing only boundary registers would ignore internal timing bottlenecks. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 83**: How useful skew for macros works

*   A. Input registers can be preponed to avoid degrading input paths
*   B. Input registers can be postponed to avoid degrading input paths
*   C. Output registers can be preponed to improve output paths
*   D. None

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | Macro useful skewing **prepones (advances/shortens latency of) input registers** driving into memories to meet setup times without degrading external data input paths. |
| $${\color{red}\text{B}}$$ | Postponing input capture worsens setup margins on incoming paths. |
| $${\color{red}\text{C}}$$ | Preponing output registers restricts downstream data setup budgets. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 84**: Useful skew for macros improves ___ macro bank paths without degrading any _____ macro bank paths

*   A. Output, output
*   B. Input, output
*   C. Input, input
*   D. Output, input

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Incorrect combination. |
| $${\color{red}\text{B}}$$ | Incorrect combination. |
| $${\color{red}\text{C}}$$ | Incorrect combination. |
| $${\color{lightgreen}\text{D}}$$ | The specialized macro algorithm shifts latency to **improve output macro bank paths without degrading input macro bank paths**. |

</details>

---

**Question 85**: Macro useful skewing happens only once, during _____ before CCD optimization, and can degrade non-macro timing

*   A. initial_place
*   B. initial_opto
*   C. final_place
*   D. final_opto

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Placement precedes timing-driven useful skew adjustments. |
| $${\color{lightgreen}\text{B}}$$ | Macro useful skewing runs as a discrete phase early during **`initial_opto`** prior to core standard-cell CCD. |
| $${\color{red}\text{C}}$$ | Occurs earlier in the physical optimization flow. |
| $${\color{red}\text{D}}$$ | Occurs earlier in the physical optimization flow. |

</details>

---

**Question 86**: \____command provides launch/capture clock latencies, CRP values, clock skew, slacks, data path logic levels for a chain of registers

*   A. report_ccd_timing
*   B. report_timing
*   C. report_multistage_timing
*   D. None

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Focuses on skew-specific trade-offs between endpoint pairs. |
| $${\color{red}\text{B}}$$ | Evaluates single paths from launch to capture. |
| $${\color{lightgreen}\text{C}}$$ | **`report_multistage_timing`** prints multi-cycle pipeline paths, displaying launch/capture clock latencies, Clock Reconvergence Pessimism (CRP), net skew, slacks, and logic levels across register chains. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 87**: Dynamic power includes ______________

*   A. Internal power
*   B. Switching power
*   C. Leakage power
*   D. Both a &b

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Internal short-circuit and cell-state toggling power. |
| $${\color{red}\text{B}}$$ | Net load capacitance charging and discharging power. |
| $${\color{red}\text{C}}$$ | Static standby sub-threshold leakage power. |
| $${\color{lightgreen}\text{D}}$$ | Dynamic power is the sum of **internal power and switching power** ($P_{\text{dyn}} = P_{\text{int}} + P_{\text{switch}}$). |

</details>

---

**Question 88**: Correct combination amongst below options is

*   A. Low VT, Higher Leakage, Slower
*   B. High VT, Lower leakage, Slower
*   C. Low VT, Higher Leakage, Faster
*   D. Both b&c

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Low $V_t$ cells are faster, not slower. |
| $${\color{red}\text{B}}$$ | High $V_t$ reduces leakage but slows switching speed. |
| $${\color{red}\text{C}}$$ | Low $V_t$ speeds up switching but increases leakage. |
| $${\color{lightgreen}\text{D}}$$ | **Both b and c are correct**: HVT yields lower leakage and slower speed, while LVT yields higher leakage and faster speed. |

</details>

---

**Question 89**: Which command/app option can be used to make scenario leakage-power enabled?

*   A. create_scenario
*   B. set_scenario_status
*   C. power.leakage_mode
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Instantiates the scenario container. |
| $${\color{lightgreen}\text{B}}$$ | **`set_scenario_status -leakage_power true`** activates leakage power optimization on the designated scenario. |
| $${\color{red}\text{C}}$$ | Application option controlling optimization algorithms, not individual scenario status. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 90**: Which is correct regarding below statements:
1. FC uses the value of the `cell_leakage_power` attribute of the library cells in the block to calculate the leakage power.
2. If a cell does not have a `cell_leakage_power` attribute, the tool uses the value of the library level `default_cell_leakage_power` attribute for that cell, otherwise 0.

*   A. Only 1 is correct
*   B. Only 2 is correct
*   C. Both 1&2 are correct
*   D. Neither 1 nor 2 is correct

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Incomplete. |
| $${\color{red}\text{B}}$$ | Incomplete. |
| $${\color{lightgreen}\text{C}}$$ | **Both 1 and 2 are correct**: Synopsys tools evaluate the cell-level `cell_leakage_power` attribute, fall back to the library-level `default_cell_leakage_power` if missing, or default to zero. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 91**: What isn't a part of Dynamic power optimization

*   A. Sizing
*   B. Pin swapping
*   C. VT swapping
*   D. Clock gating

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Downsizing gates reduces pin capacitance and dynamic power. |
| $${\color{red}\text{B}}$$ | Pin swapping steers high-frequency signals to lower-capacitance pins. |
| $${\color{lightgreen}\text{C}}$$ | **$V_t$ swapping** changes sub-threshold static leakage; it has negligible impact on capacitance or dynamic switching power. |
| $${\color{red}\text{D}}$$ | Clock gating disables switching activity ($\alpha$), reducing dynamic power. |

</details>

---

**Question 92**: Which command reports switching activity coverage on essential points, broken down by activity type?

*   A. report_activity -driver
*   B. report_switching_activity -essential
*   C. Both a&b
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Reports switching activity by driver cell. |
| $${\color{red}\text{B}}$$ | Filters coverage to essential structural nodes. |
| $${\color{lightgreen}\text{C}}$$ | **Both commands** (`report_activity` and `report_switching_activity`) can report annotated activity and toggle coverage across essential design points. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 93**: Which option is/are correct regarding enabling Total Power Optimization in FC?

*   A. set_qor_strategy command can be used for stages only upto logic_opto
*   B. set_qor_strategy command can be used for stages upto initial_opto
*   C. opt.power.mode app option setting for final_place/final_opto stage
*   D. Both b&c

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Restricts `set_qor_strategy` prematurely. |
| $${\color{red}\text{B}}$$ | `set_qor_strategy` can steer total power optimization through `initial_opto`. |
| $${\color{red}\text{C}}$$ | `opt.power.mode` drives fine-grained power optimization during late physical placement stages. |
| $${\color{lightgreen}\text{D}}$$ | **Both b and c are correct**: `set_qor_strategy` guides total power through `initial_opto`, while `opt.power.mode` controls physical closure. |

</details>

---

**Question 94**: The incorrect statement amongst below statements is:

*   A. By default, only leakage-power optimization is performed till initial_opto and can be disabled
*   B. Leakage-power optimization can't be disabled till initial_opto
*   C. Till initial_opto, in designs with multiple leakage scenarios, optimization uses the worst case leakage value of all leakage scenarios
*   D. Both a&b

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | This statement is **incorrect** (making it the correct selection): dynamic power optimization can be activated before `initial_opto`, and leakage optimization is not the exclusive default engine throughout that flow. |
| $${\color{red}\text{B}}$$ | A true statement in standard flow contexts. |
| $${\color{red}\text{C}}$$ | True: multi-scenario setups optimize against the worst-case leakage envelope. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 95**: Identify correct statement w.r.t multibit banking

*   A. RTL bus-based and placement-aware multibit mapping consider timing
*   B. set_multibit_options command sets various values of options to control multibit banking
*   C. compile.flow.enable_multibit app option controls the mapping to multibit library cells for the compile_fusion command.
*   D. All of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | True: multibit algorithms are timing-driven. |
| $${\color{red}\text{B}}$$ | True: `set_multibit_options` configures banking constraints. |
| $${\color{red}\text{C}}$$ | True: `compile.flow.enable_multibit` acts as the master switch. |
| $${\color{lightgreen}\text{D}}$$ | **All of the above** statements are accurate descriptions of multi-bit banking in Fusion Compiler. |

</details>

---

**Question 96**: What command can be used to define register min bitwidth and max fanout limits for clock-gating?

*   A. set_clock_gating_options
*   B. set_clock_gating_objects
*   C. set_clock_gate_transformations
*   D. set_lib_cell_purpose ; set_clock_gate_style

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | **`set_clock_gating_options`** includes `-min_bitwidth` and `-max_fanout` to configure ICG insertion rules. |
| $${\color{red}\text{B}}$$ | Configures object-level ICG inclusion/exclusion exceptions. |
| $${\color{red}\text{C}}$$ | Controls splitting/merging transformations on existing clock gates. |
| $${\color{red}\text{D}}$$ | Defines library cells and DFT styles. |

</details>

---

**Question 97**: \_________________ controls allowed transformations (e.g. splitting, ungating) on existing clock gating cells

*   A. set_clock_gating_options
*   B. set_clock_gating_objects
*   C. set_clock_gate_transformations
*   D. set_lib_cell_purpose ; set_clock_gate_style

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Configures bitwidth and fanout thresholds. |
| $${\color{red}\text{B}}$$ | Applies inclusions and exclusions on design blocks. |
| $${\color{lightgreen}\text{C}}$$ | **`set_clock_gate_transformations`** governs merging, splitting, and ungating transformations on pre-existing clock gates. |
| $${\color{red}\text{D}}$$ | Configures library purposes and circuit styles. |

</details>

---

**Question 98**: \_________ command is used to apply clock gating exclusions on registers/hierarchies/PDs

*   A. set_clock_gating_options
*   B. set_clock_gating_objects
*   C. set_clock_gate_transformations
*   D. set_lib_cell_purpose ; set_clock_gate_style

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Configures global bitwidth and fanout parameters. |
| $${\color{lightgreen}\text{B}}$$ | **`set_clock_gating_objects -exclude`** exempts specific registers, modules, or power domains from clock gating. |
| $${\color{red}\text{C}}$$ | Controls restructuring of existing ICG instances. |
| $${\color{red}\text{D}}$$ | Configures library cells and DFT styles. |

</details>

---

**Question 99**: \__________ command defines allowed ICG cells and ICG DFT style to be used

*   A. set_clock_gating_options
*   B. set_clock_gating_objects
*   C. set_clock_gate_transformations
*   D. set_lib_cell_purpose ; set_clock_gate_style

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Configures bitwidth and fanout sizing. |
| $${\color{red}\text{B}}$$ | Applies object-level inclusion/exclusion lists. |
| $${\color{red}\text{C}}$$ | Manages transformations on existing ICGs. |
| $${\color{lightgreen}\text{D}}$$ | **`set_lib_cell_purpose`** designates legal clock gating library cells, and **`set_clock_gate_style`** establishes the circuit implementation and DFT control style. |

</details>

---

**Question 100**: \_________ will help prevent all clock gating transformations on an existing clock gating cell

*   A. set_dont_touch
*   B. set_size_only
*   C. Both a&b
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Prevents cell removal, restructuring, splitting, and merging. |
| $${\color{red}\text{B}}$$ | Prevents structural transformations (splitting, ungating, merging) while allowing sizing. |
| $${\color{lightgreen}\text{C}}$$ | **Both `set_dont_touch` and `set_size_only`** protect the structural integrity of an existing clock gating cell against merging, splitting, or removal. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 101**: report_clock_gating report doesn't include

*   A. No of clock-gating elements
*   B. No of tool-inserted clock gates
*   C. No of pre-existing clock gates
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Included in report. |
| $${\color{red}\text{B}}$$ | Included in report. |
| $${\color{red}\text{C}}$$ | Included in report. |
| $${\color{lightgreen}\text{D}}$$ | **None of the above**: `report_clock_gating` includes total clock-gating elements, tool-inserted ICGs, and pre-existing ICGs. |

</details>

---

**Question 102**: High fanout synthesis / buffering occurs during \________

*   A. logic_opto
*   B. initial_place
*   C. initial_drc
*   D. initial_opto

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Performs generic/boolean structuring. |
| $${\color{red}\text{B}}$$ | Performs coarse placement with virtual buffering. |
| $${\color{lightgreen}\text{C}}$$ | **`initial_drc`** builds physical high-fanout buffer trees (HFNS) to resolve electrical DRC violations. |
| $${\color{red}\text{D}}$$ | Performs full timing and physical optimization after trees are inserted. |

</details>

---

**Question 103**: Tie-high/low cells will be inserted during \__________

*   A. initial_drc
*   B. initial_opto
*   C. final_place
*   D. final_opto

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Focuses on high-fanout buffer tree synthesis. |
| $${\color{lightgreen}\text{B}}$$ | Tie-high and tie-low (`TIEH`/`TIEL`) cells are inserted during **`initial_opto`** to replace direct rail tie-offs with dedicated standard cells. |
| $${\color{red}\text{C}}$$ | Refines cell locations. |
| $${\color{red}\text{D}}$$ | Final timing/power closure pass. |

</details>

---

**Question 104**: Which is correct regarding Spare cells

*   A. All outputs are floating
*   B. All inputs are floating or tied high or low
*   C. Cell is not a physical-only cell
*   D. All of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | True: outputs are left floating for post-mask ECO rewiring. |
| $${\color{red}\text{B}}$$ | True: inputs are tied off to prevent gate oxide float. |
| $${\color{red}\text{C}}$$ | True: spare cells possess logical standard cell models, unlike filler cells. |
| $${\color{lightgreen}\text{D}}$$ | **All of the above** statements are true characteristics of spare cells. |

</details>

---

**Question 105**: \_______ generates a datapath report after compile

*   A. report_design -all
*   B. report_resources -summary
*   C. Either a or b
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Reports general design and netlist statistics. |
| $${\color{lightgreen}\text{B}}$$ | **`report_resources -summary`** details datapath operators, arithmetic components, and inferred DesignWare modules. |
| $${\color{red}\text{C}}$$ | `report_design` does not generate a dedicated datapath operator report. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 106**: \_______ controls DW auto-ungrouping

*   A. compile.datapath.ungroup
*   B. compile.flow.autoungroup
*   C. compile.flow.boundary_optimization
*   D. Either a or b

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | **`compile.datapath.ungroup`** independently controls auto-ungrouping for DesignWare datapath components. |
| $${\color{red}\text{B}}$$ | Manages auto-ungrouping for user hierarchies. |
| $${\color{red}\text{C}}$$ | Controls boundary logic restructuring. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 107**: After enabling congestion driven restructuring, one iteration of placement and rewiring will be run during \________

*   A. logic_opto
*   B. initial_place
*   C. Both a&b
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Restructures logic before placement. |
| $${\color{red}\text{B}}$$ | Performs coarse placement. |
| $${\color{lightgreen}\text{C}}$$ | Congestion-driven restructuring evaluates congestion across **both `logic_opto` and `initial_place`**, triggering iterative logic rewiring and placement legalization. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 108**: Which is incorrect amongst below

*   A. place.coarse.max_density when set to 0.8 causes less clumping as compared to when set to 0.4
*   B. place.coarse.max_density only affects coarse placement
*   C. Setting place.coarse.congestion_driven_max_util to 0.75 allows the utilization of non-congested areas to increase up to 75% in order to reduce congestion in congested areas
*   D. Timing-driven has higher priority than area- or power-driven restructuring

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | This statement is **incorrect** (making it the correct selection): a max density of 0.8 allows tighter local packing and **more clumping**, whereas 0.4 forces cells to spread out, resulting in less clumping. |
| $${\color{red}\text{B}}$$ | True: applies strictly to coarse placement. |
| $${\color{red}\text{C}}$$ | True: shifts cells into lower-density bins. |
| $${\color{red}\text{D}}$$ | True: timing closure takes priority over area/power restructuring. |

</details>

---

**Question 109**: Advanced logic restructuring runs during final_opto stage of

*   A. compile_fusion
*   B. clock_opt
*   C. Both a&b
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Runs during `final_opto` inside `compile_fusion`. |
| $${\color{red}\text{B}}$$ | Runs during `final_opto` inside post-CTS `clock_opt`. |
| $${\color{lightgreen}\text{C}}$$ | Advanced logic restructuring can execute in the `final_opto` stages of **both `compile_fusion` and `clock_opt`**. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 110**: Which is true regarding opt.common.advanced_logic_restructuring_mode

*   A. Setting of “none” is the default, and enables timing-driven restructuring
*   B. Setting of “area” enables timing- and area-driven restructuring
*   C. Setting of “power” enables timing- and power-driven restructuring
*   D. All of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | True: "none" defaults to timing-driven mode. |
| $${\color{red}\text{B}}$$ | True: "area" includes area recovery. |
| $${\color{red}\text{C}}$$ | True: "power" includes dynamic/leakage recovery. |
| $${\color{lightgreen}\text{D}}$$ | **All of the above** statements accurately describe the restructuring mode settings. |

</details>

---

**Question 111**: Cells with \________\_ will not be considered for restructuring

*   A. dont_touch
*   B. size_only
*   C. Fixed attributes
*   D. Any of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Protected from modification. |
| $${\color{red}\text{B}}$$ | Protected from architectural restructuring. |
| $${\color{red}\text{C}}$$ | Protected from relocation. |
| $${\color{lightgreen}\text{D}}$$ | Cells marked with **any of the above** attributes are exempt from logic restructuring. |

</details>

---

**Question 112**: Identify the correct statements

*   A. Placement attractions are well suited for a large number of cells (e.g. modules), use bounds for a small group of cells
*   B. The create_placement_attraction command is a much "softer" placement constraint than the move bound or group bound constraints created by the create_bound command.
*   C. Placement attraction constraints can prevent fragmentation of modules
*   D. Attractions on too many modules can have a negative effect on the placement of other modules
*   E. All statements are correct

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Valid guideline for placement attraction vs bounds. |
| $${\color{red}\text{B}}$$ | Valid description of constraint stiffness. |
| $${\color{red}\text{C}}$$ | Prevents module dispersal across the floorplan. |
| $${\color{red}\text{D}}$$ | Over-constraining attractions degrades placement quality. |
| $${\color{lightgreen}\text{E}}$$ | **All statements are correct** regarding placement attractions and bounds. |

</details>

---

**Question 113**: Which is incorrect regarding advanced logic restructuring

*   A. Timing-driven logic restructuring is always enabled
*   B. Timing-driven has higher priority than area- or power-driven restructuring
*   C. Additional area/power-driven restructuring needs to be enabled by the user
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | True statement. |
| $${\color{red}\text{B}}$$ | True statement. |
| $${\color{red}\text{C}}$$ | True statement. |
| $${\color{lightgreen}\text{D}}$$ | **None of the above**: all listed options are true statements, so none are incorrect. |

</details>

---

**Question 114**: By default, Route-Driven Extraction (RDE) is enabled for

*   A. 7 nm and below
*   B. 16 nm and below
*   C. 10 nm and below
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | RDE is enabled at coarser sub-20nm geometries as well. |
| $${\color{lightgreen}\text{B}}$$ | In Fusion Compiler, Route-Driven Extraction (RDE) is enabled by default for nodes at **16 nm and below** to track severe interconnect resistance and cross-coupling effects. |
| $${\color{red}\text{C}}$$ | Misses nodes between 10nm and 16nm. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 115**: Boundary Optimization includes

*   A. Constant propagation
*   B. Unloaded propagation
*   C. Complement propagation
*   D. All of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Pushes constants across ports. |
| $${\color{red}\text{B}}$$ | Removes unused logic across ports. |
| $${\color{red}\text{C}}$$ | Pushes/absorbs inverters across ports. |
| $${\color{lightgreen}\text{D}}$$ | **All of the above** transformations are parts of boundary optimization. |

</details>

---

**Question 116**: Which is correct regarding register replication

*   A. Register replication is used to improve critical path timing
*   B. Replicated register names, by default, are appended with _rep
*   C. User can't specify both -max_fanout and -num_copies with set_register_replication. If done, -num_copies will take precedence.
*   D. It is enabled by default for all registers
*   E. A,b&c are correct

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | True: splits high-fanout loads on critical timing paths. |
| $${\color{red}\text{B}}$$ | True: appended with `_rep` by default. |
| $${\color{red}\text{C}}$$ | True: `-num_copies` overrides `-max_fanout`. |
| $${\color{red}\text{D}}$$ | False: register replication is not enabled globally by default. |
| $${\color{lightgreen}\text{E}}$$ | **Statements a, b, and c are correct**. |

</details>

---

**Question 117**: Block Abstract contains

*   A. Placement information of cells and pins
*   B. Blockages, site rows, voltage areas, and net nondefault routing rules
*   C. Constraints and timing data
*   D. Multivoltage and UPF information
*   E. a, b, c & d

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Preserves boundary placement data. |
| $${\color{red}\text{B}}$$ | Preserves physical floorplan definitions and NDRs. |
| $${\color{red}\text{C}}$$ | Preserves interface timing models and budgets. |
| $${\color{red}\text{D}}$$ | Preserves power domains and supply nets. |
| $${\color{lightgreen}\text{E}}$$ | An NDM Block Abstract contains **all of the above elements (a, b, c, & d)**. |

</details>

---

**Question 118**: Use \_______ to query block abstract reference

*   A. report_abstracts
*   B. report_design
*   C. Either a or b
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{lightgreen}\text{A}}$$ | **`report_abstracts`** specifically inspects and reports abstract views and reference properties in the active block. |
| $${\color{red}\text{B}}$$ | Summarizes overall design hierarchy. |
| $${\color{red}\text{C}}$$ | Incorrect. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 119**: Use \_______ to ensure implementation readiness prior to implementation commands (e.g compile_fusion)

*   A. check_design
*   B. check_hier_design -stage pre_compile
*   C. check_netlist
*   D. check_design_states

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Standard logic rule checker. |
| $${\color{lightgreen}\text{B}}$$ | **`check_hier_design -stage pre_compile`** audits the readiness of hierarchical sub-blocks, abstracts, and constraints prior to compilation. |
| $${\color{red}\text{C}}$$ | Limited to netlist connectivity checks. |
| $${\color{red}\text{D}}$$ | Non-standard command syntax. |

</details>

---

**Question 120**: The correct statements regarding Extracted Timing Model are

*   A. extract_model command is used to generate etm
*   B. extract_model invokes PrimeTime under the hood to perform model extraction
*   C. Can be used to model IP blocks, where internal details need to be hidden
*   D. All of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | `extract_model` creates the ETM. |
| $${\color{red}\text{B}}$$ | Runs PrimeTime engines internally to generate timing models. |
| $${\color{red}\text{C}}$$ | Generates black-box timing models for IP protection. |
| $${\color{lightgreen}\text{D}}$$ | **All of the above** statements are true regarding Extracted Timing Models. |

</details>

---

**Question 121**: Identify the incorrect statement

*   A. In a serial flow, user implements all blocks entirely and generates models from the fully routed and implemented blocks which are then used in the top-level implementation
*   B. In a parallel flow, for each implementation step at the top-level, a block for which the same or subsequent implementation step is completed is used
*   C. Report_design command can be used to check abstract type
*   D. All soft macros can be filtered using "is_soft_macro" attribute

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Accurately describes a traditional serial hierarchical flow. |
| $${\color{red}\text{B}}$$ | Accurately describes a parallel hierarchical flow. |
| $${\color{lightgreen}\text{C}}$$ | This statement is **incorrect** (making it the correct selection): `report_design` outputs general design properties, while dedicated commands like **`report_abstracts`** must be used to inspect abstract types. |
| $${\color{red}\text{D}}$$ | True: `is_soft_macro` is a valid filtering attribute in FC. |

</details>

---

**Question 122**: Use \__________ to find Soft macros at a particular level (say 1) of physical hierarchy

*   A. get_cells -hierarchical -filter is_soft_macro
*   B. get_cells -hier -filter is_soft_macro&&physical_hierarchy_level == 1
*   C. get_cells -hierarchical -filter is_soft_macro&&ref_view_name == abstract
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Finds soft macros across all levels indiscriminately. |
| $${\color{lightgreen}\text{B}}$$ | **`get_cells -hier -filter "is_soft_macro && physical_hierarchy_level == 1"`** specifically isolates soft macros located at hierarchy level 1. |
| $${\color{red}\text{C}}$$ | Filters based on view binding rather than hierarchy depth. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 123**: Use \__________ to find Soft macros bound to abstract view

*   A. get_cells -hierarchical -filter is_soft_macro
*   B. get_cells -hier -filter is_soft_macro&&physical_hierarchy_level == 1
*   C. get_cells -hierarchical -filter is_soft_macro&&ref_view_name == abstract
*   D. None of the above

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | Misses view-binding criteria. |
| $${\color{red}\text{B}}$$ | Filters by hierarchy depth rather than bound view. |
| $${\color{lightgreen}\text{C}}$$ | **`get_cells -hierarchical -filter "is_soft_macro && ref_view_name == abstract"`** targets soft macro cells referencing abstract views. |
| $${\color{red}\text{D}}$$ | Incorrect. |

</details>

---

**Question 124**: Identify the correct statement

*   A. FC automatically promotes voltage from subblock to top level even if design views are missing in design libraries
*   B. Promoting set_voltage from subblocks to the top level (automatic) requires design views to be available in the design libraries
*   C. When the design view is not present, user must specify the voltage using the set_voltage command from the top level
*   D. After linking, user can always swap individual instances or references to point to the design or abstract view, and specify a label
*   E. B,c,d

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | False: missing design views prevents automated voltage promotion. |
| $${\color{red}\text{B}}$$ | True: design views are required for automatic sub-block voltage promotion. |
| $${\color{red}\text{C}}$$ | True: manual top-level `set_voltage` definitions are required when views are missing. |
| $${\color{red}\text{D}}$$ | True: design and abstract views can be swapped via linking labels. |
| $${\color{lightgreen}\text{E}}$$ | **Statements B, C, and D are correct**. |

</details>

---

**Question 125**: Identify the incorrect statement regarding creating abstract after compile

*   A. Identifies and retains interface logic across all active modes
*   B. Retains pins in the interface that have timing constraints (across all modes active and inactive)
*   C. Retains RC parasitics only of active corners
*   D. Stores UPF information relevant to the retained interface logic

<details>
  <summary>Analysis</summary>

| Option | Description |
|:---|:---|
| $${\color{red}\text{A}}$$ | True: active mode interface logic is preserved. |
| $${\color{red}\text{B}}$$ | True: constrained boundary pins across all defined modes are retained. |
| $${\color{lightgreen}\text{C}}$$ | This statement is **incorrect** (making it the correct selection): block abstracts preserve parasitic RC models across **all defined corners** (active and inactive) so the abstract remains valid if inactive corners are enabled later. |
| $${\color{red}\text{D}}$$ | True: interface UPF power intent is stored with the abstract. |

</details>

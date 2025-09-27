# RISC-V-SoC-Program_week_1
 <details>
<summary>
  Week 1 :- Introduction to Iverilog Design and Test Bench.
</summary>
  <br>
    <details>
      <summary>Day 1 :- Introduction to verilog RTL design and Synthesis.</summary>
    <p>
<ol><h3> <li>Introduction to open-source simulator Iverilog.</li></h3><h2></h2>
  <p>A simulator is a software tool that helps verify digital designs before they are implemented in hardware. It allows us to test the functionality of the design by executing it together with a testbench. </p>
  In Iverilog, the inputs are:
  <ul><li>Design file (RTL code)</li>
    <li>Testbench file</li></ul><br>
  Basic Simulation Flow:
  <ol><li>Write the RTL design and testbench.</li>
  <li>Compile using Iverilog.</li>
  <li>Run the simulation to generate a VCD file.</li>
  <li>Open the VCD file in GTKWave to visualize waveforms.</li></ol>
  <hr>
 <h3><li>Labs using Iverilog and GTKWave.</li></h3><h2></h2>
  <p>To simulate a design and view its waveforms, the following steps were performed:
  <ol><li>Clone the workshop repository:</li><br>
    <pre>git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
cd sky130RTLDesignAndSynthesisWorkshop/verilog_files</pre>
    <li>Compile the Verilog design using Iverilog:</li><br>
    <pre>cd verilog files
iverilog good_latch.v</pre>This generates an output file named <b>"a.out."</b><br>
    <br><li>Run the simulation:</li><br>
    <pre>./a.out</pre>This produces the simulation result in a VCD file (e.g., tb_good_latch.vcd).<br>
    <br><li>Open the waveform in GTKWave:</li><br>
    <pre>gtkwave tb_good_latch.vcd</pre>At this stage, the signal transitions of the design can be visualized and analyzed in GTKWave to verify its functionality.</ol>
  <br>
  <p align="center">
  <img src="https://github.com/user-attachments/assets/b386e58c-8cc5-4927-86b4-9ff97209e914" width="45%"  valign="top"  />
  <img src="https://github.com/user-attachments/assets/b44e0958-5a2d-4659-8508-8e9a39685783" width="45%" />
</p>
  </p>
  <hr>
 <h3> <li>Introduction to Yosys and Logic Synthesis</li></h3><h2></h2>
  <p>Yosys is an open-source logic synthesis tool used to convert RTL (Register Transfer Level) designs into a gate-level netlist. This netlist maps the design onto standard cells from a library, preparing it for further verification and eventual hardware implementation. Verification of Synthesis <br> After synthesis, the netlist is verified to ensure functional equivalence with the original RTL:
  <ol>
    <li>The netlist is simulated along with the same testbench used for RTL simulation.</li>
    <li>The simulator (e.g., Iverilog) generates a VCD file capturing signal transitions.</li>
    <li>This VCD file is viewed in GTKWave to compare waveforms and confirm that the synthesized design behaves identically to the RTL.</li>
  </ol>
  </p>
  <hr>
 <h3> <li>Labs using Yosys and Sky130 PDKs</li></h3><h2></h2>
  <p>To synthesize a design using Yosys and the Sky130 PDK, the following steps were performed:
  <ol>
    <li>Navigate to the Verilog files directory:</li><br>
    <pre>cd verilog_files</pre>
    <li>Start Yosys and read the standard cell library:</li>
    <pre>yosys <br>read_liberty -lib ( relative_path_to_liberty_file ) </pre>
    <p align="center"><img src="https://github.com/user-attachments/assets/ada3a288-a113-4e98-b6ad-8559391bf9b2" width="45%"  valign="top"/><br></p>
    <li>Read the Verilog design file:</li><br>
    <pre>read_verilog good_mux.v</pre>
    <p><img src="https://github.com/user-attachments/assets/b050b932-632b-40cc-952c-8ba0971fe379" width="45%"  valign="top"/>
    <img src="https://github.com/user-attachments/assets/a38f90e2-a137-47c9-8204-129e10cd4f9b" width="45%"  valign="top"/><br></p>
   <li>Synthesize the design specifying the top module and library:</li><br>
    <pre>synth -top good_mux
abc -liberty ( relative_path_to_liberty_file )</pre>
<p align="center"><img src="https://github.com/user-attachments/assets/fde73e2b-b9ef-41fd-9e66-055e6c57f772" width="45%"  valign="center"/><br></p>  
 <li>Visualize the synthesized netlist:</li><br>
  <pre>show</pre>
    <p><img src="https://github.com/user-attachments/assets/7dee12a7-244d-4f3f-8409-fe557ec98205" width="45%"  valign="top"/>
    <img src="https://github.com/user-attachments/assets/281ef7af-d92b-4100-8ff7-d9c9a74b33b7" width="45%"  valign="top"/><br></p>
 <br>  <li>Export the synthesized netlist to a Verilog file:</li><br>
  <pre>write_verilog -noattr good_netlist.v</pre>
    <p align="center">    <img src="https://github.com/user-attachments/assets/6ba5e296-77a8-4f44-aff5-35478954b9c0" width="45%"  valign="top"/><br></p>
 <br> <li>(Optional) Open the file in a text editor for inspection:</li><br>
  <pre>!gedit ( file_name )</pre>
  <p align="center"><img src="https://github.com/user-attachments/assets/91e3fa4c-c62f-494c-adb1-57f3729ab162" width="45%"  valign="top"/><br></p> 
  </ol>
    <br><b>Explanation:</b>
    <ul>
      <li><code>read_liberty:</code> Loads the standard cell library for synthesis.</li>
      <li><code>read_verilog:</code> Loads the RTL design.</li>
      <li><code>synth</code> + <code>abc:</code> Performs logic synthesis and maps the design to the library cells.</li>
      <li><code>show:</code> Visualizes the netlist structure.</li>
      <li><code>write_verilog:</code> Saves the synthesized netlist for post-synthesis simulation or further processing.</li>
    </ul>
  </p>
</ol>
    </p><h2></h2>
    </details>
 <details>
   <summary>Day 2 :- Timing libs, hierarchical vs flat synthesis and efficient flop coding styles.</summary>
  <p>
   <h3>Introduction to Timing Libraries, Hierarchical vs Flat Synthesis, and Efficient Flop Coding Styles.</h3><h2></h2>
   <ol>
    <li><b>Timing Libraries</b></li>
    <p>
     <ul><li>A timing library (usually in <code>.lib</code> format) is a collection of standard cell characterizations. Each cell is described in terms of functionality, timing arcs, power consumption, and physical properties.</li>
      <li>Timing libraries form the backbone of digital design implementation. They contain the essential information required by synthesis and static timing analysis (STA) tools to understand the behavior of standard cells at different process, voltage, and temperature (PVT) conditions.</li>
      <li>Key Contents of a Timing Library :-</li>
      <ul><li><i>Cell Functionality</i> – Boolean logic of the gate (e.g., AND, OR, inverter, flop).</li>
       <li><i>Timing Arcs</i> – Propagation delay and transition time information from input to output pins.</li>
       <li><i>Setup and Hold Times</i> – For sequential elements like flip-flops and latches.</li>
       <li><i>Constraints</i> – Minimum pulse width, recovery/removal times, etc.</li>
       <li><i>Power Data</i> – Internal power, leakage power, and switching power.</li>
       <li><i>Multiple Corners</i> – Libraries are provided for worst-case, best-case, and typical PVT conditions.</li>
      </ul></ul>
    </p>
    <li><b>Hierarchical vs Flat Synthesis</b></li><br>
    <p>When converting RTL to gate-level netlist, synthesis can be performed in two major approaches: hierarchical or flat.<br><br>
    <i>Hierarchical Synthesis :- Each RTL block (module) is synthesized separately, maintaining its boundaries.</i>
     <ul>
      <li>Advantages:-
       <p>
       <ul><li>Preserves logical boundaries → easier debugging and ECOs.</li>
       <li>Allows block-level timing closure.</li>
       <li>Enables parallel work across teams (different engineers handle different blocks).</li>
       <li>Suitable for very large designs.</li></ul></p>
      </li>
      <li>Disadvantages :-
       <p>
        <ul>
         <li>Optimization is restricted to block boundaries.</li>
         <li>May result in suboptimal QoR (Quality of Results) compared to flat.</li>
         <li>Additional overhead in interfacing between blocks.</li>
        </ul>
       </p>
      </li>
     </ul>
    <i>Flat Synthesis :- Entire RTL is flattened into a single module and synthesized as a whole.</i><br><br>
    <ul>
      <li>Advantages:-
       <p>
       <ul><li>Maximum optimization freedom for synthesis tools.</li>
       <li>Better timing, area, and power optimization.</li>
      </ul></p>
      </li>
      <li>Disadvantages :-
       <p>
        <ul>
         <li>Very large designs can become memory and runtime heavy.</li>
         <li>Debugging becomes harder since logical hierarchy is lost.</li>
         <li>ECOs are more complex./li>
        </ul>
       </p>
      </li>
     </ul>
    </p>
    <li><b>Various Flop Coding Styles and optimization</b></li>
    <br><p>Flip-flops are fundamental sequential elements in RTL. The way they are coded has a direct impact on synthesis results, timing, and power.<br>
     <ol>
      <li>Simple D Flip-Flop with Async Reset:-</li>
     <p><pre>always @(posedge clk or negedge rst_n) begin
  if (!rst_n)
    q <= 1'b0;
  else
    q <= d;
end
</pre></p>
     <li>Enable-based Flop (Preferred)</li>
     <p><pre>always @(posedge clk or negedge rst_n) begin
  if (!rst_n)
    q <= 1'b0;
  else if (en)
    q <= d;
end
</pre></p>
     </ol>
        <p><b>Race Condition :-</b><br>
         In digital design, a race condition occurs when the behavior of a circuit depends on the relative timing of signals, leading to unpredictable or incorrect results.
<ul><li>In RTL coding, race conditions often arise due to incorrect use of blocking (=) and non-blocking (<=) assignments.</li>
<li>Example: Using blocking assignments inside a clocked always block may cause one flop’s update to immediately affect another flop in the same cycle, violating intended sequential behavior.</li>
<li>In physical circuits, race conditions can occur due to path delays causing signals to arrive earlier/later than expected.</li>
        </ul></p><br>
     <b>Optimization Aspects :-</b>
     <ul><li><i>Timing:</i> Clean synchronous coding reduces hold/setup violations.</li>
     <li><i>Area:</i> Grouping registers allows synthesis to map to multi-bit flops.</li>
     <li><i>Power:</i> Proper enable usage → synthesis can insert efficient clock gating.</li>
</ul>
    </p>
   </ol>
  </p><h2></h2>
 </details>
   <details>
   <summary>Day 3 :- Combinational and Sequential Optimizations.</summary>
    <h3>Introduction to Optimization, Combinational and Sequential Logic Optimization</h3><h2></h2>
    <p>
     <ol>
      <li>Introduction to Optimization</li><br>
      <p>Optimization in digital design refers to improving the synthesized netlist (post RTL-to-gates conversion) for:<br>
       <ul><li>Performance (timing) → meeting setup/hold requirements.</li>
        <li>Area → reducing gate count and silicon cost.</li>
        <li>Power → minimizing leakage and dynamic switching power.</li></ul><br>
      Synthesis tools perform logic transformations on the RTL to generate a gate-level representation that balances timing, area, and power based on user constraints.
      </p>
      <p>Types of Optimization:-<ol>
       <li><i>Combinational Logic Optimization</i> – Improves efficiency of purely combinational logic.</li>
       <li><i>Sequential Logic Optimization</i> – Improves efficiency of sequential circuits involving flip-flops and registers.</li>
      </ol></p>
     </ol>
    <ol>
     <li><i>Combinational Logic Optimization :-</i></li>
     <p>Combinational optimization focuses on reducing redundant logic, minimizing delay, and optimizing Boolean expressions before mapping to gates.</p>
     <p>Key Techniques :-
     <ol>
      <li>Constant Propagation</li>
      <p><ul>
       <li>Replacing logic driven by constants with simpler circuits.</li>
      <li>Example:</li>
       <p>
       <pre>y = a & 1 → y = a
y = a & 0 → y = 0</pre></p>
      </ul></p>
      <li>Boolean Simplification</li>
      <p><ul>
       <li>Using Boolean algebra or Karnaugh maps to minimize expressions.</li>
      <li>Example:</li>
       <p><pre>y = a + a'b  →  y = a + b</pre></p>
      </ul></p>
      </ol>
     </p>
     <li><i>Sequential Logic Optimization</i></li>
     <p>Sequential optimization improves designs where memory elements (flip-flops, latches) are used. It focuses on timing closure, power, and area while preserving functionality..</p>
     <p>Key Techniques :-
     <ol>
      <li>Sequential Constant Propagation</li>
      <p><ul>
       <li>If a flip-flop output always resolves to a constant (due to logic or unreachable states), it is optimized away.</li>
      </ul></p>
      <li>Register Retiming</li>
      <p><ul>
       <li>Moving registers across combinational logic to balance path delays.</li>
      <li>Example:</li>
       <ul><li>Original:</li>
       <p><pre>FF → long logic → FF</pre></p>
       <li>Retimed:</li>
        <p><pre>FF → shorter logic → FF → shorter logic → FF</pre></p>
       </ul>
      </ul></p>
      </ol>
     </p>
    </ol><h2></h2>
    </p>
 </details>
   <details>
   <summary>Day 4 :- GLS, Blocking and Non-blocking and Synthesis simulation mismatch.</summary>
    <p>
     <h3>GLS, Synthesis-Simulation mismatch and Blocking/Non-blocking statements</h3><h2></h2>
     <ol>
      <li><b>Gate-Level Simulation (GLS) :- </b></li>
      <p>Gate-Level Simulation is the process of simulating the synthesized netlist (post-synthesis Verilog) instead of the RTL.</p>
      <p>
       <ul>
        <li>What is GLS?</li>
        <p>GLS uses the structural Verilog netlist generated after synthesis. The netlist is composed of standard cells (AND, OR, MUX, FFs, etc.) from the target technology library.</p>
        <li>Why do we need GLS?</li>
        <ol><li>To verify that synthesis has not altered the functionality.</li>
         <li>To check for simulation-synthesis mismatches caused by RTL coding style.</li>
         <li>To catch mismatches between RTL and synthesized design.</li></ol>
        <p>
        <li>Types of Gate-Level Verilog Models</li>
        <ol><li><i>Timing-Aware Models</i> – Contain both functionality and timing (delays, setup/hold checks). Used for functional + timing validation.</li>
        <li><i>Functional Models</i> – Contain only functional behavior (no delay info). Used to check functionality only.</li></ol></p>
        <li>Note:</li>
        If the gate-level models are delay-annotated, GLS can also be used for timing validation, not just functional verification.
       </ul>
      </p>
      <li><b>Synthesis-Simulation Mismatches :- </b></li>
      <p>Simulation is event-driven: outputs change only when inputs or control signals in the sensitivity list change. If RTL is written carelessly, synthesis and simulation may interpret it differently, leading to mismatches.</p>
      <b>Common Causes of Mismatch:</b>
      <ol>
      <p><li>Missing Sensitivity List :-</li>
       <p><ol>
        <li>In simulation, if an input signal is missing from the sensitivity list, output updates may not trigger correctly.</li>
        <li>Example :</li>
        <p><pre>always @(sel) begin
  if (sel) y = i1;
  else     y = i0;  // i0/i1 missing in sensitivity list
end
</pre></p>
        <li>Simulation: <code>y</code> won’t update when <code>i0</code> or <code>i1</code> change.</li>
        <li>Synthesis: Interprets it as a proper multiplexer (correct).</li>
       </ol></p>
       <p>
       <li>Blocking vs Non-Blocking Assignments :-</li>
       <ul>
        <li>Blocking (<code>=</code>): Executes sequentially, one after the other.</li>
        <li>Non-blocking (<code>&lt;=</code>): Executes concurrently, updates at the end of the time step.</li>
        <li>Mismatches occur if blocking is used inside sequential always blocks (@(posedge clk)), since simulation may not reflect actual hardware behavior</li>
       </ul></p>
       <li>Non-Standard Verilog Coding :-</li>
        <ul><li>Using constructs not synthesis-friendly (e.g., delays #, infinite loops, etc.) can cause mismatches.</li></ul>
        </p>
      </ol>
      <p>How Simulation Works (Activity Driven)</p>
      <ul> <li>Simulation updates outputs only when an input changes in the sensitivity list.</li>
       <li>In always blocks:</li>
       <ol><li>Combinational always blocks (always @(*)) update immediately when any input changes.</li>
       <li>Sequential always blocks (always @(posedge clk)) update only on clock edges.</li></ol><br>
       </ul>
      <li><b>Blocking vs Non-Blocking Assignments :- </b></li>
      <p>
       <ul>
       <li>Blocking (<code>=</code>)</li>
       <p>
        <ol>
         <li>Statements are executed immediately in sequence.</li>
         <li>Risk: May cause unintended latch inference or mismatches if misused in sequential logic.</li>
         <li>Best for combinational logic modeling.</li>
        </ol>
       </p>
       <li>Non-Blocking (<code>&lt;=</code>)</li>
       <p>
        <ol>
         <li>All RHS values are evaluated first, then updates happen in parallel at the end of the simulation time step.</li>
         <li>Best for sequential logic modeling (flip-flops).</li>
        </ol>
       </p>
      </p></ul>
      <li><b>Lab Experiments :-</b></li>
      Lab 1: GLS on Ternary Operator MUX
      <p>Commands:<p><pre>iverilog ternary_op_mux.v tb_ternary_op_mux.v
./a.out
gtkwave tb_ternary_op_mux.vcd
</pre></p></p>
      <p>Inside Yosys:<p><pre>yosys
read_liberty -lib ../lib/sky130_fd_sc_hd_tt_025c_1v80.lib
read_verilog ternary_operator_mux.v
synth -top ternary_operator_mux
abc -liberty ../lib/sky130_fd_sc_hd_tt_025c_1v80.lib
write_verilog -noattr ternary_operator_mux_net.v
show
</pre></p></p>
      <p>Run GLS:<p><pre>iverilog ../my_lib/verilog_model/primitives.v \
        ../my_lib/verilog_model/sky130_fd_sc_hd.v \
        ternary_operator_mux_net.v tb_ternary_op_mux.v
./a.out
gtkwave tb_ternary_op_mux.vcd
</pre></p></p>
      Lab 2: GLS on Bad MUX (Simulation-Synthesis Mismatch)
      <p><pre>iverilog bad_mux.v tb_bad_mux.v
./a.out
gtkwave tb_bad_mux.vcd
</pre></p>
      <p>Inside Yosys:<p><pre>yosys
read_liberty -lib ../lib/sky130_fd_sc_hd_tt_025c_1v80.lib
read_verilog bad_mux.v
synth -top bad_mux
abc -liberty ../lib/sky130_fd_sc_hd_tt_025c_1v80.lib
write_verilog -noattr bad_mux_net.v
show
</pre></p></p>
      <p>Run GLS:<p><pre>iverilog ../my_lib/verilog_model/primitives.v \
        ../my_lib/verilog_model/sky130_fd_sc_hd.v \
        bad_mux_net.v tb_bad_mux.v
./a.out
gtkwave tb_bad_mux.vcd
</pre></p></p>
      Lab 3: Blocking Statement Caveat
      <p><pre>iverilog blocking_caveat.v tb_blocking_caveat.v
./a.out
gtkwave tb_blocking_caveat.vcd
</pre></p>
       <p>Inside Yosys:<p><pre>yosys
read_liberty -lib ../lib/sky130_fd_sc_hd_tt_025c_1v80.lib
read_verilog blocking_caveat.v
synth -top blocking_caveat
abc -liberty ../lib/sky130_fd_sc_hd_tt_025c_1v80.lib
write_verilog -noattr blocking_caveat_net.v
show
</pre></p></p>
       <p>Run GLS:<p><pre>iverilog ../my_lib/verilog_model/primitives.v \
        ../my_lib/verilog_model/sky130_fd_sc_hd.v \
        blocking_caveat_net.v tb_blocking_caveat.v
./a.out
gtkwave tb_blocking_caveat.vcd
</pre></p></p>
     </ol>
    </p><h2></h2>
 </details>
   <details>
   <summary>Day 5 :- Optimization in Synthesis.</summary>
    <p><h3>Optimization in Synthesis: If-Case Constructs, Loops, and Generate Statements</h3>
     <h2></h2>
    <p>
     <ol>
      <p><li><b>If-Case Constructs</b></li></p>
      <p>If Statements
      <p>
      <ul>
       <li>Purpose: Used to implement conditional logic in RTL. Can also create priority logic when multiple conditions are present.</li>
       <li>Example: Counter Implementation</li>
       <p><pre>always @(posedge clk or posedge reset) begin
    if (reset)
        count <= 3'b000;
    else if (en)
        count <= count + 1;
end
</pre></p>
         <li>Explanation:</li>
         <p><ul>
          <li>If <code>reset</code> is active, counter initializes.</li>
          <li>If <code>enable</code> is active, counter increments.</li>
          <li>If neither, the counter retains its previous value (good latch behavior).</li>
         </ul></p>
         Caution with If Statements
         <p><ul>
          <li>Incomplete if statements may infer latches if some conditions are not covered.</li>
          <li>Example of inferred latch:</li>
          <p><pre>if (cond1)
    y = a;
else if (cond2)
    y = b;
</pre></p>
          <li>Issue: If neither <code>cond1</code> nor <code>cond2</code> is true, <code>y</code> retains its previous value → synthesis infers a latch.</li>
          <li>Solution: Always include an <code>else</code> statement to avoid unintended latches.</li>
         </ul></p>
         Case Statements
         <ul>
          <li>Purpose: Alternate to if-statements, often used in combinational logic with multiple discrete selections.</li>
          <li>Example:</li>
          <p><pre>reg y;
always @(*) begin
    case(sel)
        2'b00: y = a;
        2'b01: y = b;
        default: y = c; // Avoid inferred latch
    endcase
end
</pre></p>
          Caveats with Case Statements
          <p><ol>
           <li>Incomplete Case → can infer latches.</li>
           <p><ul><li>Solution: Always include a default case.</li></ul></p>
           <li>Partial Assignment in Case → not all signals assigned in every branch.</li>
           <p><ul>
            <li>Example:</li>
            <p><pre>reg [1:0] sel;
reg x, y;
always @(*) begin
    case(sel)
        2'b00: begin x=a; y=b; end
        2'b01: begin x=c; end // y not assigned → inferred latch
        default: begin x=d; y=b; end
    endcase
end
</pre></p>
            <li>Solution: Assign all outputs in every branch, including <code>default</code>.</li>
           </ul></p>
          </ol></p>
          Comparison: If vs Case
          <p><ul>
           <li>If Statements → good for priority logic.</li>
           <li>Case Statements → good for mutually exclusive conditions, easier to read.</li>
           <li>Avoid overlapping cases → prevents ambiguity and inferred latches.</li>
          </ul></p>
         </ul>
      </ul> 
      </p>
      </p>
      <p><li><b>Lab Experiments</b></li></p>
         Lab 1: Incomplete If Statement
         <p><pre>iverilog incomp_if.v tb_incomp_if.v
./a.out
gtkwave tb_incomp_if.vcd
</pre></p>
         Inside Yosys:
         <p><pre>read_liberty -lib ../lib/sky130_fd_sc_hd_tt_025c_1v80.lib
read_verilog incomp_if.v
synth -top incomp_if
abc -liberty ../lib/sky130_fd_sc_hd_tt_025c_1v80.lib
show
</pre></p>
         Lab 2: Incomplete / Overlapping Case Statement
         <p><pre>iverilog incomp_case.v tb_incomp_case.v
./a.out
gtkwave tb_incomp_case.vcd
</pre></p>
         Inside Yosys:
         <p><pre>read_liberty -lib ../lib/sky130_fd_sc_hd_tt_025c_1v80.lib
read_verilog incomp_case.v
synth -top incomp_case
abc -liberty ../lib/sky130_fd_sc_hd_tt_025c_1v80.lib
show
</pre></p>
      <p><li><b>Loops and Generate Statements</b></li></p>
         For Loop
         <p><ul>
          <li>Usage: Inside <code>always</code> blocks for evaluating expressions or repetitive logic in RTL.</li>
          <li>Example:</li>
          <p><pre>reg [7:0] arr [0:3];
integer i;
always @(posedge clk) begin
    for (i=0; i<4; i=i+1)
        arr[i] <= arr[i] + 1;
end
</pre></p>
          <li>Synthesizer expands the loop into hardware equivalent of repeated assignments.</li>
         </ul></p>
         For-Generate
         <p><ul>
          <li>Usage: Outside <code>always</code> blocks for hardware instantiation.</li>
          <li>Example:</li>
          <p><pre>genarate i;
generate
    for (i=0; i<4; i=i+1) begin : gen_block
        dff u_dff (.clk(clk), .d(d[i]), .q(q[i]));
    end
endgenerate
</pre></p>
          <li>Synthesizer creates 4 flip-flop instances automatically.</li>
         </ul></p>
     Difference Between Loop and Generate
     <p>
      <table>
  <thead>
    <tr>
      <th>For Loop (<code>for</code>)</th>
      <th>For-Generate (<code>generate for</code>)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Used <b>inside procedural blocks</b> like <code>always</code> or <code>initial</code>.</td>
      <td>Used <b>outside procedural blocks</b> in the structural code.</td>
    </tr>
    <tr>
      <td>Describes <b>behavioral operations</b> (simulation style).</td>
      <td>Describes <b>structural hardware instantiation</b>.</td>
    </tr>
    <tr>
      <td>Executed during <b>simulation/synthesis</b>; synthesizer unrolls it.</td>
      <td>Executed during <b>elaboration (compile-time)</b> before simulation/synthesis.</td>
    </tr>
    <tr>
      <td><b>Cannot instantiate modules</b> or new hardware blocks.</td>
      <td><b>Can instantiate modules</b>, blocks, or signals.</td>
    </tr>
    <tr>
      <td>Best suited for <b>testbenches, array operations, or repeated assignments</b>.</td>
      <td>Best suited for <b>N-bit datapaths, parameterized hardware, or repetitive structures</b>.</td>
    </tr>
    <tr>
      <td>Example usage: increment counters, loop over arrays.</td>
      <td>Example usage: generate multiple adders, multiplexers, or flip-flops.</td>
    </tr>
  </tbody>
</table>
     </p>
     </ol>
    </p>
   </p>
     <p align="center"><b>✨ Thank you for reading! ✨</b></p>
 </details>
  </details>

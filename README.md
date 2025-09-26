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
    </ol>
    </p>
 </details>
   <details>
   <summary>Day 4 :- GLS, Blocking and Non-blocking and Synthesis simulation mismatch.</summary>
 </details>
   <details>
   <summary>
     Day 5 :- Optimization in Synthesis.
   </summary>
 </details>
  </details>

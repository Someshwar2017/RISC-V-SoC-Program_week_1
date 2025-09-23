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
    </p>
    </details>
 <details>
   <summary>
     Day 2 :- Timing libs, hierarchical vs flat synthesis and efficient flop coding styles.
   </summary>
 </details>
   <details>
   <summary>
     Day 3 :- Combinational and Sequential Optimizations.
   </summary>
 </details>
   <details>
   <summary>
     Day 4 :- GLS, Blocking and Non-blocking and Synthesis simulation mismatch.
   </summary>
 </details>
   <details>
   <summary>
     Day 5 :- Optimization in Synthesis.
   </summary>
 </details>
  </details>

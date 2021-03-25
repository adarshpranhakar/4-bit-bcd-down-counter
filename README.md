# 4-bit-bcd-down-counter

// Code your design here
module bcd(rst,clk,q);
  input  rst,clk;
  output reg [3:0] q;
  initial q=0;
  always@(posedge(clk))
    if(~rst||q>0)
      q=q-1;
  else 
     q=9;
endmodule

// code for test bench in EDA playground software
// Code your testbench here


module tb;
  reg rst,clk;
  wire [3:0] q;
  bcd b(rst,clk,q);
  
 
  initial begin
    clk=0;
  forever
    #2clk=~clk;
  end
  initial begin
    forever#1 $display("q=%b",q);
      end
  
  initial 
    begin
      $dumpfile("dump.vcd"); $dumpvars;
     rst=0;
      #1rst=1;
      #50$finish;
    
  end
endmodule

//The code here is to simulate 4 bit bcd down counter in Xilinx Design tools or EDA playground software

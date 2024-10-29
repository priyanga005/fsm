module fsm (input clk, input reset, input a, output reg b);
parameter A = 2’b00;
parameter B = 2’b01;
reg [1:0] state, next_state;
always @(posedge clk) begin
if (reset) begin
state <= A;
b <= 0;
end
else begin
state <= next_state;
case (state)
A: begin
if (a) begin
next_state <= B;
b <= 1;
end
else begin
next_state <= A;
b <= 0;
end
end
B: begin
next_state <= A;
b <= 0;
end
endcase
end
end
endmodule

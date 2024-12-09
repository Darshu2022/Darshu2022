Half Adder

module HalfAdder(input A, B, output Sum, Carry);

  assign Sum = A ^ B;

  assign Carry = A & B;

endmodule





Half Subtractor

module HalfSubtractor(input A, B, output Diff, Borrow);

  assign Diff = A ^ B;

  assign Borrow = ~A & B;

endmodule



Full Subtractor

module FullSubtractor(input A, B, Bin, output Diff, Borrow);

  assign Diff = A ^ B ^ Bin;

  assign Borrow = (~A & B) | (Bin & (~A ^ B));

endmodule



Binary Adder-Subtractor

module AdderSubtractor(input [3:0] A, B, input AddSub, output [3:0] Result, output CarryOut);

  wire [3:0] B_inverted;

  assign B_inverted = AddSub ? ~B : B;

  assign Cin = AddSub ? 1'b1 : 1'b0;

  assign {CarryOut, Result} = A + B_inverted + Cin;

endmodule

//除頻器
module divfreq(input CLK,output reg CLK_div);
	reg [24:0] Count;
	
	always @(posedge CLK)
	begin
		if(Count > 25000)
		begin
			Count <= 25'b0;
			CLK_div <= ~CLK_div;
		end
		else
			Count <= Count + 1'b1;
	end
endmodule

//掉落物的除頻器1
module divfreq2(input CLK, output reg CLK_div);
	reg [24:0] Count; 
	always @(posedge CLK) 
	begin 
		if(Count > 25000000) 
		begin 
			Count <= 25'b0; 
			CLK_div <= ~CLK_div; 
		end 
		else 
			Count <= Count + 1'b1; 
	end 
endmodule 

//七段顯示器的除頻器
module divfreq3(input CLK, output reg CLK_div); 
	reg [24:0] Count; 
	always @(posedge CLK) 
		begin 
			if(Count > 50000) 
				begin 
					Count <= 25'b0; CLK_div <= ~CLK_div; 
				end 
			else 
				Count <= Count + 1'b1; 
		end 
endmodule 

//計分除頻器
module divfreq4(input CLK, output reg CLK_div);
	reg [29:0] Count;
	always @(posedge CLK)
	begin
		if(Count > 23000000)
		begin
			Count <= 30'b0;
		CLK_div <= ~CLK_div;
	end
else
      Count <= Count + 1'b1;
    end
endmodule

//掉落物除頻器2
module divfreq5(input CLK, output reg CLK_div); 
	reg [24:0] Count; 
	always @(posedge CLK) 
	begin 
		if(Count > 123456000) 
		begin 
			Count <= 25'b0; 
			CLK_div <= ~CLK_div; 
		end 
		else 
			Count <= Count + 1'b1; 
	end 
endmodule

//music除頻器
module divfreq6(input CLK, output reg CLK_div);
	reg [24:0] Count; 
	always @(posedge CLK) 
	begin 
		if(Count > 5000000) 
		begin 
			Count <= 25'b0; 
			CLK_div <= ~CLK_div; 
		end 
		else 
			Count <= Count + 1'b1; 
	end 
endmodule 


//掉落物一次跳2格(b)
module fallingobject2(input reg [7:0]position_A,CLK_div2, CLK_div5,Clear,b, output reg [7:0]position_B);
	reg[24:0]cnt;
   reg restart;
	
	always @(posedge CLK_div5) 
	begin
		if(cnt > 250000)
			cnt <= 25'd0; 		
		else
		   cnt <= cnt + 1'b1;
	end
	
	initial
	begin
		position_B = position_A;
      restart = 0; 
	end	
	
	always @(posedge CLK_div2)
	begin			
		if(restart)
		begin
			position_B <= position_A;	
			restart = 0;
		end
		else
		begin
			position_B = (position_B >> 2 )+ 2'b10;
			if(position_B==8'b00000100) 
				position_B = 8'b00000011;
			if(position_B==8'b00000010)
			begin
				restart = 1;
			end
			if(b==1) position_B <= 8'b00000010;
		end
	end
endmodule

//掉落物一次跳1格(g)
module fallingobject1(input reg [7:0]position_A,CLK_div2, CLK_div5,Clear,g, output reg [7:0]position_B);
	reg[24:0]cnt;
   reg restart;

	always @(posedge CLK_div5) 
	begin
		if(cnt > 250000)
			cnt <= 25'd0; 		
		else
		   cnt <= cnt + 1'b1;
	end
	
	initial
	begin
		position_B = position_A;
      restart = 0;
	end	

	always @(posedge CLK_div2)
	begin			
		if(restart)
		begin
			position_B <= position_A;	
			restart = 0;
		end
		else
		begin			
			position_B = (position_B >> 1 )+ 1'b1;	
			if(position_B==8'b00000001)
			begin
				restart = 1;
			end
			if(position_B==8'b00000010)
			begin
				restart = 1;
			end		
			if(position_B==8'b00000100) 
				position_B = 8'b00000011;
				
			if(g==1) position_B <= 8'b00000010;			
		end
	end
endmodule

//掉落物一次跳1格(r)
module fallingobject3(input reg [7:0]position_A,CLK_div2, CLK_div5,Clear,r, output reg [7:0]position_B);
	reg[24:0]cnt;
   reg restart;

	always @(posedge CLK_div5) 
	begin
		if(cnt > 250000)
			cnt <= 25'd0; 		
		else
		   cnt <= cnt + 1'b1;
	end
	
	initial
	begin
		position_B = position_A;
      restart = 0;
	end	

	always @(posedge CLK_div2)
	begin			
		if(restart)
		begin
			position_B <= position_A;	
			restart = 0;
		end
		else
		begin			
			position_B = (position_B >> 1 )+ 1'b1;	
			if(position_B==8'b00000001)
			begin
				restart = 1;
			end
			
			if(position_B==8'b00000010)
			begin
				restart = 1;
			end
			
			if(position_B==8'b00000100) 
				position_B = 8'b00000011;
			
			if(r==1) position_B <= 8'b00000010;
		end
	end
endmodule

//掉落物一次跳1格(y)
module fallingobject4(input reg [7:0]position_A,CLK_div2, CLK_div5,Clear,y, output reg [7:0]position_B);
	reg[24:0]cnt;
   reg restart;

	always @(posedge CLK_div5) 
	begin
		if(cnt > 250000)
			cnt <= 25'd0; 		
		else
		   cnt <= cnt + 1'b1;
	end
	
	initial
	begin
		position_B = position_A;
      restart = 0;
	end	

	always @(posedge CLK_div2)
	begin			
		if(restart)
		begin
			position_B <= position_A;	
			restart = 0;
		end
		else
		begin			
			position_B = (position_B >> 1 )+ 1'b1;	
			if(position_B==8'b00000001)
			begin
				restart = 1;
			end
			
			if(position_B==8'b00000010)
			begin
				restart = 1;
			end		
			if(position_B==8'b00000100) 
				position_B = 8'b00000011;
			
			if(y==1) position_B <= 8'b00000010;			
		end
	end
endmodule

module fallingobject5(input reg [7:0]position_A,CLK_div2, CLK_div5,Clear,y, output reg [7:0]position_B);
	reg[24:0]cnt;
   reg restart;

	always @(posedge CLK_div5) 
	begin
		if(cnt > 250000)
			cnt <= 25'd0; 		
		else
		   cnt <= cnt + 1'b1;
	end
	
	initial
	begin
		position_B = position_A;
      restart = 0;
	end	

	always @(posedge CLK_div2)
	begin			
		if(restart)
		begin
			position_B <= position_A;	
			restart = 0;
		end
		else
		begin			
			position_B = (position_B >> 1 );	
			if(position_B == 8'b00000010) position_B = (position_B >> 1 );
			if(position_B==8'b00000000)
			begin
				restart = 1;
			end
			if(y==1) position_B <= 8'b00000000;			
		end
	end
endmodule

//初始畫面動畫
module InitialAni(input reg [7:0]position_A,CLK_div2, CLK_div5,output reg [7:0]position_B);
	reg[24:0]cnt;
   reg restart;

	always @(posedge CLK_div5) 
	begin
		if(cnt > 250000)
			cnt <= 25'd0; 		
		else
		   cnt <= cnt + 1'b1;
	end
	
	initial
	begin
		position_B = position_A;
      restart = 0;
	end	

	always @(posedge CLK_div2)
	begin			
		if(restart)
		begin
			position_B <= position_A;	
			restart = 0;
		end
		else
		begin			
			position_B = position_B >> 1 ;	
			restart =1;		
		end
	end
endmodule

module music(input reg start,input reg wrong,input reg over,clear,CLK_div6,CLK, output reg beep, output reg End);
	reg [7:0] music;
	reg [22:0] j;
	reg [16:0] count1,div_num;
	
	initial
	begin
	music=0;
	j=0;
	count1=0;
	end
	
	always @(posedge CLK_div6)
	begin
	if(clear) 
	begin
	music=0;
	End=0;
	end
		if(music==8'd96)
		begin
			End=1;
			end
		else
		begin
			music<=music+1'b1;
			End=0;
			end
	end

	always @(posedge CLK)
	begin
	if(count1==div_num)
	begin
		count1<=0;
		beep=~beep;
	end
	else
		count1<=count1+1'b1;
	end

	parameter
	M1=17'h0ba9e,//DO
	M2=17'h0a648,//RE
	M3=17'h0941f,//ME
	M4=17'h08bcf,//FA
	M5=17'h07c90,//SO
	M6=17'h06ef9,//LA
	M7=17'h062dd;//SI
	
	always @(posedge CLK_div6)
	begin
	if(start&&(!over))
	begin
	if(wrong) div_num=0;
	else
	begin
	case(music)
		8'd0 : div_num=M1;
		8'd1 : div_num=M1;
		8'd2 : div_num=M1;
		8'd3 : div_num=M1;
		8'd4 : div_num=M5;
		8'd5 : div_num=M5;
		8'd6 : div_num=M5;
		8'd7 : div_num=M5;	
		8'd8 : div_num=M6;
		8'd9 : div_num=M6;
		8'd10 : div_num=M6;
		8'd11: div_num=M6;
		8'd12: div_num=M5;
		8'd13: div_num=M5;
		
		8'd14:div_num=M5;
		8'd15:div_num=M5;
		8'd16 : div_num=M4;
		8'd17 : div_num=M4;
		8'd18 : div_num=M4;
		8'd19 : div_num=M4;
		8'd20 : div_num=M3;
		8'd21 : div_num=M3;	
		8'd22 : div_num=M3;
		8'd23 : div_num=M3;
		8'd24 : div_num=M2;
		8'd25 : div_num=M2;
		8'd26 : div_num=M2;
		8'd27 : div_num=M2;
		8'd28 : div_num=M1;
		8'd29 : div_num=M1;
		
		8'd30:div_num=M1;
		8'd31:div_num=M1;
		8'd32 : div_num=M5;
		8'd33 : div_num=M5;
		8'd34 : div_num=M5;
		8'd35 : div_num=M5;
		8'd36 : div_num=M4;
		8'd37 : div_num=M4;
		8'd38 : div_num=M4;
		8'd39 : div_num=M4;
		8'd40 : div_num=M3;
		8'd41 : div_num=M3;
		8'd42 : div_num=M3;
		8'd43 : div_num=M3;
		8'd44 : div_num=M2;
		8'd45 : div_num=M2;
		
		8'd46:div_num=M2;
		8'd47:div_num=M2;
		8'd48 : div_num=M5;
		8'd49 : div_num=M5;
		8'd50 : div_num=M5;
		8'd51 : div_num=M5;
		8'd52 : div_num=M4;
		8'd53 : div_num=M4;
		8'd54 : div_num=M4;
		8'd55 : div_num=M4;
		8'd56 : div_num=M3;
		8'd57 : div_num=M3;
		8'd58 : div_num=M3;
		8'd59 : div_num=M3;
		8'd60 : div_num=M2;
		8'd61 : div_num=M2;
		
		8'd62:div_num=M2;
		8'd63:div_num=M2;
		8'd64 : div_num=M1;
		8'd65 : div_num=M1;
		8'd66 : div_num=M1;
		8'd67 : div_num=M1;
		8'd68 : div_num=M5;
		8'd69 : div_num=M5;
		8'd70 : div_num=M5;
		8'd71 : div_num=M5;
		8'd72 : div_num=M6;
		8'd73 : div_num=M6;
		8'd74 : div_num=M6;
		8'd75 : div_num=M6;
		8'd76 : div_num=M5;
		8'd77 : div_num=M5;
		
		8'd78:div_num=M5;
		8'd79:div_num=M5;
		8'd80 : div_num=M4;
		8'd81 : div_num=M4;
		8'd82 : div_num=M4;
		8'd83 : div_num=M4;
		8'd84 : div_num=M3;
		8'd85 : div_num=M3;
		8'd86 : div_num=M3;
		8'd87 : div_num=M3;
		8'd88 : div_num=M2;
		8'd89 : div_num=M2;
		8'd90 : div_num=M2;
		8'd91 : div_num=M2;
		8'd92 : div_num=M1;
		8'd93 : div_num=M1;
		
		8'd94:div_num=0;
		8'd95:div_num=0;
	endcase
	end
	end
	end
	
	endmodule
module aa(output reg beep, output reg [7:0] DATA_R,DATA_G,DATA_B, output reg [3:0] COMM, output reg [5:0]hp,input CLK,Clear, r, g, b, y,output reg A,B,C,D,E,F,G,COM1,COM2);
	wire [7:0][7:0]p2;
	wire [7:0][7:0]p3;
	wire [7:0][7:0]p4;
	wire [7:0][7:0]i2;
	wire [7:0][7:0]i3;
	wire [7:0][7:0]i4;
	wire [7:0][7:0]w3;
	wire [7:0][7:0]l4;
	reg [3:0]score,score1,score2;
	reg COM;
	reg clear;
	reg over;
	reg start;
	reg wrong;
	reg End;
	
	divfreq D0(CLK,CLK_div);
	divfreq2 D2(CLK,CLK_div2);
	divfreq3 D3(CLK, CLK_div3);
	divfreq4 D4(CLK, CLK_div4);
	divfreq5 D5(CLK,CLK_div5);
	divfreq6 D6(CLK,CLK_div6);
	
	
	
	parameter logic [7:0] B_Char [7:0]=
				    '{8'b10000010,
						8'b10000010,
						8'b00000010,
						8'b00000010,
						8'b00000010,
						8'b00000010,
						8'b00000010,
						8'b00000010};
						
	parameter logic [7:0] G_Char [7:0]=
				    '{8'b00000010,
						8'b00000010,
						8'b10000010,
						8'b10000010,
						8'b01000010,
						8'b01000010,
						8'b00000010,
						8'b00000010};
						
	parameter logic [7:0] R_Char [7:0]=
				    '{8'b00000010,
						8'b00000010,
						8'b00000010,
						8'b00000010,
						8'b01000010,
						8'b01000010,
						8'b10000010,
						8'b10000010};
						
		
						
		parameter logic [7:0] Lose_Char [7:0]=
				    '{8'b00000000,
						8'b11111110,
						8'b11111110,
						8'b11110000,
						8'b11110000,
						8'b11110000,
						8'b00000000,
						8'b00000000};
						
		parameter logic [7:0] Win_Char [7:0]=
				    '{8'b00000000,
						8'b00000000,
						8'b11111110,
						8'b11111110,
						8'b00011110,
						8'b00011110,
						8'b00011110,
						8'b00000000};
						
		parameter logic [7:0] Ini_Char [7:0]=
				    '{8'b00000000,
						8'b00001100,
						8'b00001110,
						8'b00000110,
						8'b00000000,
						8'b00000000,
						8'b00000000,
						8'b00000000};
						
		parameter logic [7:0] Ini2_Char [7:0]=
				    '{8'b00000000,
						8'b00000000,
						8'b00000100,
						8'b11110000,
						8'b10000000,
						8'b01000000,
						8'b00100000,
						8'b00000000};
						
		parameter logic [7:0] Ini3_Char [7:0]=
				    '{8'b00000000,
						8'b00001000,
						8'b00011100,
						8'b01111100,
						8'b00000000,
						8'b00000000,
						8'b00000000,
						8'b00000000};		
	
	fallingobject2 F1(B_Char[0],CLK_div2, CLK_div5, Clear, b, p2[0]);
	fallingobject2 F2(B_Char[1],CLK_div2, CLK_div5, Clear, b, p2[1]);
	fallingobject2 F3(B_Char[2],CLK_div2, CLK_div5, Clear, b, p2[2]);
	fallingobject2 F4(B_Char[3],CLK_div2, CLK_div5, Clear, b, p2[3]);
	fallingobject2 F5(B_Char[4],CLK_div2, CLK_div5, Clear, b, p2[4]);
	fallingobject2 F6(B_Char[5],CLK_div2, CLK_div5, Clear, b, p2[5]);
	fallingobject2 F7(B_Char[6],CLK_div2, CLK_div5, Clear, b, p2[6]);
	fallingobject2 F8(B_Char[7],CLK_div2, CLK_div5, Clear, b, p2[7]);
	
	fallingobject1 A1(G_Char[0],CLK_div2, CLK_div5, Clear, g, p3[0]);
	fallingobject1 A2(G_Char[1],CLK_div2, CLK_div5, Clear, g, p3[1]);
	fallingobject4 A3(G_Char[2],CLK_div2, CLK_div5, Clear, y, p3[2]);
	fallingobject4 A4(G_Char[3],CLK_div2, CLK_div5, Clear, y, p3[3]);
	fallingobject1 A5(G_Char[4],CLK_div2, CLK_div5, Clear, g, p3[4]);
	fallingobject1 A6(G_Char[5],CLK_div2, CLK_div5, Clear, g, p3[5]);
	fallingobject1 A7(G_Char[6],CLK_div2, CLK_div5, Clear, g, p3[6]);
	fallingobject1 A8(G_Char[7],CLK_div2, CLK_div5, Clear, g, p3[7]);
	
	fallingobject3 B1(R_Char[0],CLK_div2, CLK_div5, Clear, r, p4[0]);
	fallingobject3 B2(R_Char[1],CLK_div2, CLK_div5, Clear, r, p4[1]);
	fallingobject4 B3(R_Char[2],CLK_div2, CLK_div5, Clear, y, p4[2]);
	fallingobject4 B4(R_Char[3],CLK_div2, CLK_div5, Clear, y, p4[3]);
	fallingobject3 B5(R_Char[4],CLK_div2, CLK_div5, Clear, r, p4[4]);
	fallingobject3 B6(R_Char[5],CLK_div2, CLK_div5, Clear, r, p4[5]);
	fallingobject3 B7(R_Char[6],CLK_div2, CLK_div5, Clear, r, p4[6]);
	fallingobject3 B8(R_Char[7],CLK_div2, CLK_div5, Clear, r, p4[7]);
	
	
	InitialAni I0(Ini_Char[0],CLK_div2, CLK_div5,i4[0]);
	InitialAni I1(Ini_Char[1],CLK_div2, CLK_div5,i4[1]);
	InitialAni I2(Ini_Char[2],CLK_div2, CLK_div5,i4[2]);
	InitialAni I3(Ini_Char[3],CLK_div2, CLK_div5,i4[3]);
	InitialAni I4(Ini_Char[4],CLK_div2, CLK_div5,i4[4]);
	InitialAni I5(Ini_Char[5],CLK_div2, CLK_div5,i4[5]);
	InitialAni I6(Ini_Char[6],CLK_div2, CLK_div5,i4[6]);
	InitialAni I7(Ini_Char[7],CLK_div2, CLK_div5,i4[7]);
	
	InitialAni Ig0(Ini2_Char[0],CLK_div2, CLK_div5,i3[0]);
	InitialAni Ig1(Ini2_Char[1],CLK_div2, CLK_div5,i3[1]);
	InitialAni Ig2(Ini2_Char[2],CLK_div2, CLK_div5,i3[2]);
	InitialAni Ig3(Ini2_Char[3],CLK_div2, CLK_div5,i3[3]);
	InitialAni Ig4(Ini2_Char[4],CLK_div2, CLK_div5,i3[4]);
	InitialAni Ig5(Ini2_Char[5],CLK_div2, CLK_div5,i3[5]);
	InitialAni Ig6(Ini2_Char[6],CLK_div2, CLK_div5,i3[6]);
	InitialAni Ig7(Ini2_Char[7],CLK_div2, CLK_div5,i3[7]);
	
	InitialAni Ib0(Ini3_Char[0],CLK_div2, CLK_div5,i2[0]);
	InitialAni Ib1(Ini3_Char[1],CLK_div2, CLK_div5,i2[1]);
	InitialAni Ib2(Ini3_Char[2],CLK_div2, CLK_div5,i2[2]);
	InitialAni Ib3(Ini3_Char[3],CLK_div2, CLK_div5,i2[3]);
	InitialAni Ib4(Ini3_Char[4],CLK_div2, CLK_div5,i2[4]);
	InitialAni Ib5(Ini3_Char[5],CLK_div2, CLK_div5,i2[5]);
	InitialAni Ib6(Ini3_Char[6],CLK_div2, CLK_div5,i2[6]);
	InitialAni Ib7(Ini3_Char[7],CLK_div2, CLK_div5,i2[7]);
	
	InitialAni wg0(Win_Char[0],CLK_div2, CLK_div5,w3[0]);
	InitialAni wg1(Win_Char[1],CLK_div2, CLK_div5,w3[1]);
	InitialAni wg2(Win_Char[2],CLK_div2, CLK_div5,w3[2]);
	InitialAni wg3(Win_Char[3],CLK_div2, CLK_div5,w3[3]);
	InitialAni wg4(Win_Char[4],CLK_div2, CLK_div5,w3[4]);
	InitialAni wg5(Win_Char[5],CLK_div2, CLK_div5,w3[5]);
	InitialAni wg6(Win_Char[6],CLK_div2, CLK_div5,w3[6]);
	InitialAni wg7(Win_Char[7],CLK_div2, CLK_div5,w3[7]);
	
	InitialAni lr0(Lose_Char[0],CLK_div2, CLK_div5,l4[0]);
	InitialAni lr1(Lose_Char[1],CLK_div2, CLK_div5,l4[1]);
	InitialAni lr2(Lose_Char[2],CLK_div2, CLK_div5,l4[2]);
	InitialAni lr3(Lose_Char[3],CLK_div2, CLK_div5,l4[3]);
	InitialAni lr4(Lose_Char[4],CLK_div2, CLK_div5,l4[4]);
	InitialAni lr5(Lose_Char[5],CLK_div2, CLK_div5,l4[5]);
	InitialAni lr6(Lose_Char[6],CLK_div2, CLK_div5,l4[6]);
	InitialAni lr7(Lose_Char[7],CLK_div2, CLK_div5,l4[7]);
	
	music M0(start,wrong,over,clear,CLK_div6,CLK,beep,End);
	bit [2:0] cnt;
	
	initial
	begin
		cnt=0;
		over=0;
		start=0;
		clear=0;
		score1 <= 4'b0000;
		score2 <= 4'b0000;
		DATA_R=8'b11111111;
		DATA_G=8'b11111111;
		DATA_B=8'b11111111;
		COMM=4'b1000;
		hp<=6'b111111;
		wrong=0;
		End=0;
	end
	
	always @(posedge CLK_div)
	begin 
		if(cnt >= 7)
			cnt=0;
		else
			cnt=cnt+1;	 
		
		if(clear)
		begin
		cnt=0;
		start=0;
		clear=0;
		DATA_R=8'b11111111;
		DATA_G=8'b11111111;
		DATA_B=8'b11111111;
		end
		
		if(start)
		begin
			COMM={1'b1,cnt};
			if(End==1)
			begin
			DATA_R=8'b11111111;
			DATA_B=8'b11111111;
			DATA_G<=~w3[cnt];
			if(b==1|g==1|r==1|y==1) clear=1;
			end
			else if(over==1)
			begin
			DATA_G=8'b11111111;
			DATA_B=8'b11111111;
			DATA_R<=~l4[cnt];
			if(b==1|g==1|r==1|y==1) clear=1;
			end
			else
			begin
			DATA_B<=~p2[cnt];
			DATA_G<=~p3[cnt];
			DATA_R<=~p4[cnt];
			end
		end
		else
		begin
			COMM={1'b1,cnt};
			DATA_B<=~i2[cnt];
			DATA_G<=~i3[cnt];
			DATA_R<=~i4[cnt];
			if(b==1|g==1|r==1|y==1) start=1;
		end
end
	
	always @(posedge CLK_div4)
	begin 
		if(clear)
		begin	
			score1 <= 4'b0000;
			score2 <= 4'b0000;
		end
		else
		begin
			if((p2[6]<10&&p2[6]>1&&p2[6]!=3&&b==1)|(p3[2]<10&&p3[2]>1&&p3[2]!=3&&y==1)|(p3[4]<10&&p3[4]>1&&p3[4]!=3&&g==1)|(p4[0]<10&&p4[0]>1&&p4[0]!=3&&r==1))
			begin	
				if(score2<4'b1001) score2 <= score2 + 1'd1; 
				else
				begin
					if(score1<4'b1001) 
					begin
						score2<=4'b0000;
						score1<=score1+1'd1;
					end
				end
			end
		end
	end
	
	
	always@(posedge CLK_div3)
   begin
	   COM<=~COM;
		if(COM)
		begin
			score<=score2;
			COM1<=1;
			COM2<=0;
		end
		else
		begin
			score<=score1;
			COM1<=0;
			COM2<=1;
		end
		   A = (score==1|score==4|score==6);
	      B = (score==5|score==6);
			C = (score==2);
			D = (score==1|score==4|score==7|score==9);
			E = ~(score==0|score==2|score==6|score==8);
			F = (score==1|score==2|score==3|score==7);
			G = (score==0|score==1|score==7);
   end
		
	always@(posedge CLK_div2)
	begin
		/*if(over)
		begin
			hp<=6'b111111;
			over=0;
		end
		else
		begin*/
			if(((p2[6]>10&&b==1)|p2[6]==3)|((p3[2]>10&&y==1)|p3[2]==3)|((p3[4]>10&&g==1)|p3[4]==3)|((p4[0]>10&&r==1)|p4[0]==3))
			begin
	      hp <= {1'b0,hp[5:1]};
			wrong=1;
			end
			else wrong=0;
			
			if(hp==0)
			over=1;
			if(clear) 
			begin
			wrong=0;
			over=0;
			hp<=6'b111111;
			end
	end
	
endmodule

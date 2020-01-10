# Read
# Authors: 107321037 107321038 107321027
 input/output
  >8x8 LED點矩陣用來顯示遊戲畫面  
  
  ![image](https://github.com/chien119/Read/blob/master/S__8093701.jpg)
  >七段顯示器 顯示得分  
  
  ![image](https://github.com/chien119/Read/blob/master/S__8093700.jpg)
  >LED陣列 顯示生命  
  
  ![image](https://github.com/chien119/Read/blob/master/S__8093698.jpg)
# 功能說明:
  音樂遊戲，當音符落到白色判定線時按下對應的按鍵來消除音符，若超過判定線則喪失一條生命，判定線往上兩格為得分範圍，在音樂結束前還有剩餘生命為過關，反之則失敗，結束後按任意鍵可重新開始。
  
# Demo Video:
 [![圖片alt到底三小]()](https://drive.google.com/open?id=1-F3nApAUea7RKSlBZKCxjyOTw6SwGkof)
# 程式模組說明
 module aa(output reg beep//音樂, output reg [7:0] DATA_R,DATA_G,DATA_B//紅 綠 藍燈, output reg [3:0] COMM, output reg [5:0]hp//生命,input CLK,Clear, r, g, b, y//紅 綠 藍 黃音符對應按鍵,output reg A,B,C,D,E,F,G,COM1,COM2//七段顯示器計分);
>DATA_R DATA_G DATA_B ->8x8點矩陣
>beep->beep
>hp->LED陣列
>r g b y->4-bit SW
>COMM->8x8點矩陣連接阜

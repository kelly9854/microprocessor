#include<reg51.h>
sbit p33 = P3^3;
sbit p34 = P3^4;

sbit r0 = P0^0;		//row0
sbit r1 = P0^1;		//row1
sbit r2 = P0^2;		//row2
sbit r3 = P0^3;		//row3
sbit c0 = P0^4;		//column0
sbit c1 = P0^5;		//column1
sbit c2 = P0^6;		//column2
       //키패드와 7-segment 출력위치를 나타내는 비트 정의
char key;
char get(void);
char col(void);
void display(char seg, char ro);
void delay(int time);
void phone();

void main(void){
	char x1, x2, x3, x4;
	while(1) { //무한반복
	
	x1=get(); //t=key하여 t를 return시켰으므로 key가 return되어 x1에 저장
		if(x1 == 0) {			//‘#’key를 눌렀을 때 시작
			x2 = get();		//두 번째 키패드 값을 x2에 저장
		if(x2 == 2) phone();		//‘*’key를 눌렀을 때
		else	x3 = get();		//세번째 키패드를 x3에 저장
			
		if(x3 == 2) phone();		//‘*’key 를 눌렀을 때		
		else	x4 = get();		//네번째 키패드를 x4에 저장

		if(x4 == 2) phone(); 		//‘*’key를 눌렀을 때
		}
	}	
}
					
			
void phone(){
			display(1,100);
			delay(300);
			
			display(2,200);
			delay(300);
			
			display(3,300);
			delay(300);
			
			display(4,300);
			delay(300);
}
char get(void) {			//키패드로부터 입력을 받는 함수(row비교)

	char t;
		
		r0 = 1;		//row 초기값 설정
		r1 = 1;
		r2 = 1;
		r3 = 1;
		
		while(1) {
			key = 0;		//눌린 키패드가 어디인지 알려주는 변수로 key를 두고 초기화
				//row0 비교
			r0 = 0;
			r1 = 1;
			r2 = 1;
			r3 = 1;
			if(col() == 1)
				break;
				//row1 비교
			r0 = 1;
			r1 = 0;
			r2 = 1;
			r3 = 1;
			if(col() == 1)
				break;
				//row2비교
			r0 = 1;
			r1 = 1;
			r2 = 0;
			r3 = 1;
			if(col() == 1)
				break;
				//row3비교
			r0 = 1;
			r1 = 1;
			r2 = 1;
			r3 = 0;
			if(col() == 1)
				break;
		}
		display(1, key);			//키패드의 누른 key를 출력
		t = key;
		while(col());
		return t;
}

char col(void) {				//키패드 입력 받는 함수 (column)
					//키패드가 눌려졌으면 1이 반환되어 get함수의 반복문 break시킴
		if(c0 == 0)		//row와 column 0 비교
			return 1;
		else key++;
		
		if(c1 == 0)		//row와 column 1 비교
			return 1;
		else key++;
		
		if(c2 == 0)		//row와 column 2 비교
			return 1;
		else key++;
		
		return 0;
}

void display(char seg, char ro) {	//7-segment에 출력하는 함수
	P1 = 0xFF;	
	
	switch(seg) {			//7-seg의 출력위치를 결정
		case 1: p33 = 1; p34 = 1; break; //display3
		case 2: p33 = 0; p34 = 1; break; //display2
		case 3: p33 = 1; p34 = 0; break; //display1
		case 4: p33 = 0; p34 = 0; break; //display0		
	}
	
	switch(ro) {			//출력할 문자를 table형식으로 정리
//키패드의 문자 출력하는 경우
		case 0: { P1 = 0xBF; break;}		//#->-출력
		case 1: { P1 = 0xC0; break;}		//0
		case 2 : { P1 = 0x7F; break;}		//*
		case 3 : { P1 = 0x98; break;}		//9
		case 4 : { P1 = 0x80; break;}		//8
		case 5 : { P1 = 0xD8; break;}		//7
		case 6 : { P1 = 0x82; break;}		//6
		case 7 : { P1 = 0x92; break;}		//5
		case 8 : { P1 = 0x99; break;}		//4
		case 9 : { P1 = 0xB0; break;}		//3
		case 10 : { P1 = 0xA4; break;}		//2
		case 11 : { P1 = 0xF9; break;}		//1
//추가적인 문자 출력
		case 100 : { P1 = 0x8E; break;} //C
		case 200 : { P1 = 0x88; break;} //A
		case 300 : { P1 = 0xC7; break;} //L
		
		}
		
}

void delay(int time) {			//딜레이함수
	int i;
	for(i=0; i<time; i++);
}

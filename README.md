# Interfacing-Seven-segment-display-with-lpc2148

Name: M.Vidya Neela	
Roll no : 212221230120
Date of experiment:



Ex. No. :8
Date: 
 

### Aim: To configure and display 4 character LED seven segment display and write a c code for displaying number 1 to 9 and A to F 
### Components required: Proteus ISIS professional suite, Kiel μ vision 5 Development environment 
 ![image](https://user-images.githubusercontent.com/36288975/201021692-efa39349-1a3c-4737-aadc-1843b954c78d.png)
Figure-01 Internal circuit for seven segment MPX4 display



### Theory: 
	7 Segment Display has seven segments in it and each segment has one LED inside it to display the numbers by lighting up the corresponding segments. Like if you want the 7-segment to display the number "5" then you need to glow segment a,f,g,c, and d by making their corresponding pins high. There are two types of 7-segment displays: Common Cathode and Common Anode, here we are using Common Cathode seven segment display.
   ![image](https://user-images.githubusercontent.com/36288975/201021740-565b47cd-26d8-4e54-a092-eef7a0a85278.png)
 
          Figure-02 Pin configuration for seven segment display  


Below table shows the HEX values and corresponding digit according to LPC2148 pins for common cathode configuration.



Sl no 	Hex code 	Output of LCD
1	0x88	1
2	0xeb	2
3	0x4c	3
4	0x49	4
5	0x2b	5
6	0x19	6
7	0x18	7
8	0xcb	8
9	0x8	9
10	0x9	A
11	0xa	B
12	0x38	C
13	0x9c	D
14	0x68	E
15	0x1c 	F
16	0x1e	0

 

![image](https://user-images.githubusercontent.com/36288975/201021930-7efe2b15-b0de-4d52-b87d-329fe6b91c89.png)
        Figure -3 Circuit diagram of interfacing for LPX4 - CA

## Kiel - Program 
```
 #include <lpc214x.h>            //Header file for LPC214x Series microcontrollers

void delay(int );              //Function declaration for delay

int i;                         //Variable declared as integer

unsigned int a[]={0x86,0xf9,0xa4,0xb0,0x99,0x92,0x82,0xf8,0x80, 0x90}; //integer array with numbers for display

int main()

{ 

    IO0DIR=0xffffffff;              //Sets direction as output for PORT 0 pins

    while(1)

    {

        for(i=0;i<=9;i++)

        {

            IO0SET=a[i];           //sets corresponding pins HIGH

            delay(9000);                  //Calls delay function

            IO0CLR=a[i];           //Sets corresponding pins LOW

        }

    }

    return 0;

}


void delay(int k)              //Function for making delay

{

    int i,j;

    for(i=0;i<k;i++)

    for(j=0;j<=1000;j++);
![Screenshot (88)](https://user-images.githubusercontent.com/93427345/201479509-3cff34fe-7622-4320-84be-de1e505b88fb.png)

}
```
##  Output screen shots :
#### DISPLAY OFF:
![201479309-d9294b81-18cd-42f0-90dc-6105838ef801](https://user-images.githubusercontent.com/94169318/202906916-321f1412-9ba2-43a1-81ef-99aad107a9e6.png)

#### DISPLAY ON:
![201479525-82d58d39-b6e8-4398-aa5b-e27a2ef5b805](https://user-images.githubusercontent.com/94169318/202906943-e5622666-0175-4b15-aee9-d8e5d0437cd6.png)

### Result :
LED seven segment display is interfaced and displayed alpha numeric characters 



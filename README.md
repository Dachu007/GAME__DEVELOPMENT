## EX 5 : TWO DIMENSIONALTRANSFORMATION 

Name:Dharshini S

Reg No:212224040074

**AIM**

To write a c program to implement 2D transformation of image.


**ALGORITHM**

Step 1:Start the program.

Step 2:Draw the image with default parameters.

Step 3 : Get the choice from the user.

Step 4: Get the parameters for transformation.

Step 5 : Perform the transformation.

Step 6 : Draw the image.

Step 7 : Stop the program.


**Program :**
```
 # include<graphics.h> 
 # include<stdio.h> 
 # include<conio.h> 
 # include<math.h> 
 
 void main() 
 { 
   int gd=DETECT,gm,i,j,k,ch; 
   float tx,ty,x,y,ang,n,temp; 
   float  a[5][3],si,co,b[5][3],c[5][3]; 
 
   initgraph(&gd,&gm,"e:\\tcpp\\bgi"); 
      n=4; 
   a[0][0]=0;    a[0][1]=0;   a[1][0]=100;  a[1][1]=0; 
   a[2][0]=100;  a[2][1]=100; a[3][0]=0;    a[3][1]=100; 
   a[4][0]=0;    a[4][1]=0; 
   while(1) 
   { 
    cleardevice(); 
    gotoxy(1,8); 
    printf("\n\t******** Program to perform 2-D Transformations ********"); 
    printf("\n\t\t\t 1. Accept the polygon"); 
    printf("\n\t\t\t 2. Perform translation"); 
    printf("\n\t\t\t 3. Perform scaling"); 
    printf("\n\t\t\t 4. Perform rotation"); 
    printf("\n\t\t\t 5. Perform reflection");
    printf("\n\t\t\t 6. Perform shearing"); 
    printf("\n\t\t\t 7. Exit"); 
    printf("\n\t\t\t Enter your choice::"); 
    scanf("%d",&ch); 
    switch(ch) 
    { 
     case 1: 
       cleardevice(); 
       gotoxy(1,1); 
       printf("\n\tEnter no of points.:"); 
       scanf("%f",&n); 
       for(i=0;i<n;i++) 
 { 
   printf("\n\t Enter x,y co-ordinates for %d::",i+1); 
   scanf("%f %f",&a[i][0],&a[i][1]); 
  } 
       a[i][0]=a[0][0]; 
       a[i][1]=a[0][1]; 
      cleardevice(); 
      for(i=0;i<n;i++) 
      line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
      line(0,240,639,240); 
      line(320,0,320,479); 
      getch(); 
      break; 
 
    case 2: 
      cleardevice();
      for(i=0;i<n;i++) 
      line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
      line(0,240,639,240); 
      line(320,0,320,479); 
       gotoxy(1,1); 
       printf("Enter translation vectors tx and ty\n\t"); 
       scanf("%f %f",&x,&y); 
       cleardevice(); 
  for(i=0;i<n;i++) 
  line(320+a[i][0]+x,240-(a[i][1]+y),320+a[i+1][0]+x,240-(a[i+1][1]+y)); 
  line(0,240,639,240); 
  line(320,0,320,479); 
  getch(); 
       break; 
 
    case 3: 
           cleardevice(); 
      for(i=0;i<n;i++) 
      line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
      line(0,240,639,240); 
      line(320,0,320,479); 
     gotoxy(1,1); 
     printf("Enter scaling vectors tx and ty\n\t"); 
     scanf("%f %f",&x,&y); 
     if(x==0) 
     x=1; 
     if(y==0)
   y=1; 
       cleardevice(); 
  for(i=0;i<n;i++) 
  line(320+(a[i][0]*x),240-(a[i][1]*y),320+(a[i+1][0]*x),240-(a[i+1][1]*y)); 
  line(0,240,639,240); 
  line(320,0,320,479); 
  getch(); 
  break; 
 
  case 4: 
      cleardevice(); 
      for(i=0;i<n;i++) 
      line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
      line(0,240,639,240); 
      line(320,0,320,479); 
     gotoxy(1,1); 
     printf("Enter the angle of rotation\n\t"); 
     scanf("%f",&ang); 
     ang=ang*0.01745; 
     gotoxy(1,3); 
     printf("Enter point of rotation\n\t"); 
     scanf("%f %f",&x,&y); 
     gotoxy(1,5); 
     printf("1.clockwise  2.anticlockwise\n\t"); 
     scanf("%d",&k); 
     si=sin(ang); 
     co=cos(ang);
     for(i=0;i<n+1;i++) 
 { 
   c[i][0]=a[i][0]; 
   c[i][1]=a[i][1]; 
   c[i][2]=1; 
 } 
           b[0][0]=co; 
      b[0][1]=si; 
      b[0][2]=0; 
      b[1][0]=(-si); 
      b[1][1]=co; 
      b[1][2]=0; 
      b[2][0]=(-x*co)+(y*si)+x; 
      b[2][1]=(-x*si)-(y*co)+y; 
      b[2][2]=1; 
           if(k==1) 
      { 
 b[0][1]=(-si); 
 b[1][0]=(si); 
 b[2][0]=(-x*co)-(y*si)+x; 
 b[2][1]=(-x*si)+(y*co)+y; 
      } 
 
     for(i=0;i<n+1;i++) 
    { 
       for(j=0;j<3;j++) 
   { 
     a[i][j] = 0 ;
      for(k=0;k<3;k++) 
     a[i][j] = a[i][j] + c[i][k] * b[k][j] ; 
   } 
     } 
 
     cleardevice(); 
     for(i=0;i<n;i++) 
       line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
       line(0,240,639,240); 
       line(320,0,320,479); 
       getch(); 
       break; 
 
    case 5: 
      cleardevice(); 
      for(i=0;i<n;i++) 
      line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
      line(0,240,639,240); 
      line(320,0,320,479); 
      gotoxy(1,1); 
      printf("\n1.Reflection about Y-axis"); 
      printf("\n2.Reflection about X-axis"); 
      printf("\n3.Reflection about origin"); 
      printf("\n4.Reflection about line y=x"); 
      printf("\n5.Reflection about line y=-x"); 
      printf("\nEnter your choice:"); 
      scanf("%d",&ch);
       switch(ch) 
      { 
  case 1: 
      for(i=0;i<n+1;i++) 
        a[i][0]=a[i][0]*(-1); 
       /* Plot the polygon */ 
       cleardevice(); 
       for(i=0;i<n;i++) 
       line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
       line(0,240,639,240); 
       line(320,0,320,479); 
       getch(); 
       break; 
 
   case 2: 
       for(i=0;i<n+1;i++) 
        a[i][1]=a[i][1]*(-1); 
        cleardevice(); 
       for(i=0;i<n;i++) 
       line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
       line(0,240,639,240); 
       line(320,0,320,479); 
       getch(); 
    break; 
 
  case 3: 
      for(i=0;i<n+1;i++) 
      {
          a[i][1]=a[i][1]*(-1); 
        a[i][0]=a[i][0]*(-1); 
      } 
        cleardevice(); 
       for(i=0;i<n;i++) 
       line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
       line(0,240,639,240); 
       line(320,0,320,479); 
       getch(); 
    break; 
 
   case 4: 
      for(i=0;i<n+1;i++) 
      { 
       temp=a[i][0]; 
       a[i][0]=a[i][1]; 
       a[i][1]=temp; 
      } 
       cleardevice(); 
       for(i=0;i<n;i++) 
       line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
       line(0,240,639,240); 
       line(320,0,320,479); 
       line(0,479,639,0); 
       getch(); 
    break; 
 
   case 5:
      for(i=0;i<n+1;i++) 
      { 
       temp=a[i][0]; 
       a[i][0]=a[i][1]; 
       a[i][1]=temp; 
      } 
     
              for(i=0;i<n+1;i++) 
      { 
        a[i][1]=a[i][1]*(-1); 
        a[i][0]=a[i][0]*(-1); 
      } 
              cleardevice(); 
       for(i=0;i<n;i++) 
       line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
       line(0,240,639,240); 
       line(320,0,320,479); 
       line(0,0,639,479); 
       getch(); 
    break; 
  default: 
    break; 
      } 
      break; 
 
    case 6: 
       cleardevice(); 
      for(i=0;i<n;i++)
       line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]); 
      line(0,240,639,240); 
      line(320,0,320,479); 
      gotoxy(1,1); 
      printf("\n1.X shear with y reference line"); 
      printf("\n2.Y shear with x reference line"); 
 
 
      printf("\nEnter your choice:"); 
      scanf("%d",&ch); 
      switch(ch) 
      { 
 
       case 1: 
       printf("\nEnter the x-shear parameter value:"); 
      scanf("%f",&temp); 
      printf("\nEnter the yref line"); 
      scanf("%f",&ty); 
       b[0][0]=1; 
      b[0][1]=0; 
      b[0][2]=0; 
      b[1][0]=temp; 
      b[1][1]=1; 
      b[1][2]=0; 
      b[2][0]=(-temp)*(ty); 
      b[2][1]=0; 
      b[2][2]=1;
        for(i=0;i<n+1;i++) 
     a[i][2]=1; 
  
  for(i=0;i<n+1;i++) 
    { 
       for(j=0;j<3;j++) 
   { 
     c[i][j] = 0 ; 
     for(k=0;k<3;k++) 
     c[i][j] = c[i][j] + a[i][k] * b[k][j] ; 
   } 
     } 
 
     cleardevice(); 
     for(i=0;i<n;i++) 
       line(320+c[i][0],240-c[i][1],320+c[i+1][0],240-c[i+1][1]); 
       line(0,240,639,240); 
       line(320,0,320,479); 
       getch(); 
 break; 
 
       case 2: 
   printf("\nEnter the y-shear parameter value:"); 
   scanf("%f",&temp); 
              printf("\nEnter the xref line"); 
   scanf("%f",&tx); 
                 b[0][0]=1; 
      b[0][1]=temp;
     b[0][2]=0; 
      b[1][0]=0; 
      b[1][1]=1; 
      b[1][2]=0; 
      b[2][0]=0; 
      b[2][1]=(-temp)*(tx); 
      b[2][2]=0; 
     for(i=0;i<n+1;i++) 
     a[i][2]=1; 
  
  for(i=0;i<n+1;i++) 
    { 
       for(j=0;j<3;j++) 
   { 
     c[i][j] = 0 ; 
     for(k=0;k<3;k++) 
     c[i][j] = c[i][j] + a[i][k] * b[k][j] ; 
   } 
     } 
 
          cleardevice(); 
     for(i=0;i<n;i++) 
       line(320+c[i][0],240-c[i][1],320+c[i+1][0],240-c[i+1][1]); 
       line(0,240,639,240); 
       line(320,0,320,479); 
       getch(); 
 break;
   default: break; 
     } 
      break;  
case 7: 
    exit(1); 
    closegraph(); 
    restorecrtmode(); 
    break; 
    default: break; 
    } 
  }
}
```



**Output :**

## 1.Accept the polygon

<img width="632" height="505" alt="Screenshot 2025-09-22 172619" src="https://github.com/user-attachments/assets/ce391186-2ca7-4f00-acff-df09ab05157f" />

<img width="627" height="498" alt="Screenshot 2025-09-22 172648" src="https://github.com/user-attachments/assets/4693ae47-8992-482f-998c-c8fbd6204299" />

<img width="637" height="503" alt="Screenshot 2025-09-22 172656" src="https://github.com/user-attachments/assets/f7074d76-4361-44b9-a060-982c2c5b3d0e" />

## 2.Translation

<img width="637" height="503" alt="Screenshot 2025-09-22 172708" src="https://github.com/user-attachments/assets/81a4e796-0568-4c87-b6d6-196262948f92" />

<img width="644" height="500" alt="Screenshot 2025-09-22 172825" src="https://github.com/user-attachments/assets/8e79073b-8f14-43e6-8fad-fc374ed3dfa9" />

<img width="646" height="508" alt="Screenshot 2025-09-22 172851" src="https://github.com/user-attachments/assets/a4f6fd43-5e57-4178-9d83-cca79935bf84" />

## 3.Scaling

<img width="630" height="505" alt="Screenshot 2025-09-22 172911" src="https://github.com/user-attachments/assets/be03b8f7-dacc-4230-83b4-99bff0c2f26b" />

<img width="636" height="505" alt="Screenshot 2025-09-22 173034" src="https://github.com/user-attachments/assets/98560a21-5de7-4ff2-91a5-3ce62f5dea02" />

<img width="632" height="513" alt="Screenshot 2025-09-22 173041" src="https://github.com/user-attachments/assets/d4ff5163-d562-4fe7-9706-23309828d63b" />

## 4.Rotation

<img width="639" height="514" alt="Screenshot 2025-09-22 173051" src="https://github.com/user-attachments/assets/dc1ebb70-2f89-440b-82f4-0fbfcfdbf00d" />

<img width="642" height="505" alt="Screenshot 2025-09-22 173124" src="https://github.com/user-attachments/assets/2326fc61-be50-47d0-ba62-e95cffb05f01" />

<img width="639" height="506" alt="Screenshot 2025-09-22 173133" src="https://github.com/user-attachments/assets/b2c87408-4534-41f3-8a78-6159c12ec3d0" />

## 5.Reflection

<img width="629" height="504" alt="Screenshot 2025-09-22 173157" src="https://github.com/user-attachments/assets/c65e9431-4790-4f77-bdbd-82d7717e3dcd" />

<img width="639" height="508" alt="Screenshot 2025-09-22 173235" src="https://github.com/user-attachments/assets/5419d04e-3232-454f-b365-7a1c1afcc73a" />

<img width="640" height="504" alt="Screenshot 2025-09-22 173241" src="https://github.com/user-attachments/assets/5c2320fb-f25c-46d4-aaee-c3c70a91a848" />

## 6.Shearing

<img width="631" height="499" alt="Screenshot 2025-09-22 173308" src="https://github.com/user-attachments/assets/01f50882-85b0-4e5a-b2ab-4c21c3d63815" />

<img width="639" height="498" alt="Screenshot 2025-09-22 173344" src="https://github.com/user-attachments/assets/404dce93-c1d9-4820-adaa-1ba3b32dba1f" />

<img width="649" height="503" alt="Screenshot 2025-09-22 173353" src="https://github.com/user-attachments/assets/5830d473-3e30-40f9-8bf6-c1f477f41a43" />




















**Result :**


Successfully completed a C program to implement 2D transformation of image.

# Railyways-Reservation-System
Railways Reservation System was done using C Programming language. This is My 3rd Semester Mini Project. Features are: Login System ,easy ticket reservation, View All trains Details also arrival and departure Time, Information show after ticket done, cancel ticket option etc.
//including all libraries
#include<stdio.h>
#include<conio.h>
#include<stdlib.h>
#include<string.h>

//ALl the globle variables and the composite data types will be declared here
typedef struct{
	char name[50];
	int train_num;
	int num_of_seats;
}pd;




void reservation(void);						
void viewdetails(void);					
void cancel(void);								
void printticket(char name[],int,int,float);	
void specifictrain(int);						
float charge(int,int);							
void login();



int main()

{
		system("cls"); 
	printf("\t\t=================================================\n");
	printf("\t\t|                                               |\n");
	printf("\t\t|        -----------------------------          |\n");
	printf("\t\t|           RAILWAYS RERS. SYSTEM               |\n");
	printf("\t\t|        -----------------------------          |\n");
	printf("\t\t|                                               |\n");
	printf("\t\t|                                               |\n");
	printf("\t\t|                                               |\n");
	printf("\t\t|              MINI PROJECT                     |\n");
	printf("\t\t|           |  Group C-project  |               |\n");
	printf("\t\t|                                               |\n");
	printf("\t\t=================================================\n\n\n");
		
	    
	printf(" \n Press any key to continue:");
	
	getch();	
    system("cls");
	login();
	int menu_choice,choice_return;
	start:
	system("cls");
	printf("\n=================================\n");
	printf("    TRAIN RESERVATION SYSTEM");
	printf("\n=================================");
	printf("\n1>> Reserve A Ticket");
	printf("\n------------------------");
	printf("\n2>> View All Available Trains");
	printf("\n------------------------");
	printf("\n3>> Cancel Reservation");
	printf("\n------------------------");
	printf("\n4>> Exit");
	printf("\n------------------------");
	printf("\n\n-->");
	scanf("%d",&menu_choice);
	switch(menu_choice)
	{
		case 1:
			reservation();	
			break;
		case 2:
			viewdetails();
			printf("\n\nPress any key to go to Main Menu..");
			getch();
			break;
		case 3:
			cancel();
			
			break;
		case 4:
			return(0);
		default:
			printf("\nInvalid choice");
	}
	goto start;
	return(0);
}


void viewdetails(void)
{
	system("cls");
	printf("-----------------------------------------------------------------------------");	
	printf("\nTr.No\tName\t\t\tDestinations\t\tCharges\t\tTime\n");
	printf("-----------------------------------------------------------------------------");
	printf("\n12301\tRajdhani Express\tHWH to NDLS\t\tRs.5000\t\t16:50");
	printf("\n12245\tDuronto Express\t\tHWH To YPR\t\tRs.5000\t\t10:50");
	printf("\n22439\tVande Bharat Express\tNDLS To SVDK\t\tRs.4500\t\t6:00");
	printf("\n12215\tGarib Rath Express\tDEE To BDTS\t\tRs.4500\t\t8:55");
          printf("\n22119\tTejas Express\t\tCSMT To KRMI\t\tRs.4000\t\t5:50");
	printf("\n12814\tSteel Express\t\tTATA To HWH\t\tRs.4000\t\t6:10");
    printf("\n12802\tPurushottam Express\tNDLS To PURI\t\tRs.3500\t\t10:40");	
    printf("\n13307\tGanga Sutlej Express\tDHN To FZR\t\tRs.3500\t\t9:50");
    printf("\n12050\tGatiman Express\t\tNZM To JHS\t\tRs.6000\t\t8:10");
    printf("\n12365\tJan Shatabdi Express\tPNBE To RNC\t\tRs.6000\t\t6:10");
    
}


void reservation(void)
{
	char confirm;
	int i=0;
	float charges;
	pd passdetails;
	FILE *fp;
	fp=fopen("seats_reserved.txt","a");
	system("cls");
	
	printf("\nEnter Your Name:> ");
	fflush(stdin);
	gets(passdetails.name);
	
	printf("\nEnter Number of seats:> ");
	scanf("%d",&passdetails.num_of_seats);
	printf("\n\n>>Press Enter To View Available Trains<< ");
	getch();
	system("cls");
	viewdetails();
	printf("\n\nEnter train number:> ");
	start1:
	scanf("%d",&passdetails.train_num);
	if(passdetails.train_num>=12050 && passdetails.train_num<=22439)
	{
		charges=charge(passdetails.train_num,passdetails.num_of_seats);
		printticket(passdetails.name,passdetails.num_of_seats,passdetails.train_num,charges);		
	}
	else
	{
		printf("\nInvalid train Number! Enter again--> ");
		goto start1;
	}
	
	printf("\n\nConfirm Ticket (y/n):>");
	start:
	scanf(" %c",&confirm);
	if(confirm == 'y')
	{
		fprintf(fp,"%s\t\t%d\t\t%d\t\t%.2f\n",&passdetails.name,passdetails.num_of_seats,passdetails.train_num,charges);
		printf("==================");
		printf("\n Reservation Done\n");
		printf("==================");
		printf("\nPress any key to go back to Main menu");
	}
	else
	{
		if(confirm=='n'){
			printf("\nReservation Not Done!\nPress any key to go back to  Main menu!");
		}
		else
		{
			printf("\nInvalid choice entered! Enter again-----> ");
			goto start;
		}
	}
	fclose(fp);
	getch();
}


float charge(int train_num,int num_of_seats)
{
		if (train_num==12301)
	{
		return(5000.0*num_of_seats);
	}
	if (train_num==12245)
	{
		return(5000.0*num_of_seats);
	}
	if (train_num==22439)
	{
		return(4500.0*num_of_seats);
	}
	if (train_num==12215)
	{
		return(4500.0*num_of_seats);
	}
	if (train_num==22119)
	{
		return(4000.0*num_of_seats);
	}
	if (train_num==12814)
	{
		return(4000.0*num_of_seats);
	}
	if (train_num==12802)
	{
		return(3500.0*num_of_seats);
	}
	if (train_num==13307)
	{
		return(3500.0*num_of_seats);
	}
	if (train_num==12050)
	{
		return(6000.0*num_of_seats);
	}
	if(train_num==12365)
	{
		return(6000.0*num_of_seats);
	}
}

void printticket(char name[],int num_of_seats,int train_num,float charges)
{
	system("cls");
	printf("-------------------\n");
	printf("\tTICKET\n");
	printf("-------------------\n\n");
	printf("Name:\t\t\t%s",name);
	printf("\nNumber Of Seats:\t%d",num_of_seats);
	printf("\nTrain Number:\t\t%d",train_num);
	specifictrain(train_num);
	printf("\nCharges:\t\t%.2f",charges);
}


void specifictrain(int train_num)
{
	
	if (train_num==12301)
	{
		printf("\nTrain:\t\t\tRajdhani Express");
		printf("\nDestination:\t\tHWH to NDLS");
		printf("\nDeparture:\t\t16:50");
	}
	if (train_num== 12245)
	{
		printf("\nTrain:\t\t\t Duronto Express");
		printf("\nDestination:\t\tHWH To YPR");
		printf("\nDeparture:\t\t10:50");
	}
	if (train_num==22439)
	{
		printf("\nTrain:\t\t\tVande Bharat Express");
		printf("\nDestination:\t\tNDLS To SVDK");
		printf("\nDeparture:\t\t6:00");
	}
	if (train_num==12215)
	{
		printf("\nTrain:\t\t\tGarib Rath Express");
		printf("\nDestination:\t\tDEE To BDTS");
		printf("\nDeparture:\t\t11:55");
	}
	if (train_num==22119)
	{
		printf("\nTrain:\t\t\tTejas Express");
		printf("\nDestination:\t\tCSMT To KRMI");
		printf("\nDeparture:\t\t5:50");
	}
	if (train_num==12814)
	{
		printf("\ntrain:\t\t\tSteel Express");
		printf("\nDestination:\t\tTATA To HWH");
		printf("\nDeparture:\t\t6:10");
	}
	if (train_num==12802)
	{
		printf("\ntrain:\t\t\tPurushottam Express");
		printf("\nDestination:\t\tNDLS to PURI");
		printf("\nDeparture:\t\t10:40");
	}
	if (train_num==13307)
	{
		printf("\ntrain:\t\t\tGanga Sutlej Express");
		printf("\n Destination:\t\tDHN To FZR");
		printf("\nDeparture:\t\t9:50");
	}
	if (train_num==12050)
	{
		printf("\ntrain:\t\t\tGatiman Express");
		printf("\nDestination:\t\tNZM To JHS");
		printf("\nDeparture:\t\t8:10");
	}
	if (train_num==12365)
	{
		printf("\ntrain:\t\t\tJan Shatabdi Express");
		printf("\nDestination:\t\tPNBE To RNC");
		printf("\nDeparture:\t\t6:10");
	}
}

void login()
{
	int a=0,i=0;
    char uname[10],c=' '; 
    char pword[10],code[10];
    char user[10]="user";
    char pass[10]="pass";
    do
{
	
    printf("\n  =======================  LOGIN FORM  =======================\n  ");
    printf(" \n                       ENTER USERNAME:-");
	scanf("%s", &uname); 
	printf(" \n                       ENTER PASSWORD:-");
	while(i<10)
	{
	    pword[i]=getch();
	    c=pword[i];
	    if(c==13) break;
	    else printf("*");
	    i++;
	}
	pword[i]='\0';
	
	i=0;
	
		if(strcmp(uname,"user")==0 && strcmp(pword,"pass")==0)
	{
	printf("  \n\n\n       WELCOME TO OUR SYSTEM !! YOUR LOGIN IS SUCCESSFUL");
	printf("\n\n\n\t\t\t\tPress any key to continue...");
	getch();
	break;
	}
	else
	{
		printf("\n        SORRY !!!!  LOGIN IS UNSUCESSFUL");
		a++;
		
		getch();
		system("cls");
	}
}
	while(a<=2);
	if (a>2)
	{
		printf("\nSorry you have entered the wrong username and password for four times!!!");
		
		getch();
		
		}
		system("cls");	
}

void cancel(void) 
{
	  
	system("cls");
	int trainnum;
	printf("-----------------------\n");
		printf("Enter the train number: \n");
			printf("-----------------------\n");
		fflush(stdin);
		scanf("%i",&trainnum);
		printf("\n\nCancelled");  
		getch();
}


              




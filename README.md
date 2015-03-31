// Friends-talking-algorithm -- Finding the expected pattern match

//Each of 17 students talked with every other student. They all
//talked about three different topics. Each pair of students talked about
//one topic. Prove that there are three students that talked about the same
//topic among themselves.

/*
My designed algorithm inputs all possible combinations of mutual topic talking
and recognizes specific pattern within that generated data, in this case finding 3 people
who talked same topic among themselves. 
*/

#include <stdio.h>
#include <time.h>

int main(void){
	
	int check = 0;
	do{
	srand(time(NULL));
	typedef struct {
		int s1;
		int s2;
		int top;
	}talk;
	
	typedef struct {
		int st1;
		int st2;
	}pair;
	
	talk all[136];
	pair arr1[136];
	pair arr2[136];
	pair arr3[136];
	int i, j, k, z;
	
	for(i = 0; i < 136; i++){
		arr1[i].st1 = -1;
		arr1[i].st2 = -1;
		arr2[i].st1 = -1;
		arr2[i].st2 = -1;
		arr3[i].st1 = -1;
		arr3[i].st2 = -1;
	}
	
	int count = 0;
	for(i = 0; i < 17; i++){
		for(j = i+1; j < 17; j++){
			all[count].s1 = i;
			all[count].s2 = j;
			all[count].top = rand()%3+1;
			count++;
		}
	}
	
	for(i = 0; i < 136; i++){
		printf("s1: %d\t s2: %d\t topic: %d\n", all[i].s1, all[i].s2, all[i].top);
	}
	printf("\n");
	int count1 = 0;
	int count2 = 0;
	int count3 = 0;
	for(i = 0; i < 136; i++){
		if(all[i].top == 1){
			arr1[count1].st1 = all[i].s1;
			arr1[count1].st2 = all[i].s2;
			count1++;
		}
		else if(all[i].top == 2){
			arr2[count2].st1 = all[i].s1;
			arr2[count2].st2 = all[i].s2;
			count2++;
		}
		else if(all[i].top == 3){
			arr3[count3].st1 = all[i].s1;
			arr3[count3].st2 = all[i].s2;
			count3++;
		}
	}
	
	int temp, temp1, temp2, topic;
	int stop = 0;
	for(i = 1; i < 4; i++){
		if(i == 1){
			for(j = 0; j < 136; j++){
				if(arr1[j].st1 != -1){
					temp = arr1[j].st1;
					temp1 = arr1[j].st2;
					for(k = j+1; k < 136; k++){
						if(arr1[k].st1 == temp){
							temp2 = arr1[k].st2;
							for(z = 0; z < 136; z++){
								if(arr1[z].st1 == temp1 && arr1[z].st2 == temp2){
									stop = 1;
									break;
								}
								else if(arr1[z].st1 == temp2 && arr1[z].st2 == temp1){
									stop = 1;
									break;
								}
							}
						}
						else if(arr1[k].st2 == temp){
							temp2 = arr1[k].st1;
							for(z = 0; z < 136; z++){
								if(arr1[z].st1 == temp1 && arr1[z].st2 == temp2){
									stop = 1;
									break;
								}
								else if(arr1[z].st1 == temp2 && arr1[z].st2 == temp1){
									stop = 1;
									break;
								}
							}
						}
						if(stop == 1){
							break;
						}
					}
				}
				if(stop == 1){
					break;
				}
			}
		}
		if(stop == 1){
			topic = i;
			break;
		}
		if(i == 2){
			for(j = 0; j < 136; j++){
				if(arr1[j].st1 != -1){
					temp = arr2[j].st1;
					temp1 = arr2[j].st2;
					for(k = j+1; k < 136; k++){
						if(arr2[k].st1 == temp){
							temp2 = arr2[k].st2;
							for(z = 0; z < 136; z++){
								if(arr2[z].st1 == temp1 && arr2[z].st2 == temp2){
									stop = 1;
									break;
								}
								else if(arr2[z].st1 == temp2 && arr2[z].st2 == temp1){
									stop = 1;
									break;
								}
							}
						}
						else if(arr2[k].st2 == temp){
							temp2 = arr2[k].st1;
							for(z = 0; z < 136; z++){
								if(arr2[z].st1 == temp1 && arr2[z].st2 == temp2){
									stop = 1;
									break;
								}
								else if(arr2[z].st1 == temp2 && arr2[z].st2 == temp1){
									stop = 1;
									break;
								}
							}
						}
						if(stop == 1){
							break;
						}
					}
				}
				if(stop == 1){
					break;
				}
			}
		}
		if(stop == 1){
			topic = i;
			break;
		}
		if(i == 3){
			for(j = 0; j < 136; j++){
				if(arr3[j].st1 != -1){
					temp = arr3[j].st1;
					temp1 = arr3[j].st2;
					for(k = j+1; k < 136; k++){
						if(arr3[k].st1 == temp){
							temp2 = arr3[k].st2;
							for(z = 0; z < 136; z++){
								if(arr3[z].st1 == temp1 && arr3[z].st2 == temp2){
									stop = 1;
									break;
								}
								else if(arr3[z].st1 == temp2 && arr3[z].st2 == temp1){
									stop = 1;
									break;
								}
							}
						}
						else if(arr3[k].st2 == temp){
							temp2 = arr3[k].st1;
							for(z = 0; z < 136; z++){
								if(arr3[z].st1 == temp1 && arr3[z].st2 == temp2){
									stop = 1;
									break;
								}
								else if(arr3[z].st1 == temp2 && arr3[z].st2 == temp1){
									stop = 1;
									break;
								}
							}
						}
						if(stop == 1){
							break;
						}
					}
				}
				if(stop == 1){
					break;
				}
			}
		}
		if(stop == 1){
			topic = i;
			break;
		}
	}
	
	printf("s1: %d\t s2: %d\t s3: %d\t topic: %d\n", temp, temp1, temp2, topic);
	printf("\n");
	printf("Check again? (1 or 0)");
	scanf("%d", &check);
	}while(check == 1);
	
	return 0;
}

---
title: C语言基础独立编程测试
date: 2022-06-13 20:50:00
author: 小粥同学
tags: C语言
---

用户先输入N，再输入N个整数，请输出最小值及所在下标。
测试用例要有全是负数的情况。

```
	int min = MAX;
	int minIndex = -1;
	int n;
	int tmp;
	scanf("%d",&n);
    if(n!=0){
        for(int i = 0 ;i < n; i ++){
            scanf("%d",&tmp);
            if(tmp < min){
                min = tmp;
                minIndex = i;
            }
        }
        printf("%d %d",min,minIndex);
    }
	
```
<!--more-->
用户输入若干个整数（以-1作为结束），请输出最大值及所在下标。
测试用例要有全是负数的情况。
```
	int max = MIN;
	int maxIndex = -1;
	int tmp;
	int count = 0;
	while(scanf("%d",&tmp) && tmp != -1){
		if(tmp > max){
			max = tmp;
			maxIndex = count;
		}
		count ++;
	}
	if(tmp != -1) printf("%d %d",max,maxIndex);
```

所谓素数，是指除了1和它本身，没有任何因子的正整数，2是最小的素数。
用户输入m,n，请找出[m,n]范围内素数的和。
参考测试用例1：[-5 10]
参考测试用例2：[10 23]
```
int isPrime(int n){
	if(n < 2) return 0;
	for(int i = 2; i <= sqrt(n); i++){
		if(n % i == 0) return 0;
	}
	return 1;
}
int main(){
	int m, n;
	scanf("%d %d",&m,&n);
	int sum = 0;
	for(int i = m; i <= n;i ++){
		if(isPrime(i)){
			sum += i;
		}
	}
	printf("%d",sum);
	return 0;
}
```
所谓合数，是指除了1和它本身，至少还有一个因子的正整数，4是最小的合数。
用户输入m,n，请找出[m,n]范围内合数的个数。
参考测试用例1：[-5 10]
参考测试用例2：[10 20]
```
int isHeShu(int n){
	if(n < 4) return 0;
	for(int i = 2; i <= sqrt(n); i++){
		if(n % i == 0) return 1;
	}
	return 0;
}
int main(){
	int m, n;
	scanf("%d %d",&m,&n);
	int sum = 0;
	for(int i = m; i <= n;i ++){
		if(isHeShu(i)){
			sum += i;
		}
	}
	printf("%d",sum);
	return 0;
}
```
用户输入10个数，请输出出现次数最多的数是多少，如果出现次数相同，则输出排在最前面的一个数（如3 5 6 7 5 3 2 2 1 0中，3、5、2都出现2次，但3是最先出现的，所以输出3）
```
int main(){
	int num[10] = {0};
	int maxCount = 0;
	int tmp = 0;
	int maxNum = 0;
	for(int i = 0; i < 10;i ++){
		scanf("%d",&num[i]);
	}
	for(int i = 0; i < 10; i++){
		tmp = 0;
		for(int j = i; j < 10; j ++){
			if(num[j] == num[i]){
				tmp ++;
			}
		}
		if(tmp > maxCount){
			maxCount = tmp;
			maxNum = num[i];
		}
	}
	printf("%d",maxNum);
	return 0;
}
```
用户输入一个4行3列的数组，请输出最大值及其下标。
参考测试用例1：
100 25 67
12 34 12
9 90 87
100 2 5
参考测试用例2：
1 2 3
5 6 7
9 100 2
11 12 13
```
int main(){
	int tmp, max = MIN, maxi = -1, maxj = -1;
	for(int i = 0;i < 4; i++){
		for(int j = 0; j < 3; j++){
			scanf("%d",&tmp);
			if(tmp > max){
				max = tmp;
				maxi = i;
				maxj = j;
			}
		}
	}
	printf("%d %d %d",max,maxi,maxj);
	return 0;
}
```
用户给定一个字符串（长度不超过30），请输出出现次数最多的字符是哪个。如果有多个字符出现次数一样，输出最先出现在字符串中的字符。如bcadaefc，其中a和c的出现次数都是2，但字符串中c先于a出现，所以输出c。
```
int main(){
	char s[31];
	gets(s);
	int maxCount = 0;
	int tmp = 0;
	char maxChar;
	for(int i = 0; i < strlen(s); i++){
		tmp = 0;
		for(int j = i; j < strlen(s); j ++){
			if(s[j] == s[i]){
				tmp ++;
			}
		}
		if(tmp > maxCount){
			maxCount = tmp;
			maxChar = s[i];
		}
	}
	printf("%c",maxChar);
	return 0;
}
```
用户给定一个字符串（不超过30），再输入一个字符，请统计该字符在字符串中的出现次数。
测试用例中要有这个字符的出现次数是0的情况。
```
int main(){
	char s[31];
	gets(s);
	int count = 0;
	char key;
	scanf("%c",&key);
	for(int i = 0; i < strlen(s); i++){
		if(s[i] == key){
			count ++;
		}
	}
	printf("%d",count);
	return 0;
}
```
用户输入一行字符串（以#作为结束的标志），请统计元音字母a,e,i,o,u的总共出现次数（含大小写）
```
int main(){
	int count[5] = {0};
	char tmp;
	scanf("%c",&tmp);
	while(tmp != '#'){
		if(tmp == 'a' || tmp == 'A') count[0] ++;
		else if(tmp == 'e' || tmp == 'E') count[1] ++;
		else if(tmp == 'i' || tmp == 'I') count[2] ++;
		else if(tmp == 'o' || tmp == 'O') count[3] ++;
		else if(tmp == 'u' || tmp == 'U') count[4] ++;
		scanf("%c",&tmp);
	}
	for(int i = 0; i < 5;i ++){
		printf("%d ",count[i]);
	}
}
```
用户输入一行字符串（以@作为结束的标志），请输出其中的所有数字字符和空格（其它字符不输出）。若字符串中没有数字字符和空格，输出No digit and space
参考测试用例1：abc13  3,so45#，对应输出13  345
```
int main(){
	int flag = 1;
	char tmp;
	scanf("%c",&tmp);
	while(tmp != '#'){
		if((tmp >= '1' && tmp <= '9') || tmp == ' ') {
			printf("%c",tmp);
			flag = 0;
		}
		scanf("%c",&tmp);
	}
	if(flag) printf("No digit and space");
	return 0;
}
```
用户输入一行字符串（不超过30），请输出其中的所有字母和空格。输出的同时，要把大写字母转为小写，把小写字母转为大写。若字符串中没有字母和空格，，输出No letter and space
参考测试用例1：abC13  3,so45#，对应输出ABc  SO
```
int main(){
	char s[31];
	gets(s);
	int flag = 1;
	for(int i = 0 ;i < strlen(s); i ++){
		if(s[i] >= 'a' && s[i] <= 'z'){
			flag = 0;
			printf("%c",s[i]+'A'-'a');
		}
		else if(s[i] >= 'A' && s[i] <= 'Z'){
			flag = 0;
			printf("%c",s[i]+'a'-'A');
		}
		else if(s[i] == ' '){
			flag = 0;
			printf("%c",s[i]);
		}
	}
	if(flag) printf("No letter and space");
	return 0;
}
```
用户先输入N，再输入N个实数，请输出它的平均值，精确到小数点后两位。
```
int main(){
	int n;
	float sum,tmp;
	scanf("%d",&n);
	for(int i = 0 ;i < n; i++){
		scanf("%f",&tmp);
		sum += tmp;
	}
	printf("%.2f",sum/n);
	return 0;
}
```
用户输入若干个成绩（以-1作为结束），请统计平均分和不及格人数。
```
int main(){
	int n = 0;
	int fail = 0;
	float sum;
	int tmp;
	scanf("%d",&tmp);
	if(tmp != -1){
		while(tmp != -1){
			sum += tmp;
			n ++;
			if(tmp < 60) fail ++;
			scanf("%d",&tmp);
		}
		
	}
	if(n !=0 )printf("%.2f %d",sum/n,fail);
	return 0;
}
```
用户输入非负数n和m（n和m不超过100），输出[n,m]中与7相关的数。所谓与7相关的数，就是这个数要么是7的倍数，要么组成中有7。
```
int main(){
	int n,m;
	scanf("%d %d",&n,&m);
	for(int i = n ;i <= m; i++){
		if(i%7 == 0) printf("%d ",i);
		else if(i%10 == 7 || i/10%10 == 7){
			printf("%d ",i);
		}
	}
	return 0;
}
```
用户输入N位同学M门课的成绩，请统计每位同学的平均分及不及格门数。
参考测试用例
5 4
100 56 67 90
40 50 89 56
34 76 60 80
100 90 80 70
30 30 30 30
```
int main(){
	int n,m,tmp;
	scanf("%d %d",&n,&m);
	for(int i = 0; i < n; i++){
		float sum = 0;
		int countFail = 0;
		for(int j = 0; j < m; j++){
			scanf("%d",&tmp);
			if(tmp < 60) countFail ++;
			sum += tmp;
		}
		printf("%.2f %d\n",sum/m,countFail);
	}
	return 0;
}
```
用户输入N位同学M门课的成绩，请统计每门课的不及格人数与平均分。
参考测试用例
5 4
100 66 67 90
60 70 60 90
34 76 60 90
100 90 80 90
30 30 30 90
```
int main(){
	int n,m,count = 0;
	scanf("%d %d",&n,&m);
	int num[n][m];
	for(int i = 0; i < n; i++){
		for(int j = 0; j < m; j++){
			scanf("%d",&num[i][j]);
		}
	}
	for(int i = 0; i < m; i++){
		float sum = 0;
		count = 0;
		for(int j = 0; j < n; j++){
			if(num[j][i] < 60) count++;
			sum += num[j][i];
		}
		printf("%d %.2f\n",count,sum/n);
	}
	return 0;
}
```
用户先输入N，再输入N位同学的成绩，输出这门课的成绩分数段分布。分数段为：90-100、80-89、70-79、60-69和<60。
```
int main(){
	int n;
	int num[5] = {0};
	int score;
	scanf("%d",&n);
	for(int i = 0 ;i < n; i++){
		scanf("%d",&score);
		if(score>= 90 && score <= 100) num[0]++;
		else if(score>= 80 && score <= 89) num[1]++;
		else if(score>= 70 && score <= 79) num[2]++;
		else if(score>= 60 && score <= 69) num[3]++;
		else num[4]++;
	}
	for(int i = 0; i < 5; i++){
		printf("%d ",num[i]);
	}
	return 0;
}
```
用户输入N和字符c，请打印如下规律的图形。字符c是第一行要打印的字符，然后之后的每行要打印的字符的ASCII码递增1，若某行打印的是字符’z’，下一行则打印字符’a’，然后继续每行的字符ASCII码递增1。
6k
     k
    ll
   mmm
  nnnn
 ooooo
pppppp
注意：图形看上去好像不齐，这是因为字母的宽度不一样而造成的视觉误差。
大家可以参考后面三行的输出效果。
```
int main(){
	int n;
	char c;
	scanf("%d%c",&n,&c);
	char tmp;
	for(int i = 0; i < n; i ++){
		for(int j = n -1 -i; j>0;j--) printf(" ");
		if(c+i > 'z') tmp = c+i-26;
		else tmp = c+i;
		for(int k = 0; k < i+1; k++) printf("%c",tmp);
		printf("\n");
	}
	return 0;
}
```
用户输入N（不超过20），请打印如下规律的图形。（%5d格式）
4
1
2  3
4  5  6
7  8  9  10 
```
int main(){
	int n,count = 1;
	scanf("%d",&n);
	for(int i = 0; i < n; i ++){
		for(int j = 0; j < i + 1;j++) {
			printf("%5d",count);
			count ++;
		}
		printf("\n");
	}
	return 0;
}
```
用户输入N（不超过20），请打印如下规律的图形。（%5d格式）
4
10  9  8  7
6   5  4
3   2
1 
```
int calculate(int n){
	int count = 0;
	for(int i = 0; i < n;i++){
		for(int j = 0; j < i+1; j++){
			count ++;
		}
	}
	return count;
}
int main(){
	int n;
	scanf("%d",&n);
	int count = calculate(n);
	for(int i = 0; i < n; i++){
		for(int j = 0; j < n-i; j ++){
			printf("%5d",count--);
		}
		printf("\n");
	}

	return 0;
}
```
用户输入一个数（不超过9位），请输出这个数各个位数之和，如145的各个位数之和是10。
```
int calculate(int n){
	int sum = 0;
	int tmp = n;
	while(tmp > 0){
		sum += tmp % 10;
		tmp /= 10;
	}
	return sum;
}
```
用户输入一个数（不超过20位），请输出这个数的偶数位数之和，如14576，从最左边开始，它的偶数位数分别是4和7，之和是11。
注意：本题的数据已超过整数的取值范围，需要以字符串的方式来读取数据，因此你读入的1其实是数字字符’1’，要想求和，需要将’1’-‘0’，才能得到数值1。
```
int calculate(char n[]){
	int sum = 0;
	for(int i = 1; i < strlen(n); i+=2){
		sum += n[i] - '0';
	}
	return sum;
}
```
用户输入一个数（不超过20位），请判断这个数是否是对称的。
注意：本题的数据已超过整数的取值范围，需要以字符串的方式来读取数据。
```
int calculate(char n[]){
	for(int i = 0; i < strlen(n)/2; i++){
		if(n[i] != n[strlen(n)-1-i]) return 0;
	}
	return 1;
}
```
用户输入N和M，请输出N和M的最大公约数。4和12的最大公约数是4，15 和6的最大公约数是3，7和15的最大公约数是1。
注意：N和M的大小不确定，即不保证N一定比M大。
```
int calculate(int n,int m){
	int tmp;
	if(n > m){
		tmp = n;
		n = m;
		m = tmp;
	}
	for(int i = n; i > 0; i--){
		if(n % i == 0 && m % i == 0) return i;
	}
	return 1;
}
```
用户输入N和M，请输出N和M的最小公倍数。4和12的最小公倍数是12，5和7的最小公倍数是35，6和4的最小公倍数是12。
```
int calculate(int n,int m){
	int tmp;
	if(n > m){
		tmp = n;
		n = m;
		m = tmp;
	}
	for(int i = m; ; i++){
		if(i % n == 0 && i % m == 0) return i;
	}
	return 0;
}
```
用户输入N（小于100）和k，请输出小于等于N的所有与k有关的数。所谓与k有关的数，就是它是k的倍数，或某个位数上是k。如20以内与7有关的数是7，14，17。
```
void calculate(int n,int k){
	for(int i = 1;i< n ;i ++){
		if(i%k == 0 || i/10%10 == k || i%10 == k) {
			printf("%d ",i);
		}
	} 
}
```
所谓“悟空数”，就是某个数字的各个位数之和是5的倍数，如145的各个位数之和是10，10是5的倍数，所以145是悟空数。
现在，用户输入N（不超过9位），请输出它是否是悟空数。
```
int calculate(int n){
	int sum = 0;
	while(n > 0){
		sum += n%10; 
		n /= 10;
	} 
	if( sum % 5 == 0) return 1;
	return 0;
}
```
所谓“凄惨数”，就是某个数字的各个位数之和要么是7的倍数，要么是3的倍数，如9354的各个位数之和是21，21是7的倍数，所以9354是凄惨数。
现在，用户输入N（不超过9位），请输出它是否是凄惨数。
```
int calculate(int n){
	int sum = 0;
	while(n > 0){
		sum += n%10; 
		n /= 10;
	} 
	if( sum % 7 == 0 || sum % 3 == 0) return 1;
	return 0;
}
```
用户输入3个正整数，请输出它们能否构成三角形，及三角形的类型，1表示等边，2表示等腰，3表示直角，4表示普通三角形，5表示不能形成三角形。
```
int calculate(int a,int b, int c){
	if(a + b > c && a + c > b && b + c > a){
		if(a == b && b == c) return 1;
		else if(a==b || b == c || a== c) return 2;
		else if(a*a + b*b == c*c || a*a + c*c == b*b || b*b + c*c == a*a) return 3;
		return 4;
	}
	return 5;
}
```
商场促销：每件商品都是在原价基础上打折促销。
小于200：无优惠
[200,500)：打9折
[500,1000)：打8折
[1000,2000)：打7折
大于等于2000：打6折
现在用户输入三个商品的原价，请输出用户实际需要付的金额。
```
float calculate(int a,int b, int c){
	float sum = 0;
	int tmp;
	for(int i = 0; i < 3; i++){
		switch(i){
			case 0:tmp = a;break;
			case 1:tmp = b;break;
			case 2:tmp = c;break;
		}
		if(tmp<200) sum += tmp;
		else if(tmp>=200 && tmp<500) sum += tmp * 0.9; 
		else if(tmp>=500 && tmp<1000) sum += tmp * 0.8;
		else if(tmp>=1000 && tmp<2000) sum += tmp * 0.7;
		else if(tmp >= 2000) sum += tmp * 0.6;
	}
	return sum;
}
```
用户按 A？B的格式输入数据，当其中的？是+，-，*，\、%中的任意一个，请输出计算结果，如果？不是以上字符，请输出Wrong input
```
	char a[3];
	gets(a);
	switch(a[1]){
		case'+':printf("%d",a[0]-'0'+a[2]-'0');break;
		case'-':printf("%d",a[0]-'0'-a[2]-'0');break;
		case'*':printf("%d",(a[0]-'0')*(a[2]-'0'));break;
		case'\\':printf("%d",(a[0]-'0')/(a[2]-'0'));break;
		case'%':printf("%d",(a[0]-'0')%(a[2]-'0'));break;
		default:printf("Wrong input");
	}
```
用户告诉你现在的时间（按m:n的格式提供，m是小时，n是分钟），以及他准备进行学习的时间t（分钟），请你计算出用户几点几分结束学习。（按24小时制）
```
int main(){
	int hour,min;
	scanf("%d:%d",&hour,&min);
	int time;
	scanf("%d",&time);
	min += time%60;
	hour += time/60;
	if(min >= 60){
		min -= 60;
		hour += 1;
	}
	if(hour >= 24){
		hour -= 24;
	}
	printf("%d:%d",hour,min);
	return 0;
}
```
12小时制转24小时制
```
int main(){
	int hour,min;
	char a[3];	
	scanf("%d:%d%s",&hour,&min,a);
	printf("%d:%d\n",hour,min);	
	if(strcmp(a,"AM") == 0){	
		if(hour == 12) hour = 0;
	}	
	else{	
		if(hour < 12) hour += 12;
		}
	printf("%d:%d",hour,min);
	return 0;
}
```
24小时制转12小时制
```
int main(){
	int hour,min;
	scanf("%d:%d",&hour,&min);
	char a[3] = "AM";
	if(hour == 0) hour = 12;
	else if(hour > 12) hour -= 12;
	if(hour >= 12) strcpy(a,"PM");
	printf("%d:%d %s",hour,min,a);
	return 0;
}
```
某国硬币有1分、3分、5分的币值，1元可兑换100分币值的硬币，显然，兑换方案有很多种（要求每个分值硬币都要有），现在用户输入N，请你输出第N个方案的兑换方法（按照币值从小到大的顺序给方案，如1号方案是1个1分，3个3分，18个5分，2号方案是1个1分，8个3分，15个5分。
如果N的大小不在方案数内，输出Wrong。
```
int main(){
	int n;
	scanf("%d",&n);
	int count=0,flag = 0;
	for(int i = 1; i < 101; i++){
		for(int j = 1; j < 34; j ++){
			if((100-i*1-j*3) % 5 == 0){
				count ++;
				if(count == n) {
					printf("%d %d %d",i,j,(100-i*1-j*3) / 5);
					flag = 1;
				}
			}
		}
	}
	if(!flag) printf("Wrong");
	return 0;
}
```
用户输入N和字符c，请输出如下图的三角形。
4#
   #
  ###
 #####
#######
金字塔形
```
int main(){
	int n;
	char c;
	scanf("%d%c",&n,&c);
	for(int i = 0;i < n;i++){
		for(int j = 0; j<n-i-1; j ++) printf(" ");
		for(int k = 0; k < 2*i+1; k ++) printf("%c",c);
		printf("\n");
	}
	return 0;
}
```
如果用户在5号恋爱，则15号是他恋爱满10天的日子。如果15号那天不是周末，他会看恋爱满20天的日子是不是周末。总之，他很渴望尽早达成心愿。
现在，用户告诉你他陷入恋爱的日子是周几（（1到7，7表示周日），请你算出他恋爱满第多少天可以达成心愿（注意：这个天数必须是10的整数倍，且当天是周末）
本题不考虑闰年的情况。
```
int main(){
	int n;
	scanf("%d",&n);
	for(int i = 10;;i += 10){
		if((n + i) % 7 == 6 || (n + i) % 7 == 7) {
			printf("%d",i);
			break;
		}
	}
	return 0;
}
```
用户输入一个十进制数，请你把它转换成三进制。
```
int main(){
	int n;
	int a[30],i=0;
	scanf("%d",&n);
	while(n){
		a[i++] = n-3*(n/3);
		n /= 3;
	}
	while(i){
		printf("%d",a[--i]);
	}
	return 0;
}
```
用户输入一行字符串（不超过100），请统计其中的单词个数。
```
int main(){
	char string[101],flag = 0, sum = 0, i = 0;
	gets(string);
	while(string[i] != '\0'){
		if(string[i++] == ' ') flag = 0;
		else{
			if(!flag) sum ++;
			flag = 1;
		}
	}
	printf("%d",sum);
	return 0;
}
```
用户先输入N，再输入N个字符串（均不超过20），请按字典顺序从大到小排序。
6
goodbye
test
zoo
fine
apple
blue
```
int main(){
	int n;
	scanf("%d\n",&n);
	char* s[20];
	char tmp[20];
	for(int i = 0;i < n;i++){
		s[i] = (char *)malloc(sizeof(char *) * 20);
	}
	for(int i = 0 ;i < n ; i++){
		gets(s[i]);
	}
	for(int i = 0; i < n; i ++){
		for(int j = i+1; j < n; j ++){
			if(strcmp(s[i], s[j]) > 0){
				strcpy(tmp,s[i]);
				strcpy(s[i],s[j]);
				strcpy(s[j],tmp);
			}
		}
	}
	for(int i = 0 ; i < n; i++){
		printf("%s\n",s[i]);
	}
	return 0;
}
```
用户先输入N，再输入N个字符串（均不超过20），请按字符串长度从小到大排序。当字符串长度相同时，按照输入的先后顺序排序
```
int main(){
	int n;
	scanf("%d\n",&n);
	char* s[20];
	char tmp[20];
	for(int i = 0;i < n;i++){
		s[i] = (char *)malloc(sizeof(char *) * 20);
	}
	for(int i = 0 ;i < n ; i++){
		gets(s[i]);
	}
	for(int i = 0; i < n; i ++){
		for(int j = i+1; j < n; j ++){
			if(strlen(s[j]) < strlen(s[i])){
				strcpy(tmp,s[i]);
				strcpy(s[i],s[j]);
				strcpy(s[j],tmp);
			}
		}
	}
	for(int i = 0 ; i < n; i++){
		printf("%s\n",s[i]);
	}
	return 0;
}
```
用户输入10个数，请去掉其中重复的数字后再输出。
```
int main(){
	int num[10],result[10],count = 0;
	for(int i = 0; i < 10 ; i ++){
		scanf("%d",&num[i]);
	}
	for(int i = 0; i < 10; i++){
		int flag = 1;
		for(int k = 0; k < count; k ++){
			if(num[i] == result[k]){
				flag = 0;
				break;
			}
		}
		if(flag){
			result[count++] = num[i];
		}
	}
	for(int i = 0; i < count; i ++){
		printf("%d ",result[i]);
	}
	return 0;
}
```
用户输入10个数，再输入x，请删除x后输出数组。注意：x可能不存在，此时应输出Not found x
```
int main(){
	int num[10],x,result[10],count = 0;
	for(int i = 0; i < 10 ; i ++){
		scanf("%d",&num[i]);
	}
	scanf("%d",&x);
	for(int i = 0; i < 10; i++){
		if(num[i] != x){
			result[count ++] = num[i];
		}
	}
	if(count == 10){
		printf("Not found %d",x);
		return 0;
	}
	for(int i = 0; i < count; i ++){
		printf("%d ",result[i]);
	}
	return 0;
}
```
用户输入9个数（乱序），用户输入k和x，表示把x插入到数组中下标为k的地方，原来的数要依次后移一个。如5 4 7 8 1 2 3 56 54，再输入4和100，则输出结果是5 4 7 8 100 1 2 3 56 54。
```
int main(){
	int num[10],x,index;
	for(int i = 0; i < 9 ; i ++){
		scanf("%d",&num[i]);
	}
	scanf("%d %d",&index,&x);
	for(int k = 9; k > index; k--){
		num[k] = num[k-1];
	}
	num[index] = x;
	for(int i = 0; i < 10; i ++){
		printf("%d ",num[i]);
	}
	return 0;
}
```
用户输入7个数，请输出中位数。所谓中位数，就是排序后，位于数组正中间的元素数值。假设1 5 9 2 6 7 8排序后是1 2 5 6 7 8 9，其中的6就是中位数。
```
int cmp(const void* _a , const void* _b)
{
    int* a = (int*)_a;
    int* b = (int*)_b;
    return *a - *b;
}
int main(){
	int num[7];
	for(int i = 0; i < 7 ; i ++){
		scanf("%d",&num[i]);
	}
	qsort(num,7,sizeof(int),cmp);
	printf("%d",num[3]);
	return 0;
}
```
用户输入两个字符串a和b（均不超过20个字符），请判断b是否是a的子串，如果是，输出b在a中第一次出现的位置。如果b不是a的子串，输出No
本题要编程完成，不可以使用现成的strstr函数
```
int main(){
	char a[20],b[20];
	gets(a);
	gets(b);
	int flag = 0;
	for(int i = 0; i < strlen(a); i++){
		if(a[i] == b[0]){
			flag = 1;
			for(int j = 1; j < strlen(b); j ++){
				if(b[j] != a[i+j]){
					flag = 0;
					break;
				}
			}
		}
		if(flag){
			printf("%d",i);
			break;
		}
	}
	if(!flag) printf("No");
	return 0;
}
```
用户输入两个数组（都是6个数），请输出它们的交集。
系统保证数组a和数组b本身不含有相同的数。 
如a是1 2 3 4 5 6，b是4 5 6 7 8 9，交集是4 5 6
也有可能a和b没交集，需要提示信息。
```
int main(){
	int a[6],b[6],result[6],count = 0;

	for(int i = 0 ; i < 6; i ++){
		scanf("%d",&a[i]);
	}
	for(int i = 0 ; i < 6; i ++){
		scanf("%d",&b[i]);
	}
	for(int i = 0; i < 6; i ++){
		for(int j = 0; j < 6; j ++){
			if(a[i] == b[j]){
				result[count++] = a[i];
			}
		}
	}
	if(count == 0) printf("No same");
	for(int i = 0; i < count; i ++){
		printf("%d ",result[i]);
	}
}
```
用户输入两个数组（a是10个数，b是4个数），请去掉a中的所有b数组元素。
例如a中的数据是10 20 30 4 5 78 43 56 99 12，b中的数据是6 4 43 2，则a中去掉b中数组元素后是10 20 30 5 78 56 99 12
```
int main(){
	int a[10],b[4],result[10],count = 0;
	for(int i = 0 ; i < 10; i ++){
		scanf("%d",&a[i]);
	}
	for(int i = 0 ; i < 4; i ++){
		scanf("%d",&b[i]);
	}
	for(int i = 0; i < 10; i ++){
		int flag = 0;
		for(int j = 0; j < 4; j ++){
			if(a[i] == b[j]){
				flag = 1;
			}
		}
		if(flag == 0){
			result[count ++] = a[i];
		}
	}
	for(int i = 0; i < count; i ++){
		printf("%d ",result[i]);
	}
}
```
用户输入一行字符串，请反序存储后再输出。不可以直接倒着输出，要求a字符串本身的顺序要改变。
```
int main(){
	char s[20];
	gets(s);
	for(int i = 0; i < strlen(s)/2; i++){
		char tmp = s[i];
		s[i] = s[strlen(s) - 1 - i];
		s[strlen(s) - i - 1] = tmp;
	}
	for(int i = 0; i < strlen(s); i++){
		printf("%c",s[i]);
	}
}
```
用户输入5对数(系数,指数)，请输出对应的一元多次方程。当系数或指数为1时，不输出这个1。这里保证数据均为非负。
如
(1,2)
(3,0)
(0,2)
(4,1)
(3,2)
输出结果是：4x^2+3+4x
```
struct data{
	int coef;
	int expan;
	struct data* next;
};
int main(){
	int c,e;
	struct data* head = (struct data*)malloc(sizeof(struct data));
	head->next = (struct data*)malloc(sizeof(struct data));
	scanf("%d %d",&head->next->coef,&head->next->expan);
	head->next->next = NULL;
	for(int i = 0; i < 4; i ++){
		scanf("%d %d",&c,&e);
		struct data* p = head->next;
		struct data* tmp = head;
		int flag = 0;
		while(p){
			if(e == p->expan){
				flag = 1;
				p->coef += c;
				if(p->coef == 0){
					tmp->next = p->next;
				}
				break;
			}
			p = p->next;
			tmp = tmp->next;
		}
		if(flag == 0) {
			struct data* newtmp = (struct data*)malloc(sizeof(struct data));
			newtmp->coef = c;
			newtmp->expan = e;
			tmp->next = newtmp;
			newtmp->next = p;
		}
	}
	struct data* p = head->next;
	printf("%d",p->coef);
	if(p->expan != 0) printf("x^%d",p->expan);
	p = p->next;
	while(p){
		if(p->coef > 0) printf("+");
		printf("%d",p->coef);
		if(p->expan != 0 && p->expan != 1) printf("x^%d",p->expan);
		else if(p->expan == 1) printf("x");
		p = p->next;
	}
	return 0;
}
```
用户输入8个数，再输入n（n>=0），让数组元素向左循环移动n次。
如12,3,4,5,7,8,20,100，n是2，输出是4,5,7,8,20,100,12,3
```
int main(){
	int num[8],n,result[8];
	for(int i = 0;i < 8; i++){
		scanf("%d",&num[i]);
	}
	scanf("%d",&n);
	for(int i = 0; i < 8;i ++){
		result[i] = num[(n+i)%8];
	}
	for(int i = 0 ;i < 8; i ++){
		printf("%d ",result[i]);
	}
	return 0;
}
```
用户输入一行字符串（不超过30），再输入n和m，把字符串中下标从n到m的字符串存到b中，再输出b。要求不能直接输出a中的相应字符段，一定要保存到另一个字符串b中，再输出这个字符串。
```
int main(){
	char s[31],b[31];
	int n,m;
	gets(s);
	scanf("%d %d",&n,&m);
	for(int i = 0 ; i<= m-n;i++){
		b[i] = s[n+i];
	}
	for(int i = 0;i <= m-n; i++){
		printf("%c",b[i]);
	}
	return 0;
}
```
用户输入6个字符串（不超过20），请你在不改变输入排序的前提下，对字符串按字典顺序由小到大排序。要在排序完成后，分别输出原字符串顺序，和排序后的顺序。
```
int main(){
	char* resource[6],*result[6];
	for(int i = 0; i <6; i ++){
		resource[i] = (char*)malloc(sizeof(char)*20);
		result[i] = (char*)malloc(sizeof(char)*20);
	}
	for(int i = 0; i < 6; i++){
		gets(resource[i]);
		strcpy(result[i],resource[i]);
	}
	for(int i = 0;i< 6;i ++){
		for(int j = i+1; j < 6; j ++){
			if(strcmp(result[j],result[i])<0){
				char tmp[20];
				strcpy(tmp,result[i]);
				strcpy(result[i],result[j]);
				strcpy(result[j],tmp);
			}
		}
	}
	for(int i = 0; i < 6; i++){
		puts(resource[i]);
	}
	for(int i = 0; i < 6; i ++){
		puts(result[i]);
	}
	return 0;
}
```
用户输入10个数，请在去掉一个最大值和一个最小值后求剩余数的平均值。
```
int main(){
	int num[10],max = MIN,min = MAX;
	for(int i = 0; i < 10; i++){
		scanf("%d",&num[i]);
		if(num[i]>max) max = num[i];
		if(num[i]<min) min = num[i];
	}
	float sum = 0;
	for(int i = 0; i < 10; i++){
		if(num[i] != max && num[i] != min) sum += num[i];
	}
	printf("%.2f",sum/=8);
	return 0;
}
```
用户输入5个数，请判断它是否是升序（是每个数都大于等于它前面的所有数）。
如果是升序，再看它是否是严格升序，即每个数都大于它前面的所有数。
输出结果有三个可能：1代表是严格升序，2代表升序（肯定不是严格升序），3代表不是升序
```
int main(){
	int num[5],flag = 1;
	for(int i = 0; i < 5; i++){
		scanf("%d",&num[i]);
	}
	for(int i = 0; i < 4; i ++){
		if(num[i+1] > num[i]) flag += 0;
		else if(num[i+1] == num[i]) flag = 2;
		else flag = 3;
	}
	printf("%d",flag);
	return 0;
}
```
用户输入一行字符串（不超过20个字符），请按从大到小的顺序进行排序。
参考用例：
zbcdg，对应输出zgdcb
```
int main(){
	char s[21];
	gets(s);
	for(int i = 0; i < strlen(s); i ++){
		for(int j = i+1; j < strlen(s); j++){
			if(s[j] > s[i]){
				char tmp;
				tmp = s[i];
				s[i] = s[j];
				s[j] = tmp;
			}
		}
	}
	for(int i = 0;i < strlen(s); i++){
		printf("%c",s[i]);
	}
	return 0;
}
```
用户输入一行字符串（不超过30），请先把奇数位置上的字符取出来组成新的字符串，再判断它是否是对称的。
如abcibbcda的奇数位置上的字符组成的新字符串是acbca，这个串是对称的。
输出Yes或No
```
int calculate(char n[]){
	for(int i = 0; i < strlen(n)/2; i++){
		if(n[i] != n[strlen(n)-1-i]) return 0;
	}
	return 1;
}
int main(){
	char s[31],result[16];
	int count = 0;
	gets(s);
	for(int i = 0; i < strlen(s); i += 2){
		result[count++] = s[i];
	}
	result[count] = '\0';
	if(calculate(result)) printf("Yes");
	else printf("No");
	return 0;
}
```
现有7个学生的信息（含学号、姓名（不超过10）、性别，成绩），请分别统计男生和女生的平均分和不及格人数。
101 Jack m 89
105 Marry f 56
102 Tom m 40
108 Face m 88
109 Alice f 70
107 David m 90
103 Lucky f 55
```
struct student{
	int num;
	char name[10];
	char gender;
	int score;
};
int main(){
	struct student students[7];
	int fail = 0,man = 0,woman = 0;
	float man_sum = 0,woman_sum = 0;
	for(int i = 0;i < 7; i++){
		scanf("%d %s %c %d",&students[i].num,&students[i].name,&students[i].gender,&students[i].score);
		if(students[i].score < 60) fail ++;
		if(students[i].gender == 'm') {
			woman_sum += students[i].score;
			woman ++;
		}
		else {
			man_sum += students[i].score;
			man ++;	
		}
	}
	printf("%.2f %.2f %d",man_sum/man,woman_sum/woman,fail);
	
	return 0;
}
```
用户输入7个学生的信息（含学号、姓名（不超过10）、性别，成绩），请按照学号从小到大进行排序。
可参考59题的用例。
```
void swap(struct student *a,struct student *b){
	struct student *tmp = (struct student*)malloc(sizeof(struct student));
	tmp->num = a->num;
	strcpy(tmp->name,a->name);
	tmp->gender = a->gender;
	tmp->score = a->score;
	
	a->num = b->num;
	strcpy(a->name,b->name);
	a->gender = b->gender;
	a->score = b->score;
		
	b->num = tmp->num;
	strcpy(b->name,tmp->name);
	b->gender = tmp->gender;
	b->score = tmp->score;
}
int main(){
	struct student students[7];
	for(int i = 0;i < 7; i++){
		scanf("%d %s %c %d",&students[i].num,&students[i].name,&students[i].gender,&students[i].score);
	}
	for(int i = 0; i < 7;i ++){
		for(int j = i+1; j < 7; j++){
			if(students[j].num < students[i].num){
				swap(students+i,students+j);
			}
			
		}
	}
	for(int i = 0; i < 7; i++){
		printf("%d %s %c %d\n",students[i].num,students[i].name,students[i].gender,students[i].score); 
	}
	return 0;
}
```
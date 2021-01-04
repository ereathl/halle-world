#include<stdio.h>
#include<math.h>
int main()
{
	int s[31] = { 0 }, j = 0;
	char ch;
	for (int i = 0; i < 30;i++)
	{
		scanf("%c",&ch);
		if (ch >= '0' && ch <= '9')
		{
			s[j] = ch - 48;
			j++;
		}
		else if (ch == ' ')
		{
			i = i - 1;
			continue;
		}
		else if (ch == '\n')
		{
			break;
		}
	}
	int cnt = j;
	int cnt1 = pow(2,j-1);
	int sum[20] = { 0 };
	int i = 0;
	for (j; j >= 0; j--)
	{
		sum[i] = sum[i] + s[j] * cnt1;
		for (int k = 0; k < 19; k++)
		{
			while (sum[k] >= 10)
			{
				sum[k] = sum[k] - 10;
				sum[k + 1]++;
			}
		}
	}
	for (int k = 19; k >= 0; k--)
	{
		if (sum[k] != 0)
		{
			for (int l = k; l >= 0; l--)
			{
				printf("%d", sum[l]);
			}
		}
	}
	return 0;
}

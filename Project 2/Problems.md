# 2018.11.15 & 2018.12.6 &

## character statistics

## select sort
```c
for (i = 0; i + 1 < n; ++ i){
	min = i;
	for (j = i + 1; j < n; ++ j){
		if (k[j] < k[min]){
			min = j;
		}
	}
	if (min != i){
		/* swap k[min] and k[i] */
		temp = k[min] ;
		k[min] = k[i];
		k[i] = temp;
	}
}
```

## reverse permutation
- output nth order permutation reversely.
- 3
- 3 2 1
- 3 1 2
- 2 3 1
- 2 1 3
- 1 3 2
- 1 2 3

# 2018.11.8

## substring replacement
- read 3 strings, **str**, **str1**, **str2** ($v0 = 12 or 8 both works)
- replace all the **str1** in **str** to **str2**
- replace field shouldn't ovverilogap. e.g. case like str: `ababa`, str1: `aba`, str2: `kkk`, should print `kkkba`.
  
## Matrix to the Power of 2^n
Input a square matrix `A`, and output its power of 2^n.
- n = 0: print `A`
- n = 1: print `A * A`
- n = 2: print `A * A * A * A`
- ......
  
## Expression Calculator (Data Structure Homework Stack)
Output the result of an expression with integers and +, -, *, /, **()**.
- 24 / ( 1 + 2 + 36 / 6 / 2 - 2) * ( 12 / 2 / 2 )
- 18
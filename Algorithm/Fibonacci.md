## 피보나치 수열을 만들어내는 여러가지 방법

<h3>1. pointer, recursion을 이용(190125)</h3>

```C
    #include <stdio.h>
    
    int fibo(int *num1, int *num2, int i){    
      int temp;
      temp = *num1;
      *num1 = *num2;
      *num2 = temp + *num2;
      
      printf("%5d \n", *num2);
      i++;
      
      if(i<10)      // i는 재귀를 진행할 횟수
        return fibo(num1, num2, i);  
      else
        return 0;
    }
    
    
    void main(){
      int num1 = 1, num2 = 2;
      printf("%5d \n%5d\n", num1, num2);
      fibo(&num1, &num2, 1);
    }
```

<h3>2. recursion만을 이용(190125)</h3>

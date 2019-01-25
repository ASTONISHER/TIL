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

```C
    #include <stdio.h>
    
    void fibo(int num1, int num2, int i){  // i는 재귀횟수
        printf("%4d ", num1);
        if(i==1)
            printf("%4d ", num2);
        else
            fibo(num2, num1+num2, --i);
    }
    
    void main(){
        fibo(1, 2, 10);
    }
```

이때, fibo(num2, num1+num2, i--);를 호출하면 안됨
> fibo에서 원래 호출된 i(여기서는 10)을 사용한 이후에 i값이 하나 줄어들어서 9가 되지만 이것은 사용되지 않는다. 기본적으로 함수를 호출할 때 인자는 '복사'되어 넘어가기 때문에 이미 넘어간 i값은 계속 10이 된다. 내 생각대로라면 recursion이 끊임 없이 발생해서 계속 연산이 진행되어 runtime error가 나와야하는데, 왜 쓰레기 값이 호출되는지는 잘 모르겠다.






# if문
+ if안에 조건문이 일치하면 if문 안에 코드가 실행이 된다.
+ if안에 조건문이 일치하지 않으면 else문을 실행시킨다.

1. if문을 실행합니다.
2. else if문을 실행합니다.
3. 최종적으로 else를 실행합니다.
``` js
const age = 30;

if(age > 19){
    console.log('환영 합니다.');
}
else if(age === 19){
    console.log('수능 잘치세요.');
}
else(age <= 19){
    console.log('안녕히 가세요.');  
}

console.log('---------------------------------');
```
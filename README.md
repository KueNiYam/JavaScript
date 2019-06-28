# JavaScript
JavaScript ES6+ Study

# var, const, let

## var

es6 이전의 변수 선언 방식입니다.
`var`은 매우 유연한 방식으로 변수를 선언할 수 있는 방법입니다.
그렇지만, 몇 가지 문제점을 가지고 있기도 합니다.

### (1) scope

`Function` 단위의 Scope를 가집니다. 

    var hello = 'hello!';
    function sayHello() {
        var hello = 'hello in function!';
        console.log(hello);
    }

    sayHello(); // hello in function!
    console.log(hello); // hello!

위의 예는 'hello'라는 변수의 유효범위가 Function 내라는 것을 알 수 있습니다.

**var는 {} 단위(Block 단위)가 아닙니다!**

    var hello = 'hello';
    if (true) {
        var hello = 'hello in if';
    }

    console.log(hello); // hello in if

위의 예제를 보면,
> if 절 내부에 hello를 변수를 새로 선언했지만, var로 선언한 변수의 scope는 {} 가 아닌 function이기 때문에 hello 변수의 {} 바깥에서도 변경된 것을 볼 수 있습니다.

### (2) 이런 것도 가능합니다.

    var hello = 'first hello';
    var hello = 'second hello';

    console.log(hello); // second hello

같은 변수를 두 번 선언했는데도, 오류가 나지 않고 잘 동작합니다.

이런 식의 유연한 변수 선언 방식은 많은 오류를 발생시킬 수 있습니다.

> 그래서, ES6에는 다음의 const와 let이라는 변수 선언 방법이 추가되었습니다.

## const

### (1) 상수를 선언합니다.

const는 `constance`의 약자입니다.
한 번 선언된 상수는 다시 재정의될 수 없습니다.

    const hello = 'hello';
    hello = 'change hello'; // Error

위와 같이, 상수로 선언한 hello의 값을 변경하려고 하면 에러가 발생합니다.

### (2) Scope는 {} 블록입니다.

    const hello = 'hello!';
    {
        const hello ='inner hello!';
        console.log(hello); // inner hello!
    }
    console.log(hello); // hello!

괄호 안에 hello를 선언했지만, const의 scope는 괄호 블록 안이기 때문에 괄호 바깥에 hello 상수를 또 선언할 수 있습니다.

## let

### (1) 변수를 선언합니다.

let으로 선언하면 값을 재정의할 수 있습니다.

    let hello = 'first hello'; // first hello
    hello = 'changed hello'; // changed hello

### (2) scope는 {} 입니다.

const와 마찬가지로 scope는 괄호 변수입니다.

    let hello = 'first hello';
    {
        let hello = 'inner hello';
        console.log(hello); // inner hello
    }
    console.log(hello); // first hello


### (3) var 처럼 같은 변수를 두 번 선언하는 것은 불가합니다.

    let hello = 'first hello';
    let hello = 'second hello'; // Error

> ES6에서는 var 보다는 const와 let을 사용해서 좀 더 명확한 코드를 만들어 내는 것을 권장합니다.

> 일반적으로 기본혁(String, Number, Boolean, Null, Undefined)에 대해서 let은 값의 변경이 있을 경우, const는 상수를 선언할 때 사용한다.
> 하지만 참조형(Array, Object, Function)를 선언하는 경우에는 const를 사용하는 것이 바람직하다.
> 참조형은 const로 선언해도 내부 값의 변경이 가능하다.

# 평가와 일급

## 평가
 
 - 코드가 계산(Evaluation) 되어 값을 만드는 것

## 일급

 - 값으로 다룰 수 있다.
 - 변수에 담을 수 있다.
 - 함수의 인자로 사용될 수 있다.
 - 함수의 결과로 사용될 수 있다.

 ## 일급 함수

 - 함수를 값으로 다룰 수 있다.
 - 조합성과 추상화의 도구

 ## 고차 함수

 함수를 값으로 다루는 함수
 
 - 함수를 인자로 받아서 실행하는 함수
 - 함수를 만들어 리턴하는 함수 (클로저를 만들어 리턴하는 함수)

### 클로저

`클로저(Closure)`는 내부함수가 외부함수의 변수(맥락, Context)에 접근할 수 있는 것을 일컫습니다. 클로저는 외부함수의 실행이 끝나서 외부함수가 소멸된 이후에도 내부함수가 외부함수에 접근할 수 있습니다.
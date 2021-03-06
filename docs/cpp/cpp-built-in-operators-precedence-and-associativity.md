---
title: C++기본 제공 연산자, 우선 순위 및 결합성
ms.date: 11/04/2016
helpviewer_keywords:
- operators (C++), hierarchy
- operator precedence
- precedence, operators
- operators (C++), associativity
- multiple operators [C++]
- associativity of operators [C++]
- operators [C++], precedence
- evaluation order
- hierarchy, operator
ms.assetid: 95c1f0ba-dad8-4034-b039-f79a904f112f
ms.openlocfilehash: 36e7ce77e24366be10b75f5bb4f8830363594301
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180409"
---
# <a name="c-built-in-operators-precedence-and-associativity"></a>C++기본 제공 연산자, 우선 순위 및 결합성

C++ 언어는 모든 C 연산자를 포함하며 몇 가지 새로운 연산자를 추가합니다. 연산자는 둘 이상의 피연산자에 대해 수행할 평가를 지정합니다.

연산자 *우선 순위* 는 연산자가 둘 이상 포함 된 식의 작업 순서를 지정 합니다. 연산자 *결합성* 은 우선 순위가 같은 여러 연산자를 포함 하는 식에서 피연산자가 왼쪽 또는 오른쪽에 있는 연산자와 함께 그룹화 되는지 여부를 지정 합니다. 다음 표에서는 C++ 연산자의 우선 순위와 결합성을 내림차순으로 보여 줍니다. 우선 순위 번호가 같은 연산자는 괄호를 사용하여 다른 관계를 명시적으로 강제하지 않는 한 우선 순위가 같습니다.

### <a name="c-operator-precedence-and-associativity"></a>C++ 연산자 우선 순위 및 결합성

|연산자 설명|연산자|
|--------------------------|--------------|
|**그룹 1 우선 순위, 결합성 없음**|
|[범위 확인](../cpp/scope-resolution-operator.md)|[::](../cpp/scope-resolution-operator.md)|
|**그룹 2 우선 순위, 왼쪽에서 오른쪽으로의 결합성**|
|[멤버 선택 (개체 또는 포인터)](../cpp/member-access-operators-dot-and.md)|[. 또는->](../cpp/member-access-operators-dot-and.md)|
|[배열 첨자](../cpp/subscript-operator.md)|[&#91;&#93;](../cpp/subscript-operator.md)|
|[함수 호출](../cpp/function-call-operator-parens.md)|[()](../cpp/function-call-operator-parens.md)|
|[후 위 증가](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[후 위 감소](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[유형 이름](../cpp/typeid-operator.md)|[typeid](../cpp/typeid-operator.md)|
|[상수 형식 변환](../cpp/const-cast-operator.md)|[const_cast](../cpp/const-cast-operator.md)|
|[동적 형식 변환](../cpp/dynamic-cast-operator.md)|[dynamic_cast](../cpp/dynamic-cast-operator.md)|
|[다시 해석 형식 변환](../cpp/reinterpret-cast-operator.md)|[reinterpret_cast](../cpp/reinterpret-cast-operator.md)|
|[정적 형식 변환](../cpp/static-cast-operator.md)|[static_cast](../cpp/static-cast-operator.md)|
|**그룹 3 우선 순위, 오른쪽에서 왼쪽으로의 연관성**|
|[개체 또는 형식의 크기](../cpp/sizeof-operator.md)|[sizeof](../cpp/sizeof-operator.md)|
|[전위 증가](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[전위 감소](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[1의 보수](../cpp/one-s-complement-operator-tilde.md)|[~](../cpp/one-s-complement-operator-tilde.md)|
|[논리적 not](../cpp/logical-negation-operator-exclpt.md)|[!](../cpp/logical-negation-operator-exclpt.md)|
|[단항 부정](../cpp/unary-plus-and-negation-operators-plus-and.md)|[-](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[단항 더하기](../cpp/unary-plus-and-negation-operators-plus-and.md)|[+](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[주소-](../cpp/address-of-operator-amp.md)|[&amp;](../cpp/address-of-operator-amp.md)|
|[간접 참조](../cpp/indirection-operator-star.md)|[&#42;](../cpp/indirection-operator-star.md)|
|[개체 만들기](../cpp/new-operator-cpp.md)|[신규](../cpp/new-operator-cpp.md)|
|[개체 제거](../cpp/delete-operator-cpp.md)|[delete](../cpp/delete-operator-cpp.md)|
|[캐스트](../cpp/cast-operator-parens.md)|[()](../cpp/cast-operator-parens.md)|
|**그룹 4 우선 순위, 왼쪽에서 오른쪽으로 결합성**|
|[멤버 포인터 (개체 또는 포인터)](../cpp/pointer-to-member-operators-dot-star-and-star.md)|[. &#42; 또는->&#42;](../cpp/pointer-to-member-operators-dot-star-and-star.md)|
|**그룹 5 우선 순위, 왼쪽에서 오른쪽으로 결합성**|
|[곱하기](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[&#42;](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[나누기](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[/](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[모듈러스](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[%](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|**그룹 6 우선 순위, 왼쪽에서 오른쪽으로 결합성**|
|[더하기](../cpp/additive-operators-plus-and.md)|[+](../cpp/additive-operators-plus-and.md)|
|[빼기](../cpp/additive-operators-plus-and.md)|[-](../cpp/additive-operators-plus-and.md)|
|**그룹 7 우선 순위, 왼쪽에서 오른쪽으로의 결합성**|
|[왼쪽 시프트](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[<<](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|[오른쪽 시프트](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[>>](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|**그룹 8 우선 순위, 왼쪽에서 오른쪽으로의 결합성**|
|[보다 작음](../cpp/relational-operators-equal-and-equal.md)|[<](../cpp/relational-operators-equal-and-equal.md)|
|[보다 큼](../cpp/relational-operators-equal-and-equal.md)|[>](../cpp/relational-operators-equal-and-equal.md)|
|[작거나 같음](../cpp/relational-operators-equal-and-equal.md)|[<=](../cpp/relational-operators-equal-and-equal.md)|
|[크거나 같음](../cpp/relational-operators-equal-and-equal.md)|[>=](../cpp/relational-operators-equal-and-equal.md)|
|**그룹 9 우선 순위, 왼쪽에서 오른쪽으로의 결합성**|
|[같음](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[==](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|[같지 않음](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[!=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|**그룹 10 우선 순위 왼쪽에서 오른쪽 결합성**|
|[비트 AND](../cpp/bitwise-and-operator-amp.md)|[&amp;](../cpp/bitwise-and-operator-amp.md)|
|**그룹 11 우선 순위, 왼쪽에서 오른쪽으로 결합성**|
|[배타적 비트 OR](../cpp/bitwise-exclusive-or-operator-hat.md)|[^](../cpp/bitwise-exclusive-or-operator-hat.md)|
|**그룹 12 우선 순위, 왼쪽에서 오른쪽으로의 결합성**|
|[포괄적 비트 OR](../cpp/bitwise-inclusive-or-operator-pipe.md)|[&#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)|
|**그룹 13 우선 순위, 왼쪽에서 오른쪽으로 결합성**|
|[논리적 AND](../cpp/logical-and-operator-amp-amp.md)|[&amp;&amp;](../cpp/logical-and-operator-amp-amp.md)|
|**그룹 14 우선 순위, 왼쪽에서 오른쪽으로 결합성**|
|[논리적 OR](../cpp/logical-or-operator-pipe-pipe.md)|[&#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)|
|**그룹 15 우선 순위, 오른쪽에서 왼쪽으로의 연관성**|
|[Defined](../cpp/conditional-operator-q.md)|[? :](../cpp/conditional-operator-q.md)|
|**그룹 16 우선 순위, 오른쪽에서 왼쪽 결합성**|
|[할당](../cpp/assignment-operators.md)|[=](../cpp/assignment-operators.md)|
|[곱하기 할당](../cpp/assignment-operators.md)|[&#42;=](../cpp/assignment-operators.md)|
|[나누기 할당](../cpp/assignment-operators.md)|[/=](../cpp/assignment-operators.md)|
|[모듈러스 할당](../cpp/assignment-operators.md)|[%=](../cpp/assignment-operators.md)|
|[추가 할당](../cpp/assignment-operators.md)|[+=](../cpp/assignment-operators.md)|
|[빼기 대입](../cpp/assignment-operators.md)|[-=](../cpp/assignment-operators.md)|
|[왼쪽 시프트 할당](../cpp/assignment-operators.md)|[<<=](../cpp/assignment-operators.md)|
|[오른쪽 시프트 할당](../cpp/assignment-operators.md)|[>>=](../cpp/assignment-operators.md)|
|[비트 and 대입](../cpp/assignment-operators.md)|[&amp;=](../cpp/assignment-operators.md)|
|[포괄적 비트 OR 대입](../cpp/assignment-operators.md)|[&#124;=](../cpp/assignment-operators.md)|
|[배타적 비트 OR 대입](../cpp/assignment-operators.md)|[^=](../cpp/assignment-operators.md)|
|**그룹 17 우선 순위, 오른쪽에서 왼쪽으로의 연관성**|
|[throw 식](../cpp/try-throw-and-catch-statements-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)|
|**그룹 18 우선 순위, 왼쪽에서 오른쪽으로의 결합성**|
|[쉼표](../cpp/comma-operator.md)|[,](../cpp/comma-operator.md)|

## <a name="see-also"></a>참고 항목

[연산자 오버로드](operator-overloading.md)

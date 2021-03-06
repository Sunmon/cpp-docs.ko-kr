---
title: 표준 변환
ms.date: 10/02/2019
helpviewer_keywords:
- standard conversions, categories of
- L-values [C++]
- conversions, standard
ms.assetid: ce7ac8d3-5c99-4674-8229-0672de05528d
ms.openlocfilehash: 41ad348b7109451f519c44f685cea0a271f71925
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161012"
---
# <a name="standard-conversions"></a>표준 변환

C++ 언어에서는 기본 형식 간의 변환을 정의합니다. 또한 포인터, 참조 및 멤버 포인터 파생 형식에 대한 변환도 정의합니다. 이러한 변환을 *표준 변환*이라고 합니다.

이 단원에서는 다음과 같은 표준 변환에 대해 설명합니다.

- 정수 계열 확장

- 정수 계열 변환

- 부동 변환

- 부동 및 정수 계열 변환

- 산술 변환

- 포인터 변환

- 참조 변환

- 멤버 포인터 변환

  > [!NOTE]
  > 사용자 정의 형식은 고유한 변환을 지정할 수 없습니다. 사용자 정의 형식의 변환은 [생성자](../cpp/constructors-cpp.md) 및 [변환](../cpp/user-defined-type-conversions-cpp.md)에서 설명 합니다.

다음 코드에서는 변환을 발생시킵니다(이 예제의 경우 정수 계열 확장).

```cpp
long  long_num1, long_num2;
int   int_num;

// int_num promoted to type long prior to assignment.
long_num1 = int_num;

// int_num promoted to type long prior to multiplication.
long_num2 = int_num * long_num2;
```

참조 형식을 생성하는 경우에만 변환의 결과가 l-value입니다. 예를 들어 `operator int&()`로 선언 된 사용자 정의 변환은 참조를 반환 하며 l-value입니다. 그러나 `operator int()`로 선언 된 변환은 개체를 반환 하 고 l-value는 반환 하지 않습니다.

## <a name="integral-promotions"></a>정수 계열 확장

정수 계열 형식의 개체는 더 큰 값 집합을 나타낼 수 있는 다른 더 광범위 한 정수 계열 형식으로 변환할 수 있습니다. 이러한 확대 형식의 변환을 *정수 계열 확장*이라고 합니다. 정수 계열 확장을 사용 하면 다른 정수 계열 형식을 사용할 수 있는 모든 위치에서 식에 다음 형식을 사용할 수 있습니다.

- **Char** 및 **short int** 형식의 개체, 리터럴 및 상수

- 열거형 유형

- **int** 비트 필드

- Enumerators

C++승격은 승격 전 값과 동일 하 게 승격 된 후의 값을 "값 유지" 합니다. 값 유지 승격에서 short 정수 형식 (예: 비트 필드 또는 **char**형식의 개체)의 개체는 int 형식이 원래 형식의 전체 범위를 나타낼 **수 있는** 경우 **int** 형식으로 승격 됩니다. **Int** 가 값의 전체 범위를 나타낼 수 없는 경우 개체는 **unsigned int**형식으로 승격 됩니다.  이 전략은 표준 C에서 사용 되는 전략과 동일 하지만 값 유지 변환은 개체의 "크기나"를 유지 하지 않습니다.

값을 보존하는 확장과 부호 유부를 보존하는 확장은 보통 동일한 결과를 생성합니다. 그러나 승격 된 개체가 다음과 같이 표시 되는 경우 다른 결과를 생성할 수 있습니다.

- `/`, `%`, `/=`, `%=`, `<`, `<=`, `>`또는 `>=`의 피연산자

   이 연산자는 부호를 사용하여 결과를 확인합니다. 값-보존 및 서명 유지 승격은 이러한 피연산자에 적용 될 때 다른 결과를 생성 합니다.

- `>>` 또는 `>>=`의 왼쪽 피연산자

   이러한 연산자는 시프트 연산에서 부호 있는 수량과 부호 없는 수량을 다르게 처리 합니다. 부호 있는 수량의 경우 오른쪽 시프트 연산은 부호 비트를 비워진 비트 위치로 전파 하 고, 비워진 비트 위치는 부호 없는 수량으로 0으로 채워집니다.

- 오버 로드 된 함수 또는 오버 로드 된 연산자의 피연산자에 대 한 인수 이거나, 인수 일치를 위해 피연산자 형식의 크기나에 따라 달라 집니다. 오버 로드 된 연산자를 정의 하는 방법은 [오버 로드 된 연산자](../cpp/operator-overloading.md)를 참조 하세요.

## <a name="integral-conversions"></a>정수 계열 변환

정수 *계열 변환은* 정수 계열 형식 간의 변환입니다. 정수 계열 형식은 **char**, **short** (또는 **short int**), **int**, **long**, **long long**입니다. 이러한 형식은 **signed** 또는 **unsigned**로 한정 될 수 있으며, **부호** 없는 **int**의 약어로 사용할 수 있습니다.

### <a name="signed-to-unsigned"></a>signed에서 unsigned로 변환

부호가 있는 정수 계열 형식의 개체를 부호가 없는 해당 형식으로 변환할 수 있습니다. 이러한 변환이 발생 하면 실제 비트 패턴이 변경 되지 않습니다. 그러나 데이터의 해석이 변경 됩니다. 다음과 같은 코드를 생각해 볼 수 있습니다.

```cpp
#include <iostream>

using namespace std;
int main()
{
    short  i = -3;
    unsigned short u;

    cout << (u = i) << "\n";
}
// Output: 65533
```

앞의 예제에서 부호 있는 **short**`i`는 정의 되 고 음수로 초기화 됩니다. 식 `(u = i)`를 `u`할당 하기 전에 `i`을 **unsigned short** 로 변환 합니다.

### <a name="unsigned-to-signed"></a>unsigned에서 signed로 변환

부호 없는 정수 계열 형식의 개체를 부호 있는 해당 형식으로 변환할 수 있습니다. 그러나 부호 없는 값이 부호 있는 형식의 표현할 수 있는 범위 밖에 있는 경우 다음 예제와 같이 결과에 올바른 값이 포함 되지 않습니다.

```cpp
#include <iostream>

using namespace std;
int main()
{
short  i;
unsigned short u = 65533;

cout << (i = u) << "\n";
}
//Output: -3
```

앞의 예제에서 `u`은 식 `(i = u)`를 평가 하기 위해 서명 된 수량으로 변환 해야 하는 **부호 없는 short** 정수 개체입니다. 해당 값은 **signed short**에서 제대로 표현할 수 없기 때문에 데이터는 표시 된 대로 잘못 해석 됩니다.

## <a name="floating-point-conversions"></a>부동 소수점 변환

부동 형식의 개체를 보다 정확한 부동 형식으로 안전하게 변환할 수 있습니다. 즉, 변환으로 인해 중요도가 떨어지지 않습니다. 예를 들어 **float** 에서 **double** 로 또는 **double** 에서 **long double** 로의 변환은 안전 하 고 값은 변경 되지 않습니다.

부동 형식의 개체는 해당 형식으로 표현할 수 있는 범위에 있는 경우 보다 정확한 형식으로 변환 될 수도 있습니다. 부동 형식의 범위는 [부동 제한](../cpp/floating-limits.md) 을 참조 하세요. 원래 값을 정확 하 게 표현할 수 없는 경우 다음으로 높은 값 이나 다음으로 낮은 표현할 수 있는 값으로 변환할 수 있습니다. 이러한 값이 없으면 결과가 정의 되지 않습니다. 다음과 같은 예제를 참조하세요.

```cpp
cout << (float)1E300 << endl;
```

**Float** 형식으로 표현할 수 있는 최대값은 3.402823466 3.402823 (1E300 보다 훨씬 작음)입니다. 따라서 숫자가 무한대로 변환 되 고 결과는 "inf"입니다.

## <a name="conversions-between-integral-and-floating-point-types"></a>정수 계열 및 부동 소수점 형식 간의 변환

특정 식은 부동 형식의 개체가 정수 계열 형식으로 변환되도록 하거나 그 반대로 변환되도록 할 수 있습니다. 정수 계열 형식의 개체를 부동 형식으로 변환 하 고 원래 값을 정확 하 게 표현할 수 없는 경우 결과는 다음으로 높은 표현 가능한 값 또는 그 다음으로 낮은 표현 가능한 값 중 하나입니다.

부동 형식의 개체가 정수 계열 형식으로 변환 되 면 소수 부분이 *잘리거나*0으로 반올림 됩니다. 1\.3과 같은 숫자는 1로 변환 되 고-1.3은-1로 변환 됩니다. 잘린 값이 가장 높은 표현 가능한 값 보다 크거나 가장 작은 표현 가능한 값 보다 작으면 결과가 정의 되지 않습니다.

## <a name="arithmetic-conversions"></a>산술 변환

많은 이항 연산자 ( [이항 연산자를 사용 하는 식](../cpp/expressions-with-binary-operators.md)에서 설명)가 피연산자를 변환 하 고 동일한 방식으로 결과를 생성 합니다. 이러한 연산자의 원인을 *일반적인 산술 변환*이라고 합니다. 네이티브 형식이 다른 피연산자의 산술 변환은 다음 표와 같이 수행 됩니다. typedef 형식은 해당 기본 네이티브 형식에 따라 동작합니다.

### <a name="conditions-for-type-conversion"></a>형식 변환 조건

|조건 충족|변환|
|--------------------|----------------|
|두 피연산자 중 하나가 **long double**형식입니다.|다른 피연산자는 **long double**형식으로 변환 됩니다.|
|이전 조건이 충족 되지 않고 피연산자 중 하나가 **double**형식입니다.|다른 피연산자는 **double**형식으로 변환 됩니다.|
|이전 조건이 충족 되지 않고 피연산자 중 하나가 **float**유형입니다.|다른 피연산자는 **float**형식으로 변환 됩니다.|
|이전 조건이 충족되지 않았습니다(부동 형식인 피연산자가 없음).|피연산자는 다음과 같이 정수 계열 확장을 가져옵니다.<br /><br />-피연산자 중 하나가 **부호 없는 long**형식인 경우 다른 피연산자는 **unsigned long**형식으로 변환 됩니다.<br />-이전 조건이 충족 되지 않았으며 피연산자 중 하나가 **long** 형식이 고 다른 피연산자가 **부호 없는 int**형식인 경우 두 피연산자는 모두 **unsigned long**형식으로 변환 됩니다.<br />-앞의 두 조건이 충족 되지 않고 피연산자 중 하나가 **long**형식인 경우 다른 피연산자는 **long**형식으로 변환 됩니다.<br />-앞의 세 조건이 충족 되지 않고 피연산자 중 하나가 **부호 없는 int**형식인 경우 다른 피연산자는 **unsigned int**형식으로 변환 됩니다.<br />-앞의 조건이 모두 충족 되지 않는 경우 두 피연산자가 모두 **int**형식으로 변환 됩니다.|

다음 코드에서는 표에 설명된 변환 규칙을 보여 줍니다.

```cpp
double dVal;
float fVal;
int iVal;
unsigned long ulVal;

int main() {
   // iVal converted to unsigned long
   // result of multiplication converted to double
   dVal = iVal * ulVal;

   // ulVal converted to float
   // result of addition converted to double
   dVal = ulVal + fVal;
}
```

위의 예제에서 첫 번째 문은 `iVal`과 `ulVal`이라는 두 정수 계열 형식을 곱한 것입니다. 조건이 충족 되는 경우 피연산자가 부동 형식이 아니고 피연산자 중 하나가 **부호 없는 int**형식입니다. 따라서 다른 피연산자 `iVal`는 **unsigned int**형식으로 변환 됩니다. 그런 다음 결과가 `dVal`에 할당 됩니다. 여기서 충족 되는 조건은 하나의 피연산자가 **double**형식 이므로 곱셈의 **부호 없는 int** 결과가 **double**형식으로 변환 됩니다.

앞의 예제에서 두 번째 문은 **float** 및 정수 계열 형식 `fVal` 및 `ulVal`를 추가 하는 것을 보여 줍니다. `ulVal` 변수는 **float** 형식으로 변환 됩니다 (테이블의 세 번째 조건). 더하기의 결과는 **double** 형식으로 변환 되 고 (테이블의 두 번째 조건) `dVal`에 할당 됩니다.

## <a name="pointer-conversions"></a>포인터 변환

초기화, 할당, 비교 및 기타 식 실행 중에 포인터가 변환될 수 있습니다.

### <a name="pointer-to-classes"></a>클래스 포인터

클래스에 대한 포인터가 기본 클래스에 대한 포인터로 변환될 수 있는 두 가지 경우가 있습니다.

첫 번째 경우는 지정된 기본 클래스에 액세스할 수 있고 변환이 명확한 경우입니다. 모호한 기본 클래스 참조에 대 한 자세한 내용은 [여러 기본 클래스](../cpp/multiple-base-classes.md)를 참조 하세요.

기본 클래스에 액세스할 수 있는지 여부는 파생에서 사용되는 상속의 종류에 따라 달라집니다. 다음 그림에 나와 있는 상속을 살펴보십시오.

![기본&#45;클래스 액세스 가능성을 보여 주는 상속 그래프](../cpp/media/vc38xa1.gif "기본&#45;클래스 액세스 가능성을 보여 주는 상속 그래프") <br/>
기본 클래스 액세스 가능성을 보여 주는 상속 그래프

다음 표에서는 그림에 나와 있는 상황에 대한 기본 클래스 액세스 가능성을 보여 줍니다.

|함수 형식|파생|B*에서 A*로의 변환이<br /><br /> B *\* 법적으로|
|----------------------|----------------|-------------------------------------------|
|외부(클래스 범위가 아닌) 함수|프라이빗|예|
||보호됨|예|
||공용|yes|
|B 멤버 함수(B 범위에 있음)|프라이빗|yes|
||보호됨|yes|
||공용|yes|
|C 멤버 함수(C 범위에 있음)|프라이빗|예|
||보호됨|yes|
||공용|yes|

클래스에 대한 포인터가 기본 클래스에 대한 포인터로 변환될 수 있는 두 번째 경우는 명시적 형식 변환을 사용하는 경우입니다. 명시적 형식 변환에 대 한 자세한 내용은 [명시적 형식 변환 연산자](explicit-type-conversion-operator-parens.md)를 참조 하세요.

이러한 변환의 결과는 하위 개체에 *대 한 포인터로, 기본*클래스에서 완전히 설명 하는 개체 부분입니다.

다음 코드에서는 두 클래스 `A` 및 `B`를 정의합니다. `B`는 `A`에서 파생됩니다. 상속에 대 한 자세한 내용은 [파생 클래스](../cpp/inheritance-cpp.md)를 참조 하세요. 그런 다음 `bObject`, `B`형식의 개체 및 개체를 가리키는 두 개의 포인터 (`pA` 및 `pB`)를 정의 합니다.

```cpp
// C2039 expected
class A
{
public:
    int AComponent;
    int AMemberFunc();
};

class B : public A
{
public:
    int BComponent;
    int BMemberFunc();
};
int main()
{
   B bObject;
   A *pA = &bObject;
   B *pB = &bObject;

   pA->AMemberFunc();   // OK in class A
   pB->AMemberFunc();   // OK: inherited from class A
   pA->BMemberFunc();   // Error: not in class A
}
```

`pA` 포인터는 `A *` 형식이고, 이는 "`A` 형식의 개체에 대한 포인터"로 해석될 수 있습니다. `bObject` (예: `BComponent` 및 `BMemberFunc`)의 멤버는 `B` 형식에 고유 하므로 `pA`을 통해 액세스할 수 없습니다. `pA` 포인터는 `A` 클래스에서 정의된 개체의 특성(멤버 함수 및 데이터)에만 액세스할 수 있습니다.

### <a name="pointer-to-function"></a>함수 포인터

함수에 대 한 포인터는 해당 포인터를 저장할 수 있을 만큼 충분히 크면 `void *` `void *`형식으로 변환할 수 있습니다.

### <a name="pointer-to-void"></a>void 포인터

**Void** 형식에 대 한 포인터는 다른 형식에 대 한 포인터로 변환 될 수 있지만 C와는 달리 명시적 형식 캐스트를 사용 합니다. 형식에 대 한 포인터는 암시적으로 **void**형식에 대 한 포인터로 변환 될 수 있습니다. 형식의 불완전 한 개체에 대 한 포인터는 **void** (암시적) 및 back (명시적)으로의 포인터로 변환 될 수 있습니다. 이러한 변환 결과는 원래 포인터 값과 같습니다. 개체는 선언 되었지만 불완전 한 것으로 간주 되지만 크기 또는 기본 클래스를 결정 하는 데 사용할 수 있는 정보가 부족 합니다.

**Const** 또는 **volatile** 이 아닌 개체에 대 한 포인터는 `void *`형식의 포인터로 암시적으로 변환 될 수 있습니다.

### <a name="const-and-volatile-pointers"></a>const 및 volatile 포인터

C++**const** 또는 **volatile** 형식에서 **const** 또는 **volatile**이 아닌 형식으로의 표준 변환을 제공 하지 않습니다. 하지만 모든 종류의 변환은 명시적 형식 캐스트를 사용하여 지정할 수 있습니다(안전하지 않은 변환 포함).

> [!NOTE]
> C++정적 멤버에 대 한 포인터를 제외 하 고 멤버에 대 한 포인터는 일반 포인터와 다르며 표준 변환이 동일 하지 않습니다. 정적 멤버에 대한 포인터는 일반 포인터이며 일반 포인터와 동일한 변환이 적용됩니다.

### <a name="null-pointer-conversions"></a>null 포인터 변환

0으로 계산 되는 정수 계열 상수 식 또는 포인터 형식으로 캐스팅 된 이러한 식은 *null 포인터*라는 포인터로 변환 됩니다. 이 포인터는 항상 유효한 개체나 함수에 대 한 포인터와 같지 않은지 비교 합니다. 예외는 동일한 오프셋을 사용 하 고 다른 개체를 가리킬 수 있는 기반 개체에 대 한 포인터입니다.

C + + 11에서는 C 스타일 null 포인터에 [nullptr](../cpp/nullptr.md) 형식이 선호 되어야 합니다.

### <a name="pointer-expression-conversions"></a>포인터 식 변환

배열 형식의 식을 동일한 형식의 포인터로 변환할 수 있습니다. 변환 결과는 첫 번째 배열 요소의 포인터입니다. 다음 예제에서는 이러한 변환에 대해 설명합니다.

```cpp
char szPath[_MAX_PATH]; // Array of type char.
char *pszPath = szPath; // Equals &szPath[0].
```

특정 형식을 반환하는 함수를 도출하는 식은 해당 형식을 반환하는 함수의 포인터로 변환됩니다. 단, 다음의 경우는 제외됩니다.

- 식은 주소 연산자 ( **&** )에 대 한 피연산자로 사용 됩니다.

- 해당 식이 함수 호출 연산자의 피연산자로 사용됩니다.

## <a name="reference-conversions"></a>참조 변환

이러한 경우 클래스에 대 한 참조를 기본 클래스에 대 한 참조로 변환할 수 있습니다.

- 지정 된 기본 클래스에 액세스할 수 있습니다.

- 해당 변환은 명확합니다. (모호한 기본 클래스 참조에 대 한 자세한 내용은 [여러 기본 클래스](../cpp/multiple-base-classes.md)를 참조 하세요.)

변환의 결과는 기본 클래스를 나타내는 하위 개체에 대한 포인터입니다.

## <a name="pointer-to-member"></a>멤버 포인터

할당, 초기화, 비교 및 기타 식 실행 중에 클래스 멤버에 대한 포인터가 변환될 수 있습니다. 이 단원에서는 다음과 같은 멤버 포인터 변환에 대해 설명합니다.

### <a name="pointer-to-base-class-member"></a>기본 클래스 멤버 포인터

기본 클래스의 멤버에 대한 포인터는 다음 조건이 충족될 때 파생되는 클래스의 멤버에 대한 포인터로 변환할 수 있습니다.

- 포인터에서 파생 클래스 및 기본 클래스 포인터로의 역 변환에 액세스할 수 있습니다.

- 파생 클래스가 기본 클래스에서 가상으로 상속하지 않습니다.

왼쪽 피연산자가 멤버에 대한 포인터인 경우 오른쪽 피연산자가 멤버 포인터 형식이거나 0으로 계산되는 상수 식이어야 합니다. 이 대입은 다음과 같은 경우에만 유효합니다.

- 오른쪽 피연산자가 왼쪽 피연산자와 같은 클래스의 멤버에 대한 포인터입니다.

- 왼쪽 피연산자가 오른쪽 피연산자의 클래스로부터 공개적으로 명확하게 파생된 클래스의 멤버에 대한 포인터입니다.

### <a name="null-pointer-to-member-conversions"></a>멤버 변환에 대 한 null 포인터

0으로 계산 되는 정수 계열 상수 식은 null 포인터로 변환 됩니다. 이 포인터는 항상 유효한 개체나 함수에 대 한 포인터와 같지 않은지 비교 합니다. 예외는 동일한 오프셋을 사용 하 고 다른 개체를 가리킬 수 있는 기반 개체에 대 한 포인터입니다.

다음 코드에서는 `i` 클래스의 `A` 멤버에 대한 포인터 정의에 대해 설명합니다. `pai` 포인터는 0으로 초기화되어 null 포인터가 됩니다.

```cpp
class A
{
public:
int i;
};

int A::*pai = 0;

int main()
{
}
```

## <a name="see-also"></a>참고 항목

[C++언어 참조](../cpp/cpp-language-reference.md)

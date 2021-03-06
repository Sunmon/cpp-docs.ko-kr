---
title: 변환 단위 및 링크 (c + +)
ms.date: 12/11/2019
ms.assetid: a6493ba0-24e2-4c89-956e-9da1dea660cb
ms.openlocfilehash: e964a3c70c138caf8848e6a6366097cbfb90f548
ms.sourcegitcommit: f7ebdfc3a260778c2ef938747cba1376c70ced15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84108397"
---
# <a name="translation-units-and-linkage"></a>변환 단위 및 링크

C + + 프로그램에서 변수나 함수 이름과 같은 *기호*는 해당 범위 내에서 여러 번 선언 될 수 있지만 한 번만 정의할 수 있습니다. 이 규칙은 "단일 정의 규칙" (ODR)입니다. *선언은* 프로그램에 이름을 도입 하거나 다시 소개 합니다. *정의* 에는 이름이 도입 됩니다. 이름이 변수를 나타내는 경우 정의에서 해당 변수를 명시적으로 초기화 합니다. *함수 정의* 는 시그니처와 함수 본문으로 구성 됩니다. 클래스 정의는 클래스 이름 다음에 모든 클래스 멤버를 나열 하는 블록으로 구성 됩니다. 멤버 함수의 본문은 선택적으로 다른 파일에서 별도로 정의할 수 있습니다.

다음 예제에서는 몇 가지 선언을 보여 줍니다.

```cpp
int i;
int f(int x);
class C;
```

다음 예제에서는 몇 가지 정의를 보여 줍니다.

```cpp
int i{42};
int f(int x){ return x * i; }
class C {
public:
   void DoSomething();
};
```

프로그램은 하나 이상의 *변환 단위로*구성 됩니다. 변환 단위는 구현 파일과이 파일에 직접 또는 간접적으로 포함 된 모든 헤더로 구성 됩니다. 일반적으로 구현 파일의 파일 확장명은 *cpp* 또는 *.cxx*입니다. 헤더 파일에는 일반적으로 *h* 또는 *배치*의 확장명이 있습니다. 각 변환 단위는 컴파일러에 의해 독립적으로 컴파일됩니다. 컴파일이 완료 되 면 링커는 컴파일된 변환 단위를 단일 *프로그램*으로 병합 합니다. ODR 규칙 위반은 일반적으로 링커 오류로 표시 됩니다. 링커 오류는 동일한 이름에 서로 다른 변환 단위에 두 개의 다른 정의가 있을 때 발생 합니다.

일반적으로 여러 파일에 걸쳐 변수를 표시 하는 가장 좋은 방법은 헤더 파일에 배치 하는 것입니다. 그런 다음 선언이 필요한 모든 *.cpp* 파일에 #include 지시어를 추가 합니다. 을 추가 하면 헤더 내용 주위에 *가드가 포함* 되므로 선언 된 이름이 한 번만 정의 됩니다.

C + + 20에서 [모듈](modules-cpp.md) 은 헤더 파일 대신 향상 된 기능으로 도입 되었습니다.

일부 경우에는 전역 변수 또는 클래스를 *cpp* 파일에 선언 해야 할 수 있습니다. 이러한 경우에는 이름에 포함 된 *링크* 종류를 컴파일러 및 링커에 알리는 방법이 필요 합니다. 링크 형식은 개체 이름이 한 파일에만 적용 되는지 아니면 모든 파일에만 적용 되는지를 지정 합니다. 링크의 개념은 전역 이름에만 적용 됩니다. 링크의 개념은 범위 내에서 선언 된 이름에는 적용 되지 않습니다. 범위는 함수 또는 클래스 정의에서와 같은 바깥쪽 중괄호 집합으로 지정 됩니다.

## <a name="external-vs-internal-linkage"></a>외부 및 내부 링크

*Free 함수* 는 전역 또는 네임 스페이스 범위에서 정의 되는 함수입니다. Const가 아닌 전역 변수와 free 함수는 기본적으로 *외부 링크*를 포함 합니다. 프로그램의 모든 변환 단위에서 볼 수 있습니다. 따라서 다른 전역 개체는 해당 이름을 가질 수 없습니다. *내부 링크* 를 포함 하거나 링크를 포함 *하지* 않는 기호는 선언 된 변환 단위 내 에서만 표시 됩니다. 이름에 내부 링크가 있으면 동일한 이름이 다른 변환 단위에 있을 수 있습니다. 클래스 정의 나 함수 본문 내에 선언 된 변수에는 링크가 없습니다.

명시적으로 **정적**으로 선언 하 여 전역 이름에 내부 링크를 강제로 적용할 수 있습니다. 이렇게 하면 해당 표시 유형이 선언 된 것과 동일한 변환 단위로 표시 됩니다. 이 컨텍스트에서 **static** 은 지역 변수에 적용 될 때와는 다른 것을 의미 합니다.

다음 개체는 기본적으로 내부 링크를 포함 합니다.

- const 개체
- constexpr 개체
- 형식 정의
- 네임 스페이스 범위의 정적 개체

Const 개체 외부 링크를 제공 하려면 **extern** 으로 선언 하 고 값을 할당 합니다.

```cpp
extern const int value = 42;
```

자세한 내용은 [extern](extern-cpp.md) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[기본 개념](../cpp/basic-concepts-cpp.md)

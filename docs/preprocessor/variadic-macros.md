---
title: Variadic 매크로
ms.date: 10/17/2019
helpviewer_keywords:
- variadic macros [C++]
- __VA_ARGS__ variadic macro specifier
ms.assetid: 51e757dc-0134-4bb2-bb74-64ea5ad75134
ms.openlocfilehash: de4d3a7f03f613cb058e564664f01837df23aefb
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72587888"
---
# <a name="variadic-macros"></a>Variadic 매크로

Variadic 매크로는 가변 개수의 인수를 포함 하는 함수 형태의 매크로입니다.

## <a name="remarks"></a>주의

Variadic 매크로를 사용 하려면 매크로 정의에서 줄임표를 최종 형식 인수로 지정 하 고, 대체 식별자 `__VA_ARGS__` 정의에서 추가 인수를 삽입 하는 데 사용할 수 있습니다.  `__VA_ARGS__`는 줄임표와 일치 하는 모든 인수로 대체 됩니다 (쉼표 포함).

C 표준은 인수가 후행 쉼표를 사용 하는 식으로 확인 되지 않도록 하나 이상의 인수를 줄임표에 전달 하도록 지정 합니다. 기존 Microsoft C++ 구현은 줄임표에 전달 된 인수가 없는 경우 후행 쉼표를 표시 하지 않습니다. @No__t_0 컴파일러 옵션이 설정 된 경우 후행 쉼표는 표시 되지 않습니다.

## <a name="example"></a>예제

```cpp
// variadic_macros.cpp
#include <stdio.h>
#define EMPTY

#define CHECK1(x, ...) if (!(x)) { printf(__VA_ARGS__); }
#define CHECK2(x, ...) if ((x)) { printf(__VA_ARGS__); }
#define CHECK3(...) { printf(__VA_ARGS__); }
#define MACRO(s, ...) printf(s, __VA_ARGS__)

int main() {
    CHECK1(0, "here %s %s %s", "are", "some", "varargs1(1)\n");
    CHECK1(1, "here %s %s %s", "are", "some", "varargs1(2)\n");   // won't print

    CHECK2(0, "here %s %s %s", "are", "some", "varargs2(3)\n");   // won't print
    CHECK2(1, "here %s %s %s", "are", "some", "varargs2(4)\n");

    // always invokes printf in the macro
    CHECK3("here %s %s %s", "are", "some", "varargs3(5)\n");

    MACRO("hello, world\n");

    MACRO("error\n", EMPTY); // would cause error C2059, except VC++
                             // suppresses the trailing comma
}
```

```Output
here are some varargs1(1)
here are some varargs2(4)
here are some varargs3(5)
hello, world
error
```

## <a name="see-also"></a>참조

[매크로(C/C++)](../preprocessor/macros-c-cpp.md)

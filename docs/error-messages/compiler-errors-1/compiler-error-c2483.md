---
title: 컴파일러 오류 C2483
ms.date: 09/15/2017
f1_keywords:
- C2483
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
ms.openlocfilehash: 20b08c0d2cd89224ed3d3b8b34915deb947b0b4b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205116"
---
# <a name="compiler-error-c2483"></a>컴파일러 오류 C2483

>'*identifier*': 생성자 또는 소멸자가 있는 개체는 ' thread '로 선언할 수 없습니다.

이 오류 메시지는 Visual Studio 2015 이상 버전에서 사용 되지 않습니다. 이전 버전에서는 `thread` 특성으로 선언 된 변수를 생성자 또는 런타임 계산이 필요한 다른 식으로 초기화할 수 없습니다. 정적 식은 `thread` 데이터를 초기화 하는 데 필요 합니다.

## <a name="example"></a>예제

다음 샘플에서는 Visual Studio 2013 및 이전 버전에서 C2483를 생성 합니다.

```cpp
// C2483.cpp
// compile with: /c
__declspec(thread) struct A {
   A(){}
   ~A(){}
} aa;   // C2483 error

__declspec(thread) struct B {} b;   // OK
```

## <a name="see-also"></a>참고 항목

[thread](../../cpp/thread.md)

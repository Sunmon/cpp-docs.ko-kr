---
title: 컴파일러 오류 C2514
ms.date: 11/04/2016
f1_keywords:
- C2514
helpviewer_keywords:
- C2514
ms.assetid: 4b7085e5-6714-4261-80b7-bc72e64ab3e8
ms.openlocfilehash: e0153ec9d48225d153221f2192761da4023fab96
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746515"
---
# <a name="compiler-error-c2514"></a>컴파일러 오류 C2514

' class ': 클래스에 생성자가 없습니다.

클래스, 구조체 또는 공용 구조체에는 해당 클래스를 인스턴스화하는 데 사용 되는 매개 변수와 일치 하는 매개 변수 목록을 포함 하는 생성자가 없습니다.

클래스를 인스턴스화하려면 먼저 완전히 선언 해야 합니다.

다음 샘플에서는 C2514를 생성 합니다.

```cpp
// C2514.cpp
// compile with: /c
class f;

class g {
public:
    g (int x);
};

class fmaker {
   f *func1() {
      return new f(2);   // C2514
   }

   g *func2() {
      return new g(2);   // OK
   }
};
```

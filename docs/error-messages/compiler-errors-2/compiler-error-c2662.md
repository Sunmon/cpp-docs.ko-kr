---
title: 컴파일러 오류 C2662
ms.date: 11/04/2016
f1_keywords:
- C2662
helpviewer_keywords:
- C2662
ms.assetid: e172c2a4-f29e-4034-8232-e7dc6f83689f
ms.openlocfilehash: b2fa2643898fed510aa7cf0f483b538ebb33b033
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760454"
---
# <a name="compiler-error-c2662"></a>컴파일러 오류 C2662

' function ': ' this ' 포인터를 ' type1 '에서 ' type2 ' (으)로 변환할 수 없습니다.

컴파일러가 `this` 포인터를 `type1`에서 `type2`로 변환할 수 없습니다.

이 오류는 `const` 개체에 대해`const` 되지 않은 멤버 함수를 호출 하 여 발생할 수 있습니다.  가능한 해결 방법은 다음과 같습니다.

- 개체 선언에서 `const`를 제거 합니다.

- 멤버 함수에 `const`를 추가 합니다.

다음 샘플에서는 C2662를 생성 합니다.

```cpp
// C2662.cpp
class C {
public:
   void func1();
   void func2() const{}
} const c;

int main() {
   c.func1();   // C2662
   c.func2();   // OK
}
```

**/Clr**을 사용 하 여 컴파일하는 경우 `const` 또는 `volatile` 정규화 된 관리 되는 형식에 대해 함수를 호출할 수 없습니다. 관리 되는 클래스의 const 멤버 함수는 선언할 수 없으므로 const 관리 되는 개체에서 메서드를 호출할 수 없습니다.

```cpp
// C2662_b.cpp
// compile with: /c /clr
ref struct M {
   property M^ Type {
      M^ get() { return this; }
   }

   void operator=(const M %m) {
      M ^ prop = m.Type;   // C2662
   }
};

ref struct N {
   property N^ Type {
      N^ get() { return this; }
   }

   void operator=(N % n) {
      N ^ prop = n.Type;   // OK
   }
};
```

다음 샘플에서는 C2662를 생성 합니다.

```cpp
// C2662_c.cpp
// compile with: /c
// C2662 expected
typedef int ISXVD;
typedef unsigned char BYTE;

class LXBASE {
protected:
    BYTE *m_rgb;
};

class LXISXVD:LXBASE {
public:
   // Delete the following line to resolve.
   ISXVD *PMin() { return (ISXVD *)m_rgb; }

   ISXVD *PMin2() const { return (ISXVD *)m_rgb; };   // OK
};

void F(const LXISXVD *plxisxvd, int iDim) {
   ISXVD isxvd;
   // Delete the following line to resolve.
   isxvd = plxisxvd->PMin()[iDim];

   isxvd = plxisxvd->PMin2()[iDim];
}
```

---
title: 컴파일러 오류 C2932
ms.date: 11/04/2016
f1_keywords:
- C2932
helpviewer_keywords:
- C2932
ms.assetid: c28e88d9-e654-4367-bfb4-13c780bca9bd
ms.openlocfilehash: c1afe47e27cb38b2a3886854ce6efe34273c9132
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750106"
---
# <a name="compiler-error-c2932"></a>컴파일러 오류 C2932

'class': type-class-id가 'identifier'의 데이터 멤버로 재정의되었습니다.

제네릭 또는 템플릿 클래스를 데이터 멤버로 사용할 수 없습니다.

다음 샘플에서는 C2932를 생성합니다.

```cpp
// C2932.cpp
// compile with: /c
template<class T>
struct TC {};

struct MyStruct {
   int TC<int>;   // C2932
   int TC;   // OK
};
```

C2932는 제네릭을 사용하는 경우에도 발생할 수 있습니다.

```cpp
// C2932b.cpp
// compile with: /clr /c
generic<class T>
ref struct GC {};

struct MyStruct {
   int GC<int>;   // C2932
   int GC;   // OK
};
```

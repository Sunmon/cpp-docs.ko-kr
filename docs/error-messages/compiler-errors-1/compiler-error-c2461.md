---
title: 컴파일러 오류 C2461
ms.date: 11/04/2016
f1_keywords:
- C2461
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
ms.openlocfilehash: 3d290bd2288f76d0ddefa2057e3e01c9edc3cbc7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205324"
---
# <a name="compiler-error-c2461"></a>컴파일러 오류 C2461

> '*class*': 생성자 구문에 정식 매개 변수가 없습니다.

클래스에 대 한 생성자는 정식 매개 변수를 지정 하지 않습니다. 생성자 선언에는 형식 매개 변수 목록을 지정 해야 합니다. 목록은 비워 둘 수 있습니다.

이 문제를 해결 하려면 *클래스*::**클래스*의 선언 뒤에 괄호 쌍을 추가 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C2461를 수정 하는 방법을 보여 줍니다.

```cpp
// C2461.cpp
// compile with: /c
class C {
   C::C;     // C2461
   C::C();   // OK
};
```

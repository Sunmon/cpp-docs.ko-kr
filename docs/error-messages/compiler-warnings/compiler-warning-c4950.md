---
title: 컴파일러 경고 C4950
ms.date: 11/04/2016
f1_keywords:
- C4950
helpviewer_keywords:
- C4950
ms.assetid: 50226a5c-c664-4d09-ac59-e9e874ca244f
ms.openlocfilehash: 52c4de94dfe087b4dcf407295e556c9350b2cb8b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164991"
---
# <a name="compiler-warning-c4950"></a>컴파일러 경고 C4950

'type_or_member': 사용되지 않는 것으로 표시되었습니다.

멤버 또는 형식이 <xref:System.ObsoleteAttribute> 특성에서 사용 되지 않는 것으로 표시 되었습니다.

C4950은 항상 오류로 실행됩니다. [Warning](../../preprocessor/warning.md) pragma 지시문 또는 [/wd](../../build/reference/compiler-option-warning-level.md) 컴파일러 옵션을 사용 하 여이 경고를 해제할 수 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C4950을 생성합니다.

```cpp
// C4950.cpp
// compile with: /clr
using namespace System;

// Any reference to Func3 should generate an error with message
[System::ObsoleteAttribute("Will be removed in next version", true)]
Int32 Func3(Int32 a, Int32 b) {
   return (a + b);
}

int main() {
   Int32 MyInt3 = ::Func3(2, 2);   // C4950
}
```

---
title: 컴파일러 오류 C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: b166096390169939f01bcb976a57612f10f7df2e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201138"
---
# <a name="compiler-error-c3389"></a>컴파일러 오류 C3389

> /clr: pure 또는/clr: safe에는 __declspec (*키워드*)를 사용할 수 없습니다.

## <a name="remarks"></a>주의

**/Clr: pure** 및 **/clr: safe** 컴파일러 옵션은 visual studio 2015에서 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

사용 되는 [__declspec](../../cpp/declspec.md) 한정자는 프로세스별 상태별를 의미 합니다.  [/clr: pure](../../build/reference/clr-common-language-runtime-compilation.md) 는 [appdomain](../../cpp/appdomain.md) 당 상태별를 의미 합니다.  따라서 `keyword` **__declspec** 한정자를 사용 하 여 변수를 선언 하 고 **/clr: pure** 를 사용 하 여 컴파일하는 것은 허용 되지 않습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3389를 생성 합니다.

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```

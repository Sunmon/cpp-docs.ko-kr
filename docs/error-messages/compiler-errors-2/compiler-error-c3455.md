---
title: 컴파일러 오류 C3455
ms.date: 11/04/2016
f1_keywords:
- C3455
helpviewer_keywords:
- C3455
ms.assetid: 218e5cfe-5391-4eeb-81c2-85c47e3a6cd2
ms.openlocfilehash: e016105a53b4020ca8ed83a95b0c9b96036b1884
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756671"
---
# <a name="compiler-error-c3455"></a>컴파일러 오류 C3455

'attribute': 해당 인수와 일치하는 특성 생성자가 없습니다.

잘못된 값이 특성을 선언하는 데 사용되었습니다.  자세한 내용은 [attribute](../../windows/attributes/attribute.md) 를 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3455를 생성합니다.

```cpp
// C3455.cpp
// compile with: /clr /c
using namespace System;

[attribute("MyAt")]   // C3455
// try the following line instead
// [attribute(All)]
ref struct MyAttr {
   MyAttr() {}
};
```

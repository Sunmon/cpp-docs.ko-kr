---
title: 컴파일러 경고(수준 4) C4429
ms.date: 11/04/2016
f1_keywords:
- C4429
helpviewer_keywords:
- C4429
ms.assetid: a3e4cf1f-a869-4e47-834a-850c21eb5297
ms.openlocfilehash: 6702db4af5c31d21610e02b1a4ec75af27ad10f2
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990831"
---
# <a name="compiler-warning-level-4-c4429"></a>컴파일러 경고(수준 4) C4429

유니버설 문자 이름이 불완전 하거나 형식이 잘못 된 것 같습니다.

컴파일러가 잘못 된 형식의 유니버설 문자 이름일 수 있는 문자 시퀀스를 검색 했습니다. 유니버설 문자 이름은 `\u` 뒤에 네 개의 16 진수 숫자 또는 8 개의 16 진수가 있는 `\U` 합니다.

다음 샘플에서는 C4429를 생성 합니다.

```cpp
// C4429.cpp
// compile with: /W4 /WX
int \ug0e4 = 0;   // C4429
// Try the following line instead:
// int \u00e4 = 0;   // OK, a well-formed universal character name.
```

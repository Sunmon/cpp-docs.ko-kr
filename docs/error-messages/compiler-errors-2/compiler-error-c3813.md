---
title: 컴파일러 오류 C3813
ms.date: 11/04/2016
f1_keywords:
- C3813
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
ms.openlocfilehash: c16ce501e25040a7ac7672a9ea131b4fe89570f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165615"
---
# <a name="compiler-error-c3813"></a>컴파일러 오류 C3813

property 선언은 WinRT 또는 관리되는 형식의 정의 내에서만 사용할 수 있습니다.

[속성](../../dotnet/how-to-use-properties-in-cpp-cli.md) 은 관리 되는 형식 또는 Windows 런타임 형식 내 에서만 선언할 수 있습니다. 네이티브 형식은 `property` 키워드를 지원하지 않습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3813 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C3813.cpp
// compile by using: cl /c /clr C3813.cpp
class A
{
   property int Int; // C3813
};

ref class B
{
   property int Int; // OK - declared within managed type
};
```

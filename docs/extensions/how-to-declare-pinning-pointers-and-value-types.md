---
title: '방법: 고정 포인터 및 값 형식 선언'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- value types, declaring
- pinning pointers
ms.assetid: 57c5ec8a-f85a-48c4-ba8b-a81268bcede0
ms.openlocfilehash: 88ef7e82161703a272a571392fd66e6055371c61
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181969"
---
# <a name="how-to-declare-pinning-pointers-and-value-types"></a>방법: 고정 포인터 및 값 형식 선언

값 형식은 암시적으로 boxing할 수 있습니다. 그런 다음, 값 형식 개체 자체에 대한 고정 포인터를 선언하고 boxed 값 형식으로의 **pin_ptr**을 사용할 수 있습니다.

## <a name="example"></a>예제

### <a name="code"></a>코드

```cpp
// pin_ptr_value.cpp
// compile with: /clr
value struct V {
   int i;
};

int main() {
   V ^ v = gcnew V;   // imnplicit boxing
   v->i=8;
   System::Console::WriteLine(v->i);
   pin_ptr<V> mv = &*v;
   mv->i = 7;
   System::Console::WriteLine(v->i);
   System::Console::WriteLine(mv->i);
}
```

```Output
8
7
7
```

## <a name="see-also"></a>참고 항목

[pin_ptr(C++/CLI)](pin-ptr-cpp-cli.md)

---
title: switch_type (C++ COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.switch_type
helpviewer_keywords:
- switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
ms.openlocfilehash: b4264681a55f45c8a4a2696e8cebbbd0eb12a4ed
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214528"
---
# <a name="switch_type"></a>switch_type

Union 판별으로 사용 되는 변수의 형식을 식별 합니다.

## <a name="syntax"></a>구문

```cpp
[switch_type(
type
}]
```

### <a name="parameters"></a>매개 변수

*type*<br/>
스위치 형식은 정수, 문자, 부울 또는 열거형 형식일 수 있습니다.

## <a name="remarks"></a>주의

**Switch_type** C++ 특성에는 [switch_type](/windows/win32/Midl/switch-type) MIDL 특성과 동일한 기능이 있습니다.

C++특성은 캡슐화 된 [공용 구조체](/windows/win32/Midl/encapsulated-unions)를 지원 하지 않습니다. [캡슐화 되지 않은 공용 구조체](/windows/win32/Midl/nonencapsulated-unions) 는 다음 형식 으로만 지원 됩니다.

```cpp
// cpp_attr_ref_switch_type.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLibrary")];
[ export ]
struct SizedValue2 {
   [switch_type("char"), switch_is(kind)] union {
      [case(1), string]
         wchar_t* wval;
      [default, string]
         char* val;
   };
   char kind;
};
```

## <a name="example"></a>예제

**Switch_type**의 샘플 사용에 대해서는 [사례](case-cpp.md) 예를 참조 하세요.

## <a name="requirements"></a>요구 사항

### <a name="attribute-context"></a>특성 컨텍스트

|||
|-|-|
|**적용 대상**|**typedef**|
|**반복 가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[Typedef, Enum, Union 및 Struct 특성](typedef-enum-union-and-struct-attributes.md)<br/>
[export](export.md)

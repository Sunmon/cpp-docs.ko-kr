---
title: is_nothrow_assignable 클래스
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_assignable
helpviewer_keywords:
- is_nothrow_assignable
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
ms.openlocfilehash: 9ee8b5f97c92b6eb378db40f93696e5e6c554205
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456016"
---
# <a name="isnothrowassignable-class"></a>is_nothrow_assignable 클래스

형식의 값을 형식 *에* 할당할 수 있는지 여부를 테스트 하 고 할당이 throw 되지 않는 것으로 알려져 있는지 테스트 합니다.

## <a name="syntax"></a>구문

```cpp
template <class To, class From>
struct is_nothrow_assignable;
```

### <a name="parameters"></a>매개 변수

*받는 사람*\
할당을 받는 개체의 형식입니다.

*보낸 사람*\
값을 제공하는 개체의 형식입니다.

## <a name="remarks"></a>설명

`declval<To>() = declval<From>()` 식은 올바른 형식이어야 하며 throw되지 않는 것으로 컴파일러에 알려져 있어야 합니다. 및 *둘* 다  완전 한 형식, **void**또는 알 수 없는 바인딩된 배열 이어야 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** \<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고자료

[<type_traits>](../standard-library/type-traits.md)

---
title: '&lt;thread&gt;'
ms.date: 11/04/2016
f1_keywords:
- <thread>
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
ms.openlocfilehash: 7053402dfb566f10c7be4c0eebaef40f3d371f43
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460083"
---
# <a name="ltthreadgt"></a>&lt;thread&gt;

클래스 스레드 및 다양 \<한 지원 함수를 정의 하  는 > 표준 헤더 스레드를 포함 합니다.

## <a name="syntax"></a>구문

```cpp
#include <thread>
```

## <a name="remarks"></a>설명

> [!NOTE]
> **/Clr**을 사용 하 여 컴파일된 코드에서이 헤더는 차단 됩니다.

이 헤더에서 스레드가 지원 되는지 여부를 나타내는 0이 아닌 값으로 매크로를정의합니다.`__STDCPP_THREADS__`

## <a name="members"></a>멤버

### <a name="public-classes"></a>public 클래스

|이름|Description|
|----------|-----------------|
|[thread 클래스](../standard-library/thread-class.md)|응용 프로그램에서 실행 스레드를 관찰 하 고 관리 하는 데 사용 되는 개체를 정의 합니다.|

### <a name="public-structures"></a>공용 구조체

|이름|Description|
|----------|-----------------|
|[hash 구조체(C++ 표준 라이브러리)](../standard-library/hash-structure-stl.md)|에 `thread::id`의해 고유 하 게 결정 되는 값을 반환 하는 멤버 함수를 정의 합니다. 멤버 함수는 형식의 `thread::id` 값을 인덱스 값의 분포에 매핑하는 데 적합 한 [해시](../standard-library/hash-class.md) 함수를 정의 합니다.|

### <a name="public-functions"></a>Public 함수

|이름|Description|
|----------|-----------------|
|[get_id](../standard-library/thread-functions.md#get_id)|현재 실행 스레드를 고유하게 식별합니다.|
|[sleep_for](../standard-library/thread-functions.md#sleep_for)|호출 스레드를 차단합니다.|
|[sleep_until](../standard-library/thread-functions.md#sleep_until)|최소한 지정된 시간까지 호출 스레드를 차단합니다.|
|[swap](../standard-library/thread-functions.md#swap)|두 **스레드** 개체의 상태를 교환 합니다.|
|[yield](../standard-library/thread-functions.md#yield)|정상적인 경우라면 현재 스레드가 계속 실행되더라도 운영 체제에 다른 스레드를 실행할 것을 알립니다.|

### <a name="public-operators"></a>Public 연산자

|이름|Description|
|----------|-----------------|
|[operator > = 연산자](../standard-library/thread-operators.md#op_gt_eq)|하나의 `thread::id` 개체가 다른 개체보다 크거나 같은지를 확인합니다.|
|[operator > 연산자](../standard-library/thread-operators.md#op_gt)|하나의 `thread::id` 개체가 다른 개체보다 큰지를 확인합니다.|
|[operator < = 연산자](../standard-library/thread-operators.md#op_lt_eq)|하나의 `thread::id` 개체가 다른 개체보다 작거나 같은지를 확인합니다.|
|[operator < 연산자](../standard-library/thread-operators.md#op_lt)|하나의 `thread::id` 개체가 다른 개체보다 작은지를 확인합니다.|
|[operator! = 연산자](../standard-library/thread-operators.md#op_neq)|두 `thread::id` 개체가 다른지 비교합니다.|
|[operator = = 연산자](../standard-library/thread-operators.md#op_eq_eq)|두 `thread::id` 개체가 같은지 비교합니다.|
|[연산자 < < 연산자](../standard-library/thread-operators.md#op_lt_lt)|`thread::id` 개체의 텍스트 표현을 스트림에 삽입합니다.|

## <a name="see-also"></a>참고자료

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)

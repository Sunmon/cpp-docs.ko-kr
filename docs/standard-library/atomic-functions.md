﻿---
title: '&lt;atomic&gt; 함수'
ms.date: 07/11/2018
f1_keywords:
- atomic/std::atomic_compare_exchange_strong
- atomic/std::atomic_compare_exchange_strong_explicit
- atomic/std::atomic_compare_exchange_weak
- atomic/std::atomic_compare_exchange_weak_explicit
- atomic/std::atomic_exchange
- atomic/std::atomic_exchange_explicit
- atomic/std::atomic_fetch_add
- atomic/std::atomic_fetch_add_explicit
- atomic/std::atomic_fetch_and
- atomic/std::atomic_fetch_and_explicit
- atomic/std::atomic_fetch_or
- atomic/std::atomic_fetch_or_explicit
- atomic/std::atomic_fetch_sub
- atomic/std::atomic_fetch_sub_explicit
- atomic/std::atomic_fetch_xor
- atomic/std::atomic_fetch_xor_explicit
- atomic/std::atomic_flag_clear
- atomic/std::atomic_flag_clear_explicit
- atomic/std::atomic_flag_test_and_set
- atomic/std::atomic_flag_test_and_set_explicit
- atomic/std::atomic_init
- atomic/std::atomic_is_lock_free
- atomic/std::atomic_load
- atomic/std::atomic_load_explicit
- atomic/std::atomic_signal_fence
- atomic/std::atomic_store
- atomic/std::atomic_store_explicit
- atomic/std::atomic_thread_fence
- atomic/std::kill_dependency
ms.assetid: 5c53b4f8-6ff5-47d7-beb2-2d6ee3c6ea89
helpviewer_keywords:
- std::atomic_compare_exchange_strong [C++]
- std::atomic_compare_exchange_strong_explicit [C++]
- std::atomic_compare_exchange_weak [C++]
- std::atomic_compare_exchange_weak_explicit [C++]
- std::atomic_exchange [C++]
- std::atomic_exchange_explicit [C++]
- std::atomic_fetch_add [C++]
- std::atomic_fetch_add_explicit [C++]
- std::atomic_fetch_and [C++]
- std::atomic_fetch_and_explicit [C++]
- std::atomic_fetch_or [C++]
- std::atomic_fetch_or_explicit [C++]
- std::atomic_fetch_sub [C++]
- std::atomic_fetch_sub_explicit [C++]
- std::atomic_fetch_xor [C++]
- std::atomic_fetch_xor_explicit [C++]
- std::atomic_flag_clear [C++]
- std::atomic_flag_clear_explicit [C++]
- std::atomic_flag_test_and_set [C++]
- std::atomic_flag_test_and_set_explicit [C++]
- std::atomic_init [C++]
- std::atomic_is_lock_free [C++]
- std::atomic_load [C++]
- std::atomic_load_explicit [C++]
- std::atomic_signal_fence [C++]
- std::atomic_store [C++]
- std::atomic_store_explicit [C++]
- std::atomic_thread_fence [C++]
- std::kill_dependency [C++]
ms.openlocfilehash: b6d03da446e4a3bae02f662e5b106bd5de534d0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376893"
---
# <a name="ltatomicgt-functions"></a>&lt;atomic&gt; 함수

||||
|-|-|-|
|[atomic_compare_exchange_strong](#atomic_compare_exchange_strong)|[atomic_compare_exchange_strong_explicit](#atomic_compare_exchange_strong_explicit)|[atomic_compare_exchange_weak](#atomic_compare_exchange_weak)|
|[atomic_compare_exchange_weak_explicit](#atomic_compare_exchange_weak_explicit)|[atomic_exchange](#atomic_exchange)|[atomic_exchange_explicit](#atomic_exchange_explicit)|
|[atomic_fetch_add](#atomic_fetch_add)|[atomic_fetch_add_explicit](#atomic_fetch_add_explicit)|[atomic_fetch_and](#atomic_fetch_and)|
|[atomic_fetch_and_explicit](#atomic_fetch_and_explicit)|[atomic_fetch_or](#atomic_fetch_or)|[atomic_fetch_or_explicit](#atomic_fetch_or_explicit)|
|[atomic_fetch_sub](#atomic_fetch_sub)|[atomic_fetch_sub_explicit](#atomic_fetch_sub_explicit)|[atomic_fetch_xor](#atomic_fetch_xor)|
|[atomic_fetch_xor_explicit](#atomic_fetch_xor_explicit)|[atomic_flag_clear](#atomic_flag_clear)|[atomic_flag_clear_explicit](#atomic_flag_clear_explicit)|
|[atomic_flag_test_and_set](#atomic_flag_test_and_set)|[atomic_flag_test_and_set_explicit](#atomic_flag_test_and_set_explicit)|[atomic_init](#atomic_init)|
|[atomic_is_lock_free](#atomic_is_lock_free)|[atomic_load](#atomic_load)|[atomic_load_explicit](#atomic_load_explicit)|
|[atomic_signal_fence](#atomic_signal_fence)|[atomic_store](#atomic_store)|[atomic_store_explicit](#atomic_store_explicit)|
|[atomic_thread_fence](#atomic_thread_fence)|[kill_dependency](#kill_dependency)|

## <a name="atomic_compare_exchange_strong"></a><a name="atomic_compare_exchange_strong"></a>atomic_compare_exchange_strong

원자 비교 및 교환 작업을 수행합니다.

```cpp
template <class Ty>
inline bool atomic_compare_exchange_strong(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Value) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;
```

### <a name="parameters"></a>매개 변수

*원자*\
형식 `Ty`값을 저장하는 *원자성* 개체에 대한 포인터입니다.

*특급*\
`Ty` 형식의 값에 대한 포인터입니다.

*값*\
`Ty` 형식의 값입니다.

### <a name="return-value"></a>Return Value

**true** 값이 같으면 **false입니다.**

### <a name="remarks"></a>설명

이 메서드는 암시적 `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) 인수를 사용하여 원자 비교 및 교환 작업을 수행합니다. 자세한 내용은 [atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit)를 참조하세요.

## <a name="atomic_compare_exchange_strong_explicit"></a><a name="atomic_compare_exchange_strong_explicit"></a>atomic_compare_exchange_strong_explicit

*원자 비교 및 교환* 작업을 수행합니다.

```cpp
template <class T>
inline bool atomic_compare_exchange_strong_explicit(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong_explicit(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;
```

### <a name="parameters"></a>매개 변수

*원자*\
`Ty` 형식의 값을 저장하는 `atomic` 개체에 대한 포인터입니다.

*특급*\
`Ty` 형식의 값에 대한 포인터입니다.

*값*\
`Ty` 형식의 값입니다.

*주문 1*\
첫 번째 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 인수입니다.

*주문 2*\
두 번째 `memory_order` 인수입니다. *Order2의* `memory_order_release` 값은 `memory_order_acq_rel` *Order1*의 값보다 더 강할 수 없거나 .

### <a name="return-value"></a>Return Value

**true** 값이 같으면 **false입니다.**

### <a name="remarks"></a>설명

*원자 성 비교 및 교환 작업은* *Atom이* 가리키는 개체에 저장된 값을 *Exp에서*가리키는 값과 비교합니다. 값이 같으면 *원자로* 가리키는 개체에 저장된 값은 `read-modify-write` 작업을 사용하고 *Order1에*의해 지정된 메모리 순서 제약 조건을 적용하여 *값으로* 대체됩니다. 값이 같지 않으면 연산은 *Atom*이 가리키는 개체에 저장된 값으로 *Exp*가 가리키는 값을 바꾸고 *Order2*에 지정된 메모리 순서 제약 조건을 적용합니다.

## <a name="atomic_compare_exchange_weak"></a><a name="atomic_compare_exchange_weak"></a>atomic_compare_exchange_weak

*약한 원자 비교 및 교환* 작업을 수행합니다.

```cpp
template <class Ty>
inline bool atomic_compare_exchange_strong(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;
```

### <a name="parameters"></a>매개 변수

*원자*\
`Ty` 형식의 값을 저장하는 `atomic` 개체에 대한 포인터입니다.

*특급*\
`Ty` 형식의 값에 대한 포인터입니다.

*값*\
`Ty` 형식의 값입니다.

### <a name="return-value"></a>Return Value

**true** 값이 같으면 **false입니다.**

### <a name="remarks"></a>설명

이 메서드는 암시적 `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) 인수를 갖는 *약한 원자 비교 및 교환 작업*을 수행합니다. 자세한 내용은 [atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit)를 참조하세요.

## <a name="atomic_compare_exchange_weak_explicit"></a><a name="atomic_compare_exchange_weak_explicit"></a>atomic_compare_exchange_weak_explicit

*약한 원자 비교 및 교환* 작업을 수행합니다.

```cpp
template <class Ty>
inline bool atomic_compare_exchange_weak_explicit(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_weak_explicit(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;
```

### <a name="parameters"></a>매개 변수

*원자*\
`Ty` 형식의 값을 저장하는 `atomic` 개체에 대한 포인터입니다.

*특급*\
`Ty` 형식의 값에 대한 포인터입니다.

*값*\
`Ty` 형식의 값입니다.

*주문 1*\
첫 번째 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 인수입니다.

*주문 2*\
두 번째 `memory_order` 인수입니다. *Order2의* `memory_order_release` `memory_order_acq_rel`값은 *Order1의*값보다 강할 수도 있고 더 강할 수도 없습니다.

### <a name="return-value"></a>Return Value

**true** 값이 같으면 **false입니다.**

### <a name="remarks"></a>설명

*원자 비교 및 교환 작업의* 강하고 약한 맛은 예상 값과 현재 값이 같지 않은 경우 새 값을 저장하지 않는다는 것을 보장합니다. 강한 풍미는 예상 값과 현재 값이 같으면 새 값을 저장합니다. 약한 맛은 때때로 **false를** 반환하고 현재 및 예상 값이 같더라도 새 값을 저장하지 않을 수 있습니다. 즉, 함수는 **false를**반환하지만 나중에 예상 값을 검사하면 변경되지 않았음을 알 수 있으므로 동일하게 비교해야 합니다.

## <a name="atomic_exchange"></a><a name="atomic_exchange"></a>atomic_exchange

*값을* 사용하여 *Atom*의 저장된 값을 대체합니다.

```cpp
template <class T>
inline Ty atomic_exchange(volatile atomic<Ty>* _Atom, Ty Value) noexcept;

template <class Ty>
inline T atomic_exchange(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>매개 변수

*원자*\
`Ty` 형식의 값을 저장하는 `atomic` 개체에 대한 포인터입니다.

*값*\
`Ty` 형식의 값입니다.

### <a name="return-value"></a>Return Value

교환 전에 *아톰의* 저장된 값입니다.

### <a name="remarks"></a>설명

이 `atomic_exchange` 함수는 `read-modify-write` `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)사용하여 *Atom에* 저장된 값을 *Value로*교환하는 작업을 수행합니다.

## <a name="atomic_exchange_explicit"></a><a name="atomic_exchange_explicit"></a>atomic_exchange_explicit

*Atom의* 저장된 값을 *값으로*바꿉꿉입니다.

```cpp
template <class Ty>
inline Ty atomic_exchange_explicit(
    volatile atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;

template <class Ty>
inline Ty atomic_exchange_explicit(
    atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>매개 변수

*원자*\
`Ty` 형식의 값을 저장하는 `atomic` 개체에 대한 포인터입니다.

*값*\
`Ty` 형식의 값입니다.

*순서*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Return Value

교환 전에 *아톰의* 저장된 값입니다.

### <a name="remarks"></a>설명

함수 `atomic_exchange_explicit`는 *Order*로 지정된 메모리 제약 조건 내에서 *Atom*에 저장된 값을 *Value*로 교환하는 `read-modify-write` 연산을 수행합니다.

## <a name="atomic_fetch_add"></a><a name="atomic_fetch_add"></a>atomic_fetch_add

값을 `atomic` 개체에 저장된 기존의 값에 더합니다.

```cpp
template <class T>
T* atomic_fetch_add(volatile atomic<T*>* Atom, ptrdiff_t Value) noexcept;
template <class T>
T* atomic_fetch_add(atomic<T*>* Atom, ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>매개 변수

*원자*\
`T` 형식에 대한 포인터를 저장하는 `atomic` 개체에 대한 포인터입니다.

*값*\
`ptrdiff_t` 형식의 값입니다.

### <a name="return-value"></a>Return Value

연산을 수행하기 직전 원자성 개체에 포함된 포인터의 값입니다.

### <a name="remarks"></a>설명

함수 `atomic_fetch_add`는 `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) 제약 조건을 사용하여 *Atom*의 저장된 값에 *Value*를 원자 단위로 추가하는 `read-modify-write` 연산을 수행합니다.

원자성 형식이 `atomic_address`이면 *Value*의 형식은 `ptrdiff_t`이고 작업에서는 저장된 포인터를 `char *`로 처리합니다.

이 연산은 또한 정수 형식에 대해 오버로드됩니다.

```cpp
integral atomic_fetch_add(volatile atomic-integral* Atom, integral Value) noexcept;

integral atomic_fetch_add(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_add_explicit"></a><a name="atomic_fetch_add_explicit"></a>atomic_fetch_add_explicit

값을 `atomic` 개체에 저장된 기존의 값에 더합니다.

```cpp
template <class T>
T* atomic_fetch_add_explicit(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;

template <class T>
T* atomic_fetch_add_explicit(
    atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>매개 변수

*원자*\
`T` 형식에 대한 포인터를 저장하는 `atomic` 개체에 대한 포인터입니다.

*값*\
`ptrdiff_t` 형식의 값입니다.

### <a name="return-value"></a>Return Value

연산을 수행하기 직전 원자성 개체에 포함된 포인터의 값입니다.

### <a name="remarks"></a>설명

`atomic_fetch_add_explicit` 함수는 `read-modify-write` 작업을 수행하여 `Order`에 지정된 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 제약 조건 내에서 *Atom*의 저장된 값에 *Value*를 원자 단위로 더합니다.

원자성 형식이 `atomic_address`인 경우, `Value`의 형식은 `ptrdiff_t`이고 연산은 저장된 포인터를 `char *`로 취급합니다.

이 연산은 또한 정수 형식에 대해 오버로드됩니다.

```cpp
integral atomic_fetch_add_explicit(
    volatile atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;

integral atomic_fetch_add_explicit(
    atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;
```

## <a name="atomic_fetch_and"></a><a name="atomic_fetch_and"></a>atomic_fetch_and

`atomic` 개체에 저장된 기존 값 및 특정 값에 대해 비트 `and`를 수행합니다.

```cpp
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>매개 변수

*원자*\
`T` 형식의 값을 저장하는 `atomic` 개체에 대한 포인터입니다.

*값*\
`T` 형식의 값입니다.

### <a name="return-value"></a>Return Value

연산을 수행하기 직전 원자성 개체에 포함된 값입니다.

### <a name="remarks"></a>설명

`atomic_fetch_and` 함수 `read-modify-write` 연산을 수행하여 *atom*의 저장된 값을 비트 값 `and`의 비트 *값*과 *atom*에 저장된 현재 값으로 바꾸기 위해 [memory_order](../standard-library/atomic-enums.md#memory_order_enum)를 `memory_order_seq_cst`사용합니다.

## <a name="atomic_fetch_and_explicit"></a><a name="atomic_fetch_and_explicit"></a>atomic_fetch_and_explicit

`atomic` 개체에 저장된 기존 값 및 특정 값의 비트 `and`를 수행합니다.

```cpp
template <class T>
inline T atomic_fetch_and_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_and_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>매개 변수

*원자*\
`T` 형식의 값을 저장하는 `atomic` 개체에 대한 포인터입니다.

*값*\
`T` 형식의 값입니다.

*순서*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Return Value

연산을 수행하기 직전 원자성 개체에 포함된 값입니다.

### <a name="remarks"></a>설명

함수 `atomic_fetch_and_explicit`는 *Order*에서 지정한 `read-modify-write` 메모리 제약 조건 내에서 *Atom*의 저장된 값을 *Value* 및 *Atom*에 저장된 현재 값의 비트 `and`로 바꾸는 작업을 수행합니다.

## <a name="atomic_fetch_or"></a><a name="atomic_fetch_or"></a>atomic_fetch_or

`atomic` 개체에 저장된 기존 값 및 특정 값에 대해 비트 `or`를 수행합니다.

```cpp
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>매개 변수

*원자*\
`T` 형식의 값을 저장하는 `atomic` 개체에 대한 포인터입니다.

*값*\
`T` 형식의 값입니다.

### <a name="return-value"></a>Return Value

연산을 수행하기 직전 원자성 개체에 포함된 값입니다.

### <a name="remarks"></a>설명

함수 `atomic_fetch_or` 는 `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum)를 사용하여 *atom*의 저장된 값 `or`을 비트 *값*의 비트 값과 *atom*에 저장된 현재 값으로 바꾸기 위해 `read-modify-write` 연산을 수행합니다.

## <a name="atomic_fetch_or_explicit"></a><a name="atomic_fetch_or_explicit"></a>atomic_fetch_or_explicit

`atomic` 개체에 저장된 기존 값 및 특정 값에 대해 비트 `or`를 수행합니다.

```cpp
template <class T>
inline T atomic_fetch_or_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_or_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>매개 변수

*원자*\
`T` 형식의 값을 저장하는 `atomic` 개체에 대한 포인터입니다.

*값*\
`T` 형식의 값입니다.

*순서*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Return Value

연산을 수행하기 직전 원자성 개체에 포함된 값입니다.

### <a name="remarks"></a>설명

함수 `atomic_fetch_or_explicit` 는 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 제약 `read-modify-write` 조건 내에서 atom의 저장된 값 `or` 을 비트 *값* 및 *atom*에 저장된 현재 *값으로 바꾸기* 위해 연산을 수행 합니다. *순서*에 따라 지정 됩니다.

## <a name="atomic_fetch_sub"></a><a name="atomic_fetch_sub"></a>atomic_fetch_sub

값을 `atomic` 개체에 저장된 기존의 값에서 뺍니다.

```cpp
template <class T>
T* atomic_fetch_sub(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value) noexcept;

template <class T>
T* atomic_fetch_sub(
    atomic<T*>* Atom,
    ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>매개 변수

*원자*\
`T` 형식에 대한 포인터를 저장하는 `atomic` 개체에 대한 포인터입니다.

*값*\
`ptrdiff_t` 형식의 값입니다.

### <a name="return-value"></a>Return Value

연산을 수행하기 직전 원자성 개체에 포함된 포인터의 값입니다.

### <a name="remarks"></a>설명

함수 `atomic_fetch_sub`는 `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) 제약 조건을 사용하여 *Atom*의 저장된 값에서 자동으로 *Value*를 빼는 `read-modify-write` 작업을 수행합니다.

원자성 형식이 `atomic_address`이면 *Value*의 형식은 `ptrdiff_t`이고 작업에서는 저장된 포인터를 `char *`로 처리합니다.

이 연산은 또한 정수 형식에 대해 오버로드됩니다.

```cpp
integral atomic_fetch_sub(volatile atomic-integral* Atom, integral Value) noexcept;
integral atomic_fetch_sub(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_sub_explicit"></a><a name="atomic_fetch_sub_explicit"></a>atomic_fetch_sub_explicit

값을 `atomic` 개체에 저장된 기존의 값에서 뺍니다.

```cpp
template <class T>
T* atomic_fetch_sub_explicit(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;

template <class T>
T* atomic_fetch_sub_explicit(
    atomic<T*>* Atom,
    ptrdiff_t Value, memory_order Order) noexcept;
```

### <a name="parameters"></a>매개 변수

*원자*\
`T` 형식에 대한 포인터를 저장하는 `atomic` 개체에 대한 포인터입니다.

*값*\
`ptrdiff_t` 형식의 값입니다.

### <a name="return-value"></a>Return Value

연산을 수행하기 직전 원자성 개체에 포함된 포인터의 값입니다.

### <a name="remarks"></a>설명

함수 `atomic_fetch_sub_explicit`는 `Order`로 지정된 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 제약 조건 내에서 *Atom*의 저장된 값에서 *Value*를 원자 단위로 빼서 `read-modify-write` 연산을 수행합니다.

원자성 형식이 `atomic_address`이면 *Value*의 형식은 `ptrdiff_t`이고 작업에서는 저장된 포인터를 `char *`로 처리합니다.

이 연산은 또한 정수 형식에 대해 오버로드됩니다.

```cpp
integral atomic_fetch_sub_explicit(
    volatile atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;

integral atomic_fetch_sub_explicit(
    atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;
```

## <a name="atomic_fetch_xor"></a><a name="atomic_fetch_xor"></a>atomic_fetch_xor

`atomic` 개체에 저장된 기존 값 및 특정 값에 대해 비트 `exclusive or`를 수행합니다.

```cpp
template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;

template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>매개 변수

*원자*\
`T` 형식의 값을 저장하는 `atomic` 개체에 대한 포인터입니다.

*값*\
`T` 형식의 값입니다.

### <a name="return-value"></a>Return Value

연산을 수행하기 직전 원자성 개체에 포함된 값입니다.

### <a name="remarks"></a>설명

함수 `atomic_fetch_xor` 는 `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum)를 사용하여 *atom*의 저장된 값 `exclusive or`을 비트 *값*의 비트 값과 *atom*에 저장된 현재 값으로 바꾸기 위해 `read-modify-write` 연산을 수행합니다.

## <a name="atomic_fetch_xor_explicit"></a><a name="atomic_fetch_xor_explicit"></a>atomic_fetch_xor_explicit

`atomic` 개체에 저장된 기존 값 및 특정 값에 대해 비트 `exclusive or`를 수행합니다.

```cpp
template <class T>
inline T atomic_fetch_xor_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_xor_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>매개 변수

*원자*\
`T` 형식의 값을 저장하는 `atomic` 개체에 대한 포인터입니다.

*값*\
`T` 형식의 값입니다.

*순서*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Return Value

연산을 수행하기 직전 원자성 개체에 포함된 값입니다.

### <a name="remarks"></a>설명

함수 `atomic_fetch_xor_explicit`는 *Order*로 지정된 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 제약 조건을 사용하여 *Atom*의 저장된 값을 *Atom*에 저장된 현재 값과 *Value*의 비트 `exclusive or`로 바꾸는 `read-modify-write` 작업을 수행합니다.

## <a name="atomic_flag_clear"></a><a name="atomic_flag_clear"></a>atomic_flag_clear

[atomic_flag](../standard-library/atomic-flag-structure.md) 개체의 **bool** 플래그를 memory_order **false로**설정합니다. `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)

```cpp
inline void atomic_flag_clear(volatile atomic_flag* Flag) noexcept;
inline void atomic_flag_clear(atomic_flag* Flag) noexcept;
```

### <a name="parameters"></a>매개 변수

*플래그*\
`atomic_flag` 개체에 대한 포인터입니다.

## <a name="atomic_flag_clear_explicit"></a><a name="atomic_flag_clear_explicit"></a>atomic_flag_clear_explicit

지정된 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 제약 조건 내에서 [atomic_flag](../standard-library/atomic-flag-structure.md) 개체의 **bool** 플래그를 **false로**설정합니다.

```cpp
inline void atomic_flag_clear_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline void atomic_flag_clear_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>매개 변수

*플래그*\
`atomic_flag` 개체에 대한 포인터입니다.

*순서*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_flag_test_and_set"></a><a name="atomic_flag_test_and_set"></a>atomic_flag_test_and_set

memory_order 제약 조건 내에서 [atomic_flag](../standard-library/atomic-flag-structure.md) 개체에서 **bool** 플래그를 `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) **true로**설정합니다.

```cpp
inline bool atomic_flag_test_and_set(volatile atomic_flag* Flag,) noexcept;
inline bool atomic_flag_test_and_set(atomic_flag* Flag,) noexcept;
```

### <a name="parameters"></a>매개 변수

*플래그*\
`atomic_flag` 개체에 대한 포인터입니다.

### <a name="return-value"></a>Return Value

*플래그*의 초기 값입니다.

## <a name="atomic_flag_test_and_set_explicit"></a><a name="atomic_flag_test_and_set_explicit"></a>atomic_flag_test_and_set_explicit

지정된 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 제약 조건 내에서 [atomic_flag](../standard-library/atomic-flag-structure.md) 개체의 **bool** 플래그를 **true로**설정합니다.

```cpp
inline bool atomic_flag_test_and_set_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline bool atomic_flag_test_and_set_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>매개 변수

*플래그*\
`atomic_flag` 개체에 대한 포인터입니다.

*순서*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Return Value

*플래그*의 초기 값입니다.

## <a name="atomic_init"></a><a name="atomic_init"></a>atomic_init

`atomic` 개체에서 저장된 값을 설정합니다.

```cpp
template <class Ty>
inline void atomic_init(volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline void atomic_init(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>매개 변수

*원자*\
`Ty` 형식의 값을 저장하는 `atomic` 개체에 대한 포인터입니다.

*값*\
`Ty` 형식의 값입니다.

### <a name="remarks"></a>설명

`atomic_init`는 원자 연산이 아닙니다. 스레드로부터 안전하지 않습니다.

## <a name="atomic_is_lock_free"></a><a name="atomic_is_lock_free"></a>atomic_is_lock_free

`atomic` 개체의 원자 연산이 *잠금 해제*인지를 지정합니다.

```cpp
template <class T>
inline bool atomic_is_lock_free(const volatile atomic<T>* Atom) noexcept;
template <class T>
inline bool atomic_is_lock_free(const atomic<T>* Atom) noexcept;
```

### <a name="parameters"></a>매개 변수

*원자*\
`T` 형식의 값을 저장하는 `atomic` 개체에 대한 포인터입니다.

### <a name="return-value"></a>Return Value

*Atom*의 원자성 작업이 잠금 해제이면 **true**이고, 그렇지 않으면 **false**입니다.

### <a name="remarks"></a>설명

하나의 원자 형식에 대해 어떠한 원자 작업도 잠금을 사용하지 않는 경우, 해당 원자 형식은 잠금 없음이라고 합니다. 이 함수가 true를 반환하는 경우 신호 처리기에서 형식을 안전하게 사용할 수 있습니다.

## <a name="atomic_load"></a><a name="atomic_load"></a>atomic_load

`atomic` 개체에서 저장된 값을 검색합니다.

```cpp
template <class Ty>
inline Ty atomic_load(const volatile atomic<Ty>* Atom) noexcept;
template <class Ty>
inline Ty atomic_load(const atomic<Ty>* Atom) noexcept;
```

### <a name="parameters"></a>매개 변수

*원자*\
`Ty` 형식의 값을 포함하는 `atomic` 개체에 대한 포인터입니다.

### <a name="return-value"></a>Return Value

*Atom*에 저장된 검색된 값입니다.

### <a name="remarks"></a>설명

`atomic_load`는 `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum)를 암시적으로 사용합니다.

## <a name="atomic_load_explicit"></a><a name="atomic_load_explicit"></a>atomic_load_explicit

지정한 [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 내에서 `atomic` 개체에 저장된 값을 검색합니다.

```cpp
template <class Ty>
inline Ty atomic_load_explicit(const volatile atomic<Ty>* Atom, memory_order Order) noexcept;
template <class Ty>
inline Ty atomic_load_explicit(const atomic<Ty>* Atom, memory_order Order) noexcept;
```

### <a name="parameters"></a>매개 변수

*원자*\
`Ty` 형식의 값을 포함하는 `atomic` 개체에 대한 포인터입니다.

*순서*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum). `memory_order_release` 또는 `memory_order_acq_rel`을 사용하지 마세요.

### <a name="return-value"></a>Return Value

*Atom*에 저장된 검색된 값입니다.

## <a name="atomic_signal_fence"></a><a name="atomic_signal_fence"></a>atomic_signal_fence

동일한 스레드에서 실행되는 신호 처리기가 있는 호출 스레드에서 다른 fence 간, 로드/저장 작업 간에 순서를 적용하는 메모리 동기화 기본 형식인 *fence* 역할을 수행합니다.

```cpp
inline void atomic_signal_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>매개 변수

*순서*\
fence 형식을 결정하는 메모리 순서 제약 조건입니다.

### <a name="remarks"></a>설명

*Order* 인수는 울타리 유형을 결정합니다.

|||
|-|-|
|`memory_order_relaxed`|fence가 효과가 없습니다.|
|`memory_order_consume`|fence가 acquire fence입니다.|
|`memory_order_acquire`|fence가 acquire fence입니다.|
|`memory_order_release`|fence가 release fence입니다.|
|`memory_order_acq_rel`|fence가 acquire fence이면서 동시에 release fence입니다.|
|`memory_order_seq_cst`|fence가 acquire fence이면서 동시에 release fence이고, 일관된 순서로 되어 있습니다.|

## <a name="atomic_store"></a><a name="atomic_store"></a>atomic_store

값을 원자 단위로 원자 개체에 저장합니다.

```cpp
template <class Ty>
inline Ty atomic_store_explicit(const volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline Ty atomic_store_explicit(const atomic<Ty>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>매개 변수

*원자*\
`Ty` 형식의 값을 포함하는 원자 개체에 대한 포인터입니다.

*값*\
`Ty` 형식의 값입니다.

### <a name="remarks"></a>설명

`atomic_store`memory_order `memory_order_seq_cst` [제약](../standard-library/atomic-enums.md#memory_order_enum) 조건 내에서 *Atom이*가리키는 개체에 *값을* 저장합니다.

## <a name="atomic_store_explicit"></a><a name="atomic_store_explicit"></a>atomic_store_explicit

값을 원자 단위로 원자 개체에 저장합니다.

```cpp
template <class Ty>
inline Ty atomic_store_explicit(
    const volatile atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;

template <class Ty>
inline Ty atomic_store_explicit(
    const atomic<Ty>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>매개 변수

*원자*\
`Ty` 형식의 값을 포함하는 `atomic` 개체에 대한 포인터입니다.

*값*\
`Ty` 형식의 값입니다.

*순서*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum). `memory_order_consume`, `memory_order_acquire` 또는 `memory_order_acq_rel`을 사용하지 마세요.

### <a name="remarks"></a>설명

`atomic_store`*Atom이*가리키는 개체에 *Order에* 지정된 값 `memory_order` 에 값을 *Order*저장합니다.

## <a name="atomic_thread_fence"></a><a name="atomic_thread_fence"></a>atomic_thread_fence

연결된 원자 연산 없이 로드/저장 작업 간에 순서를 적용하는 메모리 동기화 기본 형식인 *fence* 역할을 수행합니다.

```cpp
inline void atomic_thread_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>매개 변수

*순서*\
fence 형식을 결정하는 메모리 순서 제약 조건입니다.

### <a name="remarks"></a>설명

*Order* 인수는 울타리 유형을 결정합니다.

|||
|-|-|
|`memory_order_relaxed`|fence가 효과가 없습니다.|
|`memory_order_consume`|fence가 acquire fence입니다.|
|`memory_order_acquire`|fence가 acquire fence입니다.|
|`memory_order_release`|fence가 release fence입니다.|
|`memory_order_acq_rel`|fence가 acquire fence이면서 동시에 release fence입니다.|
|`memory_order_seq_cst`|fence가 acquire fence이면서 동시에 release fence이고, 일관된 순서로 되어 있습니다.|

## <a name="kill_dependency"></a><a name="kill_dependency"></a>kill_dependency

종속성을 제거합니다.

```cpp
template <class Ty>
Ty kill_dependency(Ty Arg) noexcept;
```

### <a name="parameters"></a>매개 변수

*Arg*\
`Ty` 형식의 값입니다.

### <a name="return-value"></a>Return Value

반환 값은 *Arg입니다.* *Arg의* 평가는 함수 호출에 대한 종속성을 전달하지 않습니다. 가능한 종속성 체인을 중단하면 함수는 컴파일러가 좀 더 효율적인 코드를 생성하도록 허용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[\<원자>](../standard-library/atomic.md)

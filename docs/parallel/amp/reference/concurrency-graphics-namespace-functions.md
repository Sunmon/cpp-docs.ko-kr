---
title: Concurrency::graphics 네임스페이스 함수
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::fast_math::copy_async
- amp_graphics/Concurrency::fast_math::copy
ms.assetid: ace01cd5-29d3-4356-930e-c81a61c5f934
ms.openlocfilehash: 776f715f72d2e3b6b3841856323a52953e9c5344
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376335"
---
# <a name="concurrencygraphics-namespace-functions"></a>Concurrency::graphics 네임스페이스 함수

|||
|-|-|
|[copy](#copy)|[copy_async](#copy_async)|

## <a name="copy-function-concurrencygraphics-namespace"></a><a name="copy"></a>복사 함수(동시성::그래픽 네임스페이스)

소스 텍스처를 대상 버퍼에 복사하거나 소스 버퍼를 대상 버퍼에 복사합니다. 이 함수의 일반적인 `copy(src, dest)`형태는 .

```cpp
template <
    typename _Src_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture, void>::type>
>
void copy (
    const _Src_type& _Src,
    _Out_ void* _Dst,
    unsigned int _Dst_byte_size);

template <
    typename _Src_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture, void>::type
>
void copy(
    const _Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset,
    const extent<_Src_type::rank>& _Copy_extent,
    _Out_ void* _Dst,
    unsigned int _Dst_byte_size);

template <
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
void copy(
    const void* _Src,
    unsigned int _Src_byte_size, _Dst_type& _Dst);

template <
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
void copy(
    const void* _Src,
    unsigned int _Src_byte_size,
    _Dst_type& _Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Dst_type::rank>& _Copy_extent);

template <
    typename InputIterator,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
void copy(InputIterator first, InputIterator last, _Dst_type& _Dst);

template <
    typename InputIterator,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>void copy(InputIterator first, InputIterator last, _Dst_type& _Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Dst_type::rank>& _Copy_extent);

template <
    typename _Src_type,
    typename OutputIterator,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& !details::texture_traits<OutputIterator>::is_texture, void>::type
>
void copy(
    const _Src_type& _Src, OutputIterator _Dst);

template <
    typename _Src_type,
    typename OutputIterator,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& !details::texture_traits<OutputIterator>::is_texture, void>::type
>
void copy (
    const _Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset,
    const extent<_Src_type::rank>& _Copy_extent, OutputIterator _Dst);

template <
    typename _Src_type,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& details::texture_traits<_Dst_type>::is_texture, void>::type
>
void copy (
    const _Src_type& _Src, _Dst_type& _Dst);

template <
    typename _Src_type,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& details::texture_traits<_Dst_type>::is_texture,
    void>::type
>
void copy (
    const _Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset, _Dst_type& _Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Src_type::rank>& _Copy_extent);
```

### <a name="parameters"></a>매개 변수

*_Copy_extent*<br/>
복사할 텍스처 섹션의 범위입니다.

*_Dst*<br/>
복사할 개체입니다.

*_Dst_byte_size*<br/>
대상의 바이트 수입니다.

*_Dst_type*<br/>
대상 개체의 형식입니다.

*_Dst_offset*<br/>
복사를 시작할 대상에 대한 오프셋입니다.

*InputIterator*<br/>
입력 반복기의 형식입니다.

*출력이터*<br/>
출력 거터레이터의 유형입니다.

*_Src*<br/>
복사할 것을 반대합니다.

*_Src_byte_size*<br/>
소스의 바이트 수입니다.

*_Src_type*<br/>
소스 개체의 형식입니다.

*_Src_offset*<br/>
복사를 시작할 소스로 오프셋합니다.

*첫 번째*<br/>
소스 컨테이너에 대한 시작 이터레이터입니다.

*마지막*<br/>
소스 컨테이너에 대한 끝 이터레이터입니다.

## <a name="copy_async-function-concurrencygraphics-namespace"></a><a name="copy_async"></a>copy_async 함수(동시성::그래픽 네임스페이스)

비동기적으로 소스 텍스처를 대상 버퍼에 복사하거나 소스 버퍼를 대상 버퍼에 복사한 다음 기다릴 수 있는 [completion_future](completion-future-class.md) 개체를 반환합니다. 가속기에서 코드가 실행중일 때는 데이터를 복사할 수 없습니다. 이 함수의 일반적인 `copy(src, dest)`형태는 .

```cpp
template<
    typename _Src_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(
    const _Src_type& _Src,
    _Out_ void* _Dst,
    unsigned int _Dst_byte_size);

template<
    typename _Src_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(
    const _Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset,
    const extent<_Src_type::rank>& _Copy_extent,
    _Out_ void* _Dst,
    unsigned int _Dst_byte_size);

template <
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(
    const void* _Src,
    unsigned int _Src_byte_size, _Dst_type& _Dst);

template <
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(
    const void* _Src,
    unsigned int _Src_byte_size, _Dst_type& _Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Dst_type::rank>& _Copy_extent);

template <
    typename InputIterator,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(InputIterator first, InputIterator last, _Dst_type& _Dst);

template <
    typename InputIterator,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(InputIterator first, InputIterator last, _Dst_type& _Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Dst_type::rank>& _Copy_extent);

template <
    typename _Src_type,
    typename OutputIterator,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& !details::texture_traits<OutputIterator>::is_texture, void>::type
>
concurrency::completion_future copy_async(_Src_type& _Src, OutputIterator _Dst);

template <
    typename _Src_type,
    typename OutputIterator,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& !details::texture_traits<OutputIterator>::is_texture, void>::type
>
concurrency::completion_future copy_async(_Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset,
    const extent<_Src_type::rank>& _Copy_extent,
    OutputIterator _Dst);

template <
    typename _Src_type,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(_Src_type& _Src, _Dst_type& _Dst);

template <
    typename _Src_type,
    typename _Dst_type,
    typename = typename std::enable_if<details::texture_traits<_Src_type>::is_texture&& details::texture_traits<_Dst_type>::is_texture, void>::type
>
concurrency::completion_future copy_async(_Src_type& _Src,
    const index<_Src_type::rank>& _Src_offset, _Dst_type &_Dst,
    const index<_Dst_type::rank>& _Dst_offset,
    const extent<_Src_type::rank>& _Copy_extent);
```

### <a name="parameters"></a>매개 변수

*_Copy_extent*<br/>
복사할 텍스처 섹션의 범위입니다.

*_Dst*<br/>
복사할 개체입니다.

*_Dst_byte_size*<br/>
대상의 바이트 수입니다.

*_Dst_type*<br/>
대상 개체의 형식입니다.

*_Dst_offset*<br/>
복사를 시작할 대상에 대한 오프셋입니다.

*InputIterator*<br/>
입력 반복기의 형식입니다.

*출력이터*<br/>
출력 거터레이터의 유형입니다.

*_Src*<br/>
복사할 것을 반대합니다.

*_Src_byte_size*<br/>
소스의 바이트 수입니다.

*_Src_type*<br/>
소스 개체의 형식입니다.

*_Src_offset*<br/>
복사를 시작할 소스로 오프셋합니다.

*첫 번째*<br/>
소스 컨테이너에 대한 시작 이터레이터입니다.

*마지막*<br/>
소스 컨테이너에 대한 끝 이터레이터입니다.

## <a name="requirements"></a>요구 사항

**헤더:** amp_graphics.h

**네임스페이스:** 동시성::그래픽

## <a name="see-also"></a>참고 항목

[Concurrency::graphics 네임스페이스](concurrency-graphics-namespace.md)

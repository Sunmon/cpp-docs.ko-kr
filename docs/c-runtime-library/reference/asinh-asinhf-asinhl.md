---
title: asinh, asinhf, asinhl
ms.date: 4/2/2020
api_name:
- asinh
- asinhf
- asinhl
- _o_asinh
- _o_asinhf
- _o_asinhl
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- asinhf
- asinhl
- asinh
helpviewer_keywords:
- asinh function
- asinhl function
- asinhf function
ms.assetid: 4488babe-1a7e-44ca-8b7b-c2db0a70084f
ms.openlocfilehash: a200aa6e511ab83866fbf1df2beabb827c611c46
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919616"
---
# <a name="asinh-asinhf-asinhl"></a>asinh, asinhf, asinhl

역쌍곡 사인을 계산합니다.

## <a name="syntax"></a>구문

```C
double asinh( double x );
float asinhf( float x );
long double asinhl( long double x );
```

```cpp
float asinh( float x );  // C++ only
long double asinh( long double x );  // C++ only
```

### <a name="parameters"></a>매개 변수

*x*<br/>
부동 소수점 값입니다.

## <a name="return-value"></a>Return Value

**Asinh** 함수는 *x*의 역 하이퍼볼릭 사인 (원호 하이퍼볼릭 사인)을 반환 합니다. 이 함수는 부동 소수점 도메인에 대해 유효합니다. *X* 가 quiet NaN, 무한 또는 무한대 이면 동일한 값이 반환 됩니다.

|입력|SEH 예외|**_matherr** 발생할|
|-----------|-------------------|--------------------------|
|± QNAN, IND, INF|없음|없음|

## <a name="remarks"></a>설명

C + +를 사용 하는 경우 **float** 또는 **long** **double** 값을 사용 하 고 반환 하는 **asinh** 의 오버 로드를 호출할 수 있습니다. C 프로그램에서 **asinh** 는 항상 **double**을 사용 하 고 반환 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|기능|필수 C 헤더|필수 C++ 헤더|
|--------------|--------------|------------------|
|**asinh**, **asinh**, **asinh**|\<math.h>|\<cmath>> 또는 \<math<|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_asinh.c
// Compile by using: cl /W4 crt_asinh.c
// This program displays the hyperbolic sine of pi / 4
// and the arc hyperbolic sine of the result.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x, y;

   x = sinh( pi / 4 );
   y = asinh( x );
   printf( "sinh( %f ) = %f\n", pi/4, x );
   printf( "asinh( %f ) = %f\n", x, y );
}
```

```Output
sinh( 0.785398 ) = 0.868671
asinh( 0.868671 ) = 0.785398
```

## <a name="see-also"></a>참조

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)<br/>
[cosh, coshf, coshl](cosh-coshf-coshl.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)<br/>

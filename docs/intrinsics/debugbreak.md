---
title: __debugbreak
ms.date: 09/02/2019
f1_keywords:
- __debugbreak_cpp
- __debugbreak
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
ms.openlocfilehash: e4cf2c85818a878417c560ddb5a80f8690e60a93
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217929"
---
# <a name="__debugbreak"></a>__debugbreak

**Microsoft 전용**

코드에서 중단점이 발생하며 사용자에게 디버거를 실행하라는 메시지가 표시됩니다.

## <a name="syntax"></a>구문

```C
void __debugbreak();
```

## <a name="requirements"></a>요구 사항

|내장 함수|아키텍처|헤더|
|---------------|------------------|------------|
|`__debugbreak`|x86, x64, ARM, ARM64|\<intrin.h>|

## <a name="remarks"></a>설명

[Debugbreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak)와 유사한 컴파일러내장함수는중단점을발생시키는이식가능한Win32방법입니다.`__debugbreak`

> [!NOTE]
> **/Clr**을 사용 하 여 컴파일하는 경우 `__debugbreak` 를 포함 하는 함수가 MSIL로 컴파일됩니다. `asm int 3`은 함수를 네이티브로 컴파일하도록 합니다. 자세한 내용은 [__asm](../assembler/inline/asm.md)를 참조 하세요.

예:

```C
main() {
   __debugbreak();
}
```

위의 예는 아래 예와 유사합니다.

```C
main() {
   __asm {
      int 3
   }
}
```

x86 컴퓨터의 경우

ARM64 `__debugbreak` 에서 내장 함수는 명령 `brk #0xF000`으로 컴파일됩니다.

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참고자료

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[C++ 키워드](../cpp/keywords-cpp.md)

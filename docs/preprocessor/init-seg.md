---
title: init_seg pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.init_seg
- init_seg_CPP
helpviewer_keywords:
- pragmas, init_seg
- init_seg pragma
- data segment initializing [C++]
ms.assetid: 40a5898a-5c85-4aa9-8d73-3d967eb13610
ms.openlocfilehash: 5e57ea0eedfc1df6e196391c5edd3acfbad0a7c7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221010"
---
# <a name="init_seg-pragma"></a>init_seg pragma

**C++컴퓨터별**

시작 코드가 실행되는 순서에 영향을 주는 키워드 또는 코드 섹션을 지정합니다.

## <a name="syntax"></a>구문

> **#pragma init_seg (** { **컴파일러** | **lib** | **사용자** | "*섹션 이름*" [ **,** *func-name* ]} **)**

## <a name="remarks"></a>설명

이 문서에서 *세그먼트* 와 *섹션* 은 동일한 의미를 갖습니다.

코드는 때때로 전역 정적 개체를 초기화 해야 하므로 개체를 생성할 시기를 지정 해야 합니다. 특히 Dll (동적 연결 라이브러리) 또는 초기화가 필요한 라이브러리에서 **init_seg** pragma를 사용 하는 것이 중요 합니다.

**Init_seg** pragma에 대 한 옵션은 다음과 같습니다.

**컴파일러나**\
Microsoft C 런타임 라이브러리 초기화용으로 예약되어 있습니다. 이 그룹의 개체는 처음 생성됩니다.

**lib**\
타사 클래스 라이브러리 공급업체의 초기화에 사용할 수 있습니다. 이 그룹의 개체는 **컴파일러**로 표시 된 후 다른 모든 개체 보다 먼저 생성 됩니다.

**정의**\
모든 사용자가 사용할 수 있습니다. 이 그룹의 개체는 마지막에 생성됩니다.

*섹션-이름*\
초기화 섹션의 명시적 지정을 허용합니다. 사용자 지정 *섹션 이름* 에 있는 개체는 암시적으로 생성 되지 않습니다. 그러나 해당 주소는 *섹션 이름*으로 명명 된 섹션에 배치 됩니다.

사용자가 지정 하는 *섹션 이름* 에는 해당 모듈에서 pragma 뒤에 선언 된 전역 개체를 구성 하는 도우미 함수에 대 한 포인터가 포함 됩니다.

섹션을 만들 때 사용할 수 없는 이름 목록은 [/SECTION](../build/reference/section-specify-section-attributes.md)를 참조 하세요.

*func-name*\
프로그램이 종료되면 `atexit` 대신 호출될 함수를 지정합니다. 이 도우미 함수는 전역 개체의 소멸자에 대 한 포인터를 사용 하 여 [atexit](../c-runtime-library/reference/atexit.md) 도 호출 합니다. 다음 형식의 pragma에서 함수 식별자를 지정하면

```cpp
int __cdecl myexit (void (__cdecl *pf)(void))
```

C 런타임 라이브러리의 `atexit` 대신 해당 함수가 호출됩니다. 이를 통해 개체를 제거할 준비가 되 면 호출할 소멸자 목록을 작성할 수 있습니다.

초기화를 지연해야 하는 경우(예: DLL에서) 섹션 이름을 명시적으로 지정할 수 있습니다. 그런 다음 코드에서 각 정적 개체에 대 한 생성자를 호출 해야 합니다.

`atexit` 대체 식별자에는 따옴표가 없습니다.

개체는 다른 `XXX_seg` pragma에 정의 된 섹션에 계속 배치 됩니다.

모듈에 선언 된 개체는 C 런타임에 의해 자동으로 초기화 되지 않습니다. 코드에서 초기화를 수행 해야 합니다.

기본적으로 `init_seg` 섹션은 읽기 전용입니다. 섹션 이름이 `.CRT`이면 컴파일러가 읽기, 쓰기로 표시 된 경우에도 특성을 읽기 전용으로 자동 변경 합니다.

변환 단위에서 **init_seg** 를 두 번 이상 지정할 수 없습니다.

개체에 코드에서 명시적으로 정의 된 사용자 정의 생성자가 없는 경우에도 컴파일러에서 사용자 정의 생성자를 생성할 수 있습니다. 예를 들어 v-table 포인터를 바인딩하기 위해 하나를 만들 수 있습니다. 필요한 경우 코드에서 컴파일러에서 생성 된 생성자를 호출 합니다.

## <a name="example"></a>예제

```cpp
// pragma_directive_init_seg.cpp
#include <stdio.h>
#pragma warning(disable : 4075)

typedef void (__cdecl *PF)(void);
int cxpf = 0;   // number of destructors we need to call
PF pfx[200];    // pointers to destructors.

int myexit (PF pf) {
   pfx[cxpf++] = pf;
   return 0;
}

struct A {
   A() { puts("A()"); }
   ~A() { puts("~A()"); }
};

// ctor & dtor called by CRT startup code
// because this is before the pragma init_seg
A aaaa;

// The order here is important.
// Section names must be 8 characters or less.
// The sections with the same name before the $
// are merged into one section. The order that
// they are merged is determined by sorting
// the characters after the $.
// InitSegStart and InitSegEnd are used to set
// boundaries so we can find the real functions
// that we need to call for initialization.

#pragma section(".mine$a", read)
__declspec(allocate(".mine$a")) const PF InitSegStart = (PF)1;

#pragma section(".mine$z",read)
__declspec(allocate(".mine$z")) const PF InitSegEnd = (PF)1;

// The comparison for 0 is important.
// For now, each section is 256 bytes. When they
// are merged, they are padded with zeros. You
// can't depend on the section being 256 bytes, but
// you can depend on it being padded with zeros.

void InitializeObjects () {
   const PF *x = &InitSegStart;
   for (++x ; x < &InitSegEnd ; ++x)
      if (*x) (*x)();
}

void DestroyObjects () {
   while (cxpf>0) {
      --cxpf;
      (pfx[cxpf])();
   }
}

// by default, goes into a read only section
#pragma init_seg(".mine$m", myexit)

A bbbb;
A cccc;

int main () {
   InitializeObjects();
   DestroyObjects();
}
```

```Output
A()
A()
A()
~A()
~A()
~A()
```

## <a name="see-also"></a>참고자료

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

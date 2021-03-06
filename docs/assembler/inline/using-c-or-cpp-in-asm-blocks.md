---
title: __asm 블록에서 C 또는 C++ 사용
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembly, mixing instructions with C/C++ statements
- symbols, in __asm blocks
- macros, __asm blocks
- preprocessor directives, used in __asm blocks
- type names, used in __asm blocks
- preprocessor directives
- preprocessor, directives
- constants, in __asm blocks
- comments, in __asm blocks
- typedef names, used in __asm blocks
- __asm keyword [C++], C/C++ elements in
ms.assetid: ae8b2b52-6b75-42e3-ac0c-ad02d922ed97
ms.openlocfilehash: 16b298b92a4ba40d9091499a1821ad4f3c413d6c
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74854526"
---
# <a name="using-c-or-c-in-__asm-blocks"></a>__asm 블록에서 C 또는 C++ 사용

**Microsoft 전용**

인라인 어셈블리 명령은 C 또는 C++ 문과 함께 사용할 수 있으므로 C 또는 C++ 변수를 이름으로 참조하고 이러한 언어의 다른 많은 요소를 사용할 수 있습니다.

`__asm` 블록은 다음 언어 요소를 사용할 수 있습니다.

- 레이블과 변수 및 함수 이름을 포함하는 기호

- 기호화된 상수와 `enum` 멤버를 포함하는 상수

- 매크로 및 전처리기 지시문

- 설명 ( __/\* \*/__ 및 __//__ )

- 형식 이름(MASM 형식이 올바를 때마다)

- 일반적으로 **PTR** , **TYPE** 등의 연산자와 함께 사용 되거나 구조체 또는 공용 구조체 멤버를 지정 하는 `typedef` 이름입니다.

`__asm` 블록 내에서 C 표기법 또는 어셈블러 기수 표기법과 함께 정수 상수(예: 0x100 및 100h는 동일)를 지정할 수 있습니다. 이를 통해 C에서 (`#define`을 사용하여) 상수를 정의한 다음 C 또는 C++ 모두와 프로그램의 어셈블리 부분에서 사용할 수 있습니다. a 0과 함께 이전 상수에 의해 8진수에서 상수를 지정할 수도 있습니다. 예를 들어, 0777은 8진수 상수를 지정합니다.

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [__asm 블록에서 연산자 사용](../../assembler/inline/using-operators-in-asm-blocks.md)

- [C 또는 C++ Symbols_in __asm 블록 사용](../../assembler/inline/using-c-or-cpp-symbols-in-asm-blocks.md)

- [__asm 블록에서 C 또는 C++ 데이터 액세스](../../assembler/inline/accessing-c-or-cpp-data-in-asm-blocks.md)

- [인라인 어셈블리로 함수 작성](../../assembler/inline/writing-functions-with-inline-assembly.md)

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[인라인 어셈블러](../../assembler/inline/inline-assembler.md)<br/>

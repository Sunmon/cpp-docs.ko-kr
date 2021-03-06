---
title: 전처리기 지시문
ms.date: 08/29/2019
helpviewer_keywords:
- directives, preprocessor
- preprocessor, directives
ms.assetid: e0fc4564-b6cf-4a36-bf51-6ccd7abd0a94
ms.openlocfilehash: 86432ebf210523dd958f3258075d9e9c6d3bb4e6
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222270"
---
# <a name="preprocessor-directives"></a>전처리기 지시문

`#define`, `#ifdef`과 같은 전처리기 지시문은 일반적으로 소스 프로그램을 쉽게 변경하고 여러 실행 환경에서 쉽게 컴파일할 수 있도록 하는데 사용됩니다. 소스 파일의 지시문은 특정 작업을 수행 하도록 전처리기에 지시 합니다. 예를 들어 전처리기는 텍스트에서 토큰을 대체하거나, 다른 파일의 내용을 소스 파일에 삽입하거나, 소스코드의 부분을 제거하여 컴파일되지 않도록 할 수 있습니다. 전처리기 코드 줄은 컴파일 과정에서 매크로가 실제 코드로 대체되기 전에 인식되고 수행됩니다. 따라서 매크로가 전처리기 명령과 같이 보이는 항목으로 확장 되 면 전처리기에서 인식 되지 않습니다.

전처리기 문은 이스케이프 시퀀스가 지원 되지 않는 경우를 제외 하 고 소스 파일 문과 동일한 문자 집합을 사용 합니다. 전처리기 명령문에 사용된 문자 집합은 실행 문자 집합과 동일합니다. 전처리기는 음수 문자 값도 인식합니다.

전처리기는 다음 지시문을 인식합니다.

|||||
|-|-|-|-|
|[#define](../preprocessor/hash-define-directive-c-cpp.md)|[#error](../preprocessor/hash-error-directive-c-cpp.md)|[#import](../preprocessor/hash-import-directive-cpp.md)|[#undef](../preprocessor/hash-undef-directive-c-cpp.md)|
|[#elif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#if](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#include](../preprocessor/hash-include-directive-c-cpp.md)|[#using](../preprocessor/hash-using-directive-cpp.md)|
|[#else](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#ifdef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#line](../preprocessor/hash-line-directive-c-cpp.md)|[#endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|
|[#ifndef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)|||

숫자 기호 (`#`)는 지시문을 포함 하는 줄의 첫 번째 공백 아닌 공백 문자 여야 합니다. 공백 문자는 지시문의 숫자 기호와 첫 문자 사이에 나타날 수 있습니다. 일부 지시문에는 인수 또는 값을 함께 사용합니다. 지시문 뒤에 오는 모든 텍스트 (지시문의 일부인 인수 또는 값 제외)는 한 줄로 된 주석 구분 기호 (`//`) 앞 이나 주석 구분 기호 (`/* */`)로 묶어야 합니다. 전처리기 지시문이 포함 된 줄은 백슬래시 (`\`)를 사용 하 여 줄 끝 표식 바로 앞에 올 수 있습니다.

전처리기 지시문은 소스 파일의 어디에 나 나타날 수 있지만 소스 파일의 나머지 부분에만 적용 됩니다.

## <a name="see-also"></a>참고자료

[전처리기 연산자](../preprocessor/preprocessor-operators.md)\
[미리 정의 된 매크로](../preprocessor/predefined-macros.md)\
[c/c + + 전처리기 참조](../preprocessor/c-cpp-preprocessor-reference.md)

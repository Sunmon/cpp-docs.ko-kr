---
title: 심각한 오류 C1900
ms.date: 11/04/2016
f1_keywords:
- C1900
helpviewer_keywords:
- C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
ms.openlocfilehash: 6a802928315126b72397ba6e8cc61b66f46deb41
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202842"
---
# <a name="fatal-error-c1900"></a>심각한 오류 C1900

> '*Tool1*' 버전 '*number1*' 및 '*tool2*' 버전 '*number2*' 사이에 Il이 일치 하지 않습니다.

컴파일러의 여러 패스에서 실행되는 도구가 일치하지 않습니다. *number1* 및 *number2* 는 파일의 날짜를 나타냅니다. 예를 들어 패스 1에서는 컴파일러 프런트 엔드가 실행되고(c1.dll) 패스 2에서는 컴파일러 백 엔드가 실행됩니다(c2.dll) 파일의 날짜는 일치해야 합니다.

이 문제를 해결하려면 Visual Studio에 모든 업데이트가 적용되었는지 확인합니다. 문제가 지속 되 면 Windows 제어판의 **프로그램 및 기능** 을 사용 하 여 Visual Studio를 복구 하거나 다시 설치 합니다.

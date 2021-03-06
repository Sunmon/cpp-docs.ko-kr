---
title: C 런타임 오류 R6017
ms.date: 11/04/2016
f1_keywords:
- R6017
helpviewer_keywords:
- R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
ms.openlocfilehash: 2d868939425c11f13dffd84e28c1afee45e3b11a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197304"
---
# <a name="c-runtime-error-r6017"></a>C 런타임 오류 R6017

예기치 않은 다중 스레드 잠금 오류

> [!NOTE]
> 앱을 실행 하는 동안이 오류 메시지가 표시 되 면 내부 문제가 있기 때문에 앱이 종료 되었습니다. 이 오류가 발생할 수 있는 몇 가지 원인이 있지만 앱 코드의 결함으로 인해 발생 하는 경우가 종종 있습니다.
>
> 이 오류를 해결하려면 다음 단계를 시도할 수 있습니다.
>
> - **제어판** 의 **앱 및 기능** 또는 **프로그램 및 기능** 페이지를 사용 하 여 프로그램을 복구 하거나 다시 설치 합니다.
> - **제어판** 의 소프트웨어 업데이트에 대 한 **Windows 업데이트** 를 확인 합니다.
> - 앱의 업데이트 된 버전을 확인 합니다. 문제가 지속 되 면 앱 공급 업체에 문의 하세요.

**프로그래머를 위한 정보**

시스템 리소스에 대 한 C 런타임 다중 스레드 잠금 액세스를 시도 하는 동안 프로세스에서 예기치 않은 오류가 발생 했습니다. 일반적으로이 오류는 프로세스가 런타임 힙 데이터를 실수로 변경 하는 경우에 발생 합니다. 그러나 런타임 라이브러리나 운영 체제 코드에서 내부 오류가 원인일 수도 있습니다.

이 문제를 해결 하려면 코드에서 힙 손상 버그를 확인 합니다. 자세한 내용 및 예제는 [CRT 디버그 힙 정보](/visualstudio/debugger/crt-debug-heap-details)를 참조 하세요. 다음으로, 앱 배포에 대 한 최신 재배포 가능 패키지를 사용 하 고 있는지 확인 합니다. 자세한 내용은 [ C++Visual에서 배포 ](../../windows/deployment-in-visual-cpp.md)를 참조 하세요.

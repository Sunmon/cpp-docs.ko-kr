---
title: C 런타임 오류 R6032
ms.date: 11/04/2016
f1_keywords:
- R6032
helpviewer_keywords:
- R6032
ms.assetid: 52092a63-cc51-444a-bfc3-fad965a3558e
ms.openlocfilehash: b29b946d08cff903cf0ca398ba0d7589cb5d54ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197095"
---
# <a name="c-runtime-error-r6032"></a>C 런타임 오류 R6032

로캘 정보를 위한 공간이 부족 합니다.

> [!NOTE]
> 앱을 실행 하는 동안이 오류 메시지가 표시 되는 경우 내부 메모리 문제가 있기 때문에 앱이 종료 되었습니다. 이 오류에 대 한 몇 가지 가능한 이유가 있지만 메모리 부족 상태 또는 프로그램의 버그로 인해 발생 하는 경우가 많습니다.
>
> 이 오류를 해결하려면 다음 단계를 시도할 수 있습니다.
>
> - 실행 중인 다른 응용 프로그램을 닫거나 컴퓨터를 다시 시작 하 여 메모리를 확보 하십시오.
> - **제어판** 의 **앱 및 기능** 또는 **프로그램 및 기능** 페이지를 사용 하 여 프로그램을 복구 하거나 다시 설치 합니다.
> - **제어판** 의 소프트웨어 업데이트에 대 한 **Windows 업데이트** 를 확인 합니다.
> - 앱의 업데이트 된 버전을 확인 합니다. 문제가 지속 되 면 앱 공급 업체에 문의 하세요.

**프로그래머를 위한 정보**

런타임은 로캘 구분 함수에 대 한 호출을 처리할 수 있도록 각 스레드의 로캘에 대 한 정보를 유지 관리 합니다. 이 정보에 대 한 메모리 할당이 실패 하는 경우 기본 기능이 너무 많기 때문에 런타임을 계속할 수 없습니다.

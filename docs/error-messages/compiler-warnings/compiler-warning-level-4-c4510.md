---
title: 컴파일러 경고(수준 4) C4510
description: 컴파일러 경고 C4510 설명 및 솔루션입니다.
ms.date: 09/22/2019
f1_keywords:
- C4510
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
ms.openlocfilehash: 05a6d0fe42d8247d3328506d8772b2fa77b5703c
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230377"
---
# <a name="compiler-warning-level-4-c4510"></a>컴파일러 경고(수준 4) C4510

> '*class*': 기본 생성자를 생성할 수 없습니다.

컴파일러가 사용자 정의 생성자가 없는 지정 된 클래스에 대 한 기본 생성자를 생성할 수 없습니다. 이 유형의 개체를 만들 수 없습니다.

다음을 포함 하 여 컴파일러가 기본 생성자를 생성 하지 못하도록 하는 여러 상황이 있습니다.

- **Const** 데이터 멤버입니다.

- 참조 인 데이터 멤버입니다.

이 문제를 해결 하려면 이러한 멤버를 초기화 하는 클래스에 대 한 사용자 정의 기본 생성자를 만듭니다.

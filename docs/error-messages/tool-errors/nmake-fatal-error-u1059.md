---
title: NMAKE 심각한 오류 U1059
ms.date: 08/27/2018
f1_keywords:
- U1059
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
ms.openlocfilehash: 33be3312e1f0aaa7f1e8aad64b44ea9aefd25346
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182840"
---
# <a name="nmake-fatal-error-u1059"></a>NMAKE 심각한 오류 U1059

> 구문 오류: 종속에 '} '가 없습니다.

종속 된 검색 경로가 잘못 지정 되었습니다. 경로에 공백이 있거나 닫는 중괄호 ( **}** )가 생략 되었습니다.

종속에 대 한 디렉터리 사양의 구문은

> **{** *directory* **} 종속**

여기서 *디렉터리* 는 하나 이상의 경로를 지정 하며 각 경로는 세미콜론 ( **;** )으로 구분 됩니다. 공백은 허용 되지 않습니다.

검색 경로의 일부 또는 전체가 매크로로 대체 되는 경우 매크로 확장에 공백이 없는지 확인 합니다.

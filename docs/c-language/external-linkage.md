---
title: 외부 링크
ms.date: 11/04/2016
helpviewer_keywords:
- linkage [C++], external
- external linkage, about external linkage
- external linkage
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
ms.openlocfilehash: 35b0fda1f501755640123f5181454a5c36b7e986
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233743"
---
# <a name="external-linkage"></a>외부 링크

식별자에 대한 파일 범위 수준의 첫 번째 선언이 **static** 스토리지 클래스 지정자를 사용하지 않으면 개체는 외부 링크를 포함하고 있습니다.

함수에 대한 식별자 선언에 *storage-class-specifier*가 없는 경우 해당 링크는 *storage-class-specifier* `extern`로 선언된 것처럼 결정됩니다. 개체에 대한 식별자 선언에 파일 범위가 있고 *storage-class-specifier*가 없는 경우 해당 링크는 외부입니다.

외부 링크가 있는 식별자의 이름은 외부 링크와 같은 이름에 대해 다른 선언을 할 때와 같은 함수 또는 데이터 개체를 지정합니다. 두 선언이 동일한 변환 단위나 다른 변환 단위일 수 있습니다. 개체 또는 함수에 전역 수명도 있는 경우 전체 프로그램이 개체 또는 함수를 공유합니다.

## <a name="see-also"></a>참조

[extern을 사용하여 링크 지정](../cpp/using-extern-to-specify-linkage.md)

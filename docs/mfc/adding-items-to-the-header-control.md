---
title: 헤더 컨트롤에 항목 추가
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
ms.openlocfilehash: 5749a0cae2dfe7e6c9f4c166eca487e36c2d21d2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616462"
---
# <a name="adding-items-to-the-header-control"></a>헤더 컨트롤에 항목 추가

부모 창에서 헤더 컨트롤 ([CHeaderCtrl](reference/cheaderctrl-class.md))을 만든 후 필요한 만큼 "헤더 항목"을 추가 합니다. 일반적으로 열 마다 하나씩 추가 합니다.

### <a name="to-add-a-header-item"></a>헤더 항목을 추가 하려면

1. [HD_ITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) 구조를 준비 합니다.

1. [CHeaderCtrl:: InsertItem](reference/cheaderctrl-class.md#insertitem)를 호출 하 고 구조체를 전달 합니다.

1. 추가 항목에 대해 1 단계와 2 단계를 반복 합니다.

자세한 내용은 Windows SDK에서 [헤더 컨트롤에 항목 추가](/windows/win32/Controls/header-controls) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CHeaderCtrl 사용](using-cheaderctrl.md)<br/>
[컨트롤](controls-mfc.md)

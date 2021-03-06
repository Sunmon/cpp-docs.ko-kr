---
title: 공용 구조체의 스토리지
ms.date: 11/04/2016
helpviewer_keywords:
- storage, union
- union keyword [C], storage
- union keyword [C]
ms.assetid: b33d246a-8d20-41c4-89b2-ab05f1428792
ms.openlocfilehash: 49b99dc17fd7bdddd8a47e3bfd5913a70a7631a7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157931"
---
# <a name="storage-of-unions"></a>공용 구조체의 스토리지

공용 구조체 변수와 연결된 스토리지는 공용 구조체의 최대 멤버에 필요한 스토리지입니다. 작은 멤버를 저장하면 사용하지 않는 메모리 공간에 공용 구조체 변수에 포함될 수 있습니다. 모든 멤버가 같은 메모리 공간에 저장되고 같은 주소에서 시작됩니다. 값이 다른 멤버에 할당될 때마다 저장된 값을 덮어씁니다. 예를 들어:

```
union         /* Defines a union named x */
{
    char *a, b;
    float f[20];
} x;
```

`x` 공용 구조체의 멤버는 선언 순서대로 `char` 값의 포인터, `char` 값, **float** 값의 배열입니다. `x`는 공용 구조체의 가장 긴 멤버이므로 `f`에 할당된 스토리지는 요소가 20개인 배열 `f`에 필요한 스토리지입니다. 공용 구조체에 연결된 태그가 없으므로 해당 형식에 이름이 없거나 "익명"입니다.

## <a name="see-also"></a>참조

[공용 구조체 선언](../c-language/union-declarations.md)

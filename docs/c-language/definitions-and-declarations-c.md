---
title: 선언 및 정의 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- export functions
ms.assetid: d150395a-89d4-4298-9ac4-08f84fe1261c
ms.openlocfilehash: 8723c3f09a5e9a8eecf0e552c9f5a7fd9b7f6c68
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234360"
---
# <a name="definitions-and-declarations-c"></a>선언 및 정의 (C)

**Microsoft 전용**

DLL 인터페이스는 시스템의 일부 프로그램에서 내보내지는 것으로 알려진 모든 항목(함수 및 데이터), 즉 **dllimport** 또는 `dllexport`로 선언되는 모든 항목을 참조합니다. DLL 인터페이스에 포함된 모든 선언은 **dllimport** 또는 `dllexport` 특성을 지정해야 합니다. 하지만 정의는 `dllexport` 특성만 지정할 수 있습니다. 예를 들어, 다음 함수 정의는 컴파일러 오류를 생성합니다.

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllImport int func()    /* Error; dllimport prohibited in */
                        /* definition. */
{
   return 1;
}
```

다음 코드도 오류를 생성합니다.

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllImport int i = 10;      /* Error; this is a definition. */
```

그러나 다음은 올바른 구문입니다.

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport int i = 10;      /* Okay: this is an export definition. */
```

**dllimport**가 선언을 암시하는 반면 `dllexport`는 정의를 암시합니다. `extern`에 `dllexport` 키워드를 사용하여 선언을 강제해야 합니다. 그렇지 않으면 정의가 암시됩니다.

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllImport int k;   /* These are correct and imply */
Dllimport int j;          /* a declaration. */
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[DLL 가져오기 및 내보내기 함수](../c-language/dll-import-and-export-functions.md)

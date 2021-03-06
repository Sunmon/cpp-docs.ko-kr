---
title: /VERBOSE(진행 메시지 표시)
ms.date: 06/13/2019
f1_keywords:
- /verbose
- VC.Project.VCLinkerTool.ShowProgress
helpviewer_keywords:
- -VERBOSE linker option
- linking [C++], session progress information
- Print Progress Messages linker option
- linker [C++], output dependency information
- /VERBOSE linker option
- dependencies [C++], dependency information in linker output
- VERBOSE linker option
ms.assetid: 9c347d98-4c37-4724-a39e-0983934693ab
ms.openlocfilehash: bbf7b5966c741535f26202979cbfd71f839cc537
ms.sourcegitcommit: e79188287189b76b34eb7e8fb1bfe646bdb586bc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67141664"
---
# <a name="verbose-print-progress-messages"></a>/VERBOSE(진행 메시지 표시)

연결 프로세스 중 진행 메시지를 출력 합니다.

## <a name="syntax"></a>구문

> **/VERBOSE**\[ **:** {**CLR**|**ICF**|**INCR**|**LIB**|**REF**|**SAFESEH**|**UNUSEDDELAYLOAD**|**UNUSEDLIBS**}\]

## <a name="remarks"></a>설명

링커 보내는 연결 세션의 진행률에 대 한 정보를 **출력** 창입니다. 명령줄에서 정보를 표준 출력으로 전송 되 고 파일로 리디렉션할 수 있습니다.

| 옵션 | 설명 |
| ------------ | ----------------- |
| /VERBOSE | 연결 프로세스에 대 한 세부 정보를 표시 합니다. |
| /VERBOSE:CLR | 개체 및 메타 데이터를 사용 하 여 컴파일된 특정 링커 작업에 대 한 정보를 표시 [/clr](clr-common-language-runtime-compilation.md)합니다. |
| /VERBOSE:ICF | 사용할 때 발생 하는 링커 작업에 대 한 정보를 표시 [/opt: icf](opt-optimizations.md)합니다. |
| /VERBOSE:INCR | 증분적인 링크 프로세스에 대한 정보를 표시합니다. |
| /VERBOSE:LIB | 검색된 라이브러리만 나타내는 진행률 메시지를 표시합니다.<br/> 라이브러리 검색 프로세스를 포함 하는 정보를 표시 합니다. 각 라이브러리 및 개체 이름 (전체 경로)를 나열, 라이브러리 및 기호를 참조 하는 개체의 목록에서 확인 되는 기호입니다. |
| /VERBOSE:REF | 사용할 때 발생 하는 링커 작업에 대 한 정보를 표시 [/opt: ref](opt-optimizations.md)합니다. |
| /VERBOSE:SAFESEH | 구조적된 때 안전한 예외 처리와 호환 되지 않는 모듈에 대 한 정보를 표시 [/SAFESEH](safeseh-image-has-safe-exception-handlers.md) 지정 되지 않습니다. |
| /VERBOSE:UNUSEDDELAYLOAD | 로드 된 이미지를 만들 때 사용 되는 기호가 있는 Dll을 지연에 대 한 정보를 표시 합니다. |
| /VERBOSE:UNUSEDLIBS | 이미지를 만들 때 사용되지 않은 모든 라이브러리 파일에 대한 정보를 표시합니다. |

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. 선택 된 **구성 속성** > **링커** > **명령줄** 속성 페이지.

1. 옵션을 추가 합니다 **추가 옵션** 상자입니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ShowProgress%2A>을 참조하세요.

## <a name="see-also"></a>참고자료

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)

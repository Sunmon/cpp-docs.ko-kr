---
title: 속성 페이지(MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages [MFC], global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
ms.openlocfilehash: 6456a192a502a0fcc032eaefc667c90ecec86d42
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751148"
---
# <a name="property-pages-mfc"></a>속성 페이지(MFC)

속성 페이지는 대화 상자 데이터 교환(DDX)을 기반으로 하는 데이터 매핑 메커니즘을 지원하여 보고 편집할 수 있는 사용자 지정 가능한 그래픽 인터페이스에 특정 OLE 제어 속성의 현재 값을 표시합니다.

이 데이터 매핑 메커니즘은 속성 페이지 컨트롤을 OLE 컨트롤의 개별 속성에 매핑합니다. 컨트롤 속성의 값은 속성 페이지 컨트롤의 상태 또는 내용을 반영합니다. 속성 페이지 컨트롤과 속성 간의 매핑은 속성 페이지의 `DoDataExchange` 멤버 함수에서 함수 **호출을 DDP_** 지정합니다. 다음은 컨트롤의 속성 페이지를 사용하여 입력된 데이터를 교환하는 **DDP_** 함수 목록입니다.

### <a name="property-page-data-transfer"></a>속성 페이지 데이터 전송

|||
|-|-|
|[DDP_CBIndex](#ddp_cbindex)|선택한 문자열의 인덱스를 컨트롤의 속성과 콤보 상자에 연결합니다.|
|[DDP_CBString](#ddp_cbstring)|선택한 문자열을 컨트롤의 속성과 콤보 상자에 연결합니다. 선택한 문자열은 속성 값과 동일한 문자로 시작할 수 있지만 완전히 일치할 필요는 없습니다.|
|[DDP_CBStringExact](#ddp_cbstringexact)|선택한 문자열을 컨트롤의 속성과 콤보 상자에 연결합니다. 선택한 문자열과 속성의 문자열 값이 정확히 일치해야 합니다.|
|[DDP_Check](#ddp_check)|컨트롤의 속성 페이지에 있는 확인란을 컨트롤의 속성과 연결합니다.|
|[DDP_LBIndex](#ddp_lbindex)|선택한 문자열의 인덱스를 목록 상자에 컨트롤의 속성과 연결합니다.|
|[DDP_LBString](#ddp_lbstring)|선택한 문자열을 목록 상자에 컨트롤의 속성과 연결합니다. 선택한 문자열은 속성값과 동일한 문자로 시작할 수 있지만 완전히 일치하지는 않아도 됩니다.|
|[DDP_LBStringExact](#ddp_lbstringexact)|선택한 문자열을 목록 상자에 컨트롤의 속성과 연결합니다. 선택한 문자열과 속성의 문자열 값이 정확히 일치해야 합니다.|
|[DDP_PostProcessing](#ddp_postprocessing)|컨트롤에서 속성 값의 전송을 완료합니다.|
|[DDP_Radio](#ddp_radio)|컨트롤의 속성 페이지에 라디오 단추 그룹을 연결 합니다.|
|[DDP_Text](#ddp_text)|컨트롤의 속성 페이지에서 컨트롤의 속성을 연결 합니다. 이 함수는 **double**, **short**, BSTR 및 **long과**같은 여러 가지 유형의 속성을 처리합니다.|

함수 및 속성 페이지에 대한 자세한 내용은 [ActiveX 컨트롤: 속성 페이지](../../mfc/mfc-activex-controls-property-pages.md)문서를 참조하십시오. `DoDataExchange`

다음은 OLE 컨트롤의 속성 페이지를 만들고 관리하는 데 사용되는 매크로 목록입니다.

### <a name="property-pages"></a>속성 페이지

|||
|-|-|
|[BEGIN_PROPPAGEIDS](#begin_proppageids)|속성 페이지 아이디 목록을 시작합니다.|
|[END_PROPPAGEIDS](#end_proppageids)|속성 페이지 아이디 목록을 종료합니다.|
|[PROPPAGEID](#proppageid)|컨트롤 클래스의 속성 페이지를 선언합니다.|

## <a name="ddp_cbindex"></a><a name="ddp_cbindex"></a>DDP_CBIndex

속성 페이지의 `DoDataExchange` 함수에서 이 함수를 호출하여 정수 속성의 값을 속성 페이지의 콤보 상자에 있는 현재 선택 항목의 인덱스와 동기화합니다.

```cpp
void AFXAPI DDP_CBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*id*<br/>
*pszPropName에서*지정한 제어 속성과 연결된 콤보 상자 컨트롤의 리소스 ID입니다.

*멤버*<br/>
*id로* 지정된 속성 페이지 컨트롤과 연결된 멤버 변수 및 *pszPropName에서*지정한 속성입니다.

*pszPropName*<br/>
*id로*지정된 콤보 상자 컨트롤과 교환할 컨트롤 속성의 속성 이름입니다.

### <a name="remarks"></a>설명

이 함수는 해당 `DDX_CBIndex` 함수 호출 전에 호출되어야 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxctl.h

## <a name="ddp_cbstring"></a><a name="ddp_cbstring"></a>DDP_CBString

속성 페이지의 `DoDataExchange` 함수에서 이 함수를 호출하여 속성 페이지의 콤보 상자에서 현재 선택 항목과 string 속성 값을 동기화합니다.

```cpp
void AFXAPI DDP_CBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*id*<br/>
*pszPropName에서*지정한 제어 속성과 연결된 콤보 상자 컨트롤의 리소스 ID입니다.

*멤버*<br/>
*id로* 지정된 속성 페이지 컨트롤과 연결된 멤버 변수 및 *pszPropName에서*지정한 속성입니다.

*pszPropName*<br/>
*id로*지정된 콤보 상자 문자열로 교환할 컨트롤 속성의 속성 이름입니다.

### <a name="remarks"></a>설명

이 함수는 해당 `DDX_CBString` 함수 호출 전에 호출되어야 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxctl.h

## <a name="ddp_cbstringexact"></a><a name="ddp_cbstringexact"></a>DDP_CBStringExact

속성 페이지의 `DoDataExchange` 함수에서 이 함수를 호출하여 속성 페이지의 콤보 상자에서 현재 선택 항목과 정확히 일치하는 문자열 속성의 값을 동기화합니다.

```cpp
void AFXAPI DDP_CBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*id*<br/>
*pszPropName에서*지정한 제어 속성과 연결된 콤보 상자 컨트롤의 리소스 ID입니다.

*멤버*<br/>
*id로* 지정된 속성 페이지 컨트롤과 연결된 멤버 변수 및 *pszPropName에서*지정한 속성입니다.

*pszPropName*<br/>
*id로*지정된 콤보 상자 문자열로 교환할 컨트롤 속성의 속성 이름입니다.

### <a name="remarks"></a>설명

이 함수는 해당 `DDX_CBStringExact` 함수 호출 전에 호출되어야 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxctl.h

## <a name="ddp_check"></a><a name="ddp_check"></a>DDP_Check

속성 페이지의 `DoDataExchange` 함수에서 이 함수를 호출하여 속성 값을 연결된 속성 페이지 확인란 컨트롤과 동기화합니다.

```cpp
void AFXAPI DDP_Check(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCSTR pszPropName);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*id*<br/>
*pszPropName에서*지정한 컨트롤 속성과 연결된 확인란 컨트롤의 리소스 ID입니다.

*멤버*<br/>
*id로* 지정된 속성 페이지 컨트롤과 연결된 멤버 변수 및 *pszPropName에서*지정한 속성입니다.

*pszPropName*<br/>
*id로*지정된 확인란 컨트롤과 교환할 컨트롤 속성의 속성 이름입니다.

### <a name="remarks"></a>설명

이 함수는 해당 `DDX_Check` 함수 호출 전에 호출되어야 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxctl.h

## <a name="ddp_lbindex"></a><a name="ddp_lbindex"></a>DDP_LBIndex

속성 페이지의 `DoDataExchange` 함수에서 이 함수를 호출하여 정수 속성의 값을 속성 페이지의 목록 상자에 있는 현재 선택 항목의 인덱스와 동기화합니다.

```cpp
void AFXAPI DDP_LBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*id*<br/>
*pszPropName에서*지정한 컨트롤 속성과 연결된 목록 상자 컨트롤의 리소스 ID입니다.

*멤버*<br/>
*id로* 지정된 속성 페이지 컨트롤과 연결된 멤버 변수 및 *pszPropName에서*지정한 속성입니다.

*pszPropName*<br/>
*id로*지정된 목록 상자 문자열로 교환할 컨트롤 속성의 속성 이름입니다.

### <a name="remarks"></a>설명

이 함수는 해당 `DDX_LBIndex` 함수 호출 전에 호출되어야 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxctl.h

## <a name="ddp_lbstring"></a><a name="ddp_lbstring"></a>DDP_LBString

속성 페이지의 `DoDataExchange` 함수에서 이 함수를 호출하여 string 속성의 값과 속성 페이지의 목록 상자의 현재 선택 영역을 동기화합니다.

```cpp
void AFXAPI DDP_LBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*id*<br/>
*pszPropName에서*지정한 컨트롤 속성과 연결된 목록 상자 컨트롤의 리소스 ID입니다.

*멤버*<br/>
*id로* 지정된 속성 페이지 컨트롤과 연결된 멤버 변수 및 *pszPropName에서*지정한 속성입니다.

*pszPropName*<br/>
*id로*지정된 목록 상자 문자열로 교환할 컨트롤 속성의 속성 이름입니다.

### <a name="remarks"></a>설명

이 함수는 해당 `DDX_LBString` 함수 호출 전에 호출되어야 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxctl.h

## <a name="ddp_lbstringexact"></a><a name="ddp_lbstringexact"></a>DDP_LBStringExact

속성 페이지의 `DoDataExchange` 함수에서 이 함수를 호출하여 속성 페이지의 목록 상자에서 현재 선택 항목과 정확히 일치하는 문자열 속성의 값을 동기화합니다.

```cpp
void AFXAPI DDP_LBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*id*<br/>
*pszPropName에서*지정한 컨트롤 속성과 연결된 목록 상자 컨트롤의 리소스 ID입니다.

*멤버*<br/>
*id로* 지정된 속성 페이지 컨트롤과 연결된 멤버 변수 및 *pszPropName에서*지정한 속성입니다.

*pszPropName*<br/>
*id로*지정된 목록 상자 문자열로 교환할 컨트롤 속성의 속성 이름입니다.

### <a name="remarks"></a>설명

이 함수는 해당 `DDX_LBStringExact` 함수 호출 전에 호출되어야 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxctl.h

## <a name="ddp_postprocessing"></a><a name="ddp_postprocessing"></a>DDP_PostProcessing

속성 페이지의 `DoDataExchange` 함수에서 이 함수를 호출하여 속성 값이 저장될 때 속성 페이지에서 컨트롤로 속성 값의 전송을 완료합니다.

```cpp
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

### <a name="remarks"></a>설명

모든 데이터 교환 함수가 완료된 후 이 함수를 호출해야 합니다. 다음은 그 예입니다.

[!code-cpp[NVC_MFCAxCtl#15](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]

### <a name="requirements"></a>요구 사항

  **헤더** afxctl.h

## <a name="ddp_radio"></a><a name="ddp_radio"></a>DDP_Radio

컨트롤 함수에서 `DoPropExchange` 이 함수를 호출하여 속성 값을 연결된 속성 페이지 라디오 단추 컨트롤과 동기화합니다.

```cpp
void AFXAPI DDP_Radio(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*id*<br/>
*pszPropName에서*지정한 제어 속성과 연결된 라디오 단추 컨트롤의 리소스 ID입니다.

*멤버*<br/>
*id로* 지정된 속성 페이지 컨트롤과 연결된 멤버 변수 및 *pszPropName에서*지정한 속성입니다.

*pszPropName*<br/>
*id로*지정된 라디오 단추 컨트롤과 교환할 컨트롤 속성의 속성 이름입니다.

### <a name="remarks"></a>설명

이 함수는 해당 `DDX_Radio` 함수 호출 전에 호출되어야 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxctl.h

## <a name="ddp_text"></a><a name="ddp_text"></a>DDP_Text

컨트롤의 `DoDataExchange` 함수에서 이 함수를 호출하여 속성 값을 연결된 속성 페이지 컨트롤과 동기화합니다.

```cpp
void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    BYTE & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    UINT & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    long & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    DWORD & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    float & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    double & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    CString & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>매개 변수

*pDX*<br/>
`CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.

*id*<br/>
*pszPropName에서*지정한 컨트롤 속성과 연결된 컨트롤의 리소스 ID입니다.

*멤버*<br/>
*id로* 지정된 속성 페이지 컨트롤과 연결된 멤버 변수 및 *pszPropName에서*지정한 속성입니다.

*pszPropName*<br/>
*id로*지정된 컨트롤과 교환할 컨트롤 속성의 속성 이름입니다.

### <a name="remarks"></a>설명

이 함수는 해당 `DDX_Text` 함수 호출 전에 호출되어야 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxctl.h

## <a name="begin_proppageids"></a><a name="begin_proppageids"></a>BEGIN_PROPPAGEIDS

컨트롤의 속성 페이지 아이디 목록의 정의를 시작합니다.

```
BEGIN_PROPPAGEIDS(class_name,  count)
```

### <a name="parameters"></a>매개 변수

*class_name*<br/>
속성 페이지를 지정하는 컨트롤 클래스의 이름입니다.

*count*<br/>
컨트롤 클래스에서 사용하는 속성 페이지 수입니다.

### <a name="remarks"></a>설명

클래스의 멤버 함수를 정의하는 구현(.cpp) 파일에서 BEGIN_PROPPAGEIDS 매크로로 속성 페이지 목록을 시작한 다음 각 속성 페이지에 대한 매크로 항목을 추가하고 END_PROPPAGEIDS 매크로로 속성 페이지 목록을 완료합니다.

속성 페이지에 대한 자세한 내용은 [ActiveX 컨트롤: 속성 페이지를](../../mfc/mfc-activex-controls-property-pages.md)참조하십시오.

### <a name="requirements"></a>요구 사항

  **헤더** afxctl.h

## <a name="end_proppageids"></a><a name="end_proppageids"></a>END_PROPPAGEIDS

속성 페이지 ID 목록의 정의를 종료합니다.

```
END_PROPPAGEIDS(class_name)
```

### <a name="parameters"></a>매개 변수

*class_name*<br/>
속성 페이지를 소유 하는 컨트롤 클래스의 이름입니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxctl.h

## <a name="proppageid"></a><a name="proppageid"></a>프롭페이지 ID

OLE 컨트롤에서 사용할 속성 페이지를 추가합니다.

```
PROPPAGEID(clsid)
```

### <a name="parameters"></a>매개 변수

*clsid*<br/>
속성 페이지의 고유 클래스 ID입니다.

### <a name="remarks"></a>설명

모든 PROPPAGEID 매크로는 컨트롤의 구현 파일에 있는 BEGIN_PROPPAGEIDS END_PROPPAGEIDS 매크로 사이에 배치되어야 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxctl.h

## <a name="see-also"></a>참조

[매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)

---
title: '방법: .NET 컬렉션에서 STL/CLR 컨테이너로 변환'
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR, converting from .NET collections
- STL/CLR Containers [STL/CLR]
ms.assetid: bb927c48-78e8-4150-bd0b-787c651f4a87
ms.openlocfilehash: 156b4162f742915939ebdfaec6a84d77afaad8cd
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545050"
---
# <a name="how-to-convert-from-a-net-collection-to-a-stlclr-container"></a>방법: .NET 컬렉션에서 STL/CLR 컨테이너로 변환

이 항목에서는 .NET 컬렉션을 해당 하는 STL/CLR 컨테이너로 변환 하는 방법을 보여 줍니다. 예를 들어 .NET <xref:System.Collections.Generic.List%601> STL/CLR [벡터로](../dotnet/vector-stl-clr.md) 변환 하는 방법 및 .net <xref:System.Collections.Generic.Dictionary%602>을 STL/clr [맵으로](../dotnet/map-stl-clr.md)변환 하는 방법을 보여 주지만 프로시저는 모든 컬렉션 및 컨테이너와 유사 합니다.

### <a name="to-create-a-container-from-a-collection"></a>컬렉션에서 컨테이너를 만들려면

1. 전체 컬렉션을 변환 하려면 STL/CLR 컨테이너를 만들고 컬렉션을 생성자에 게 전달 합니다.

   첫 번째 예제에서는이 프로시저를 보여 줍니다.

또는

1. [Collection_adapter](../dotnet/collection-adapter-stl-clr.md) 개체를 만들어 일반 STL/CLR 컨테이너를 만듭니다. 이 템플릿 클래스는 .NET 컬렉션 인터페이스를 인수로 사용 합니다. 지원 되는 인터페이스를 확인 하려면 [collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md)를 참조 하세요.

1. .NET 컬렉션의 내용을 컨테이너에 복사 합니다. STL/CLR [알고리즘](../dotnet/algorithm-stl-clr.md)을 사용 하거나 .net 컬렉션을 반복 하 고 각 요소의 복사본을 STL/clr 컨테이너에 삽입 하 여이 작업을 수행할 수 있습니다.

   두 번째 예에서는이 절차를 보여 줍니다.

## <a name="example"></a>예제

이 예제에서는 제네릭 <xref:System.Collections.Generic.List%601> 만들고 요소 5 개를 추가 합니다. 그런 다음 <xref:System.Collections.Generic.IEnumerable%601>를 인수로 사용 하는 생성자를 사용 하 여 `vector`를 만듭니다.

```cpp
// cliext_convert_list_to_vector.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/algorithm>
#include <cliext/vector>

using namespace System;
using namespace System::Collections;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    List<int> ^primeNumbersColl = gcnew List<int>();
    primeNumbersColl->Add(2);
    primeNumbersColl->Add(3);
    primeNumbersColl->Add(5);
    primeNumbersColl->Add(7);
    primeNumbersColl->Add(11);

    cliext::vector<int> ^primeNumbersCont =
        gcnew cliext::vector<int>(primeNumbersColl);

    Console::WriteLine("The contents of the cliext::vector are:");
    cliext::vector<int>::const_iterator it;
    for (it = primeNumbersCont->begin(); it != primeNumbersCont->end(); it++)
    {
        Console::WriteLine(*it);
    }
}
```

```Output
The contents of the cliext::vector are:
2
3
5
7
11
```

## <a name="example"></a>예제

이 예제에서는 제네릭 <xref:System.Collections.Generic.Dictionary%602> 만들고 요소 5 개를 추가 합니다. 그런 다음 `collection_adapter`를 만들어 <xref:System.Collections.Generic.Dictionary%602> 간단한 STL/CLR 컨테이너로 래핑합니다. 마지막으로 `map`를 만들고 `collection_adapter`를 반복 하 여 <xref:System.Collections.Generic.Dictionary%602> 내용을 `map`에 복사 합니다. 이 과정에서 `make_pair` 함수를 사용 하 여 새 쌍을 만들고 새 쌍을 `map`에 직접 삽입 합니다.

```cpp
// cliext_convert_dictionary_to_map.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/algorithm>
#include <cliext/map>

using namespace System;
using namespace System::Collections;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    System::Collections::Generic::Dictionary<float, int> ^dict =
        gcnew System::Collections::Generic::Dictionary<float, int>();
    dict->Add(42.0, 42);
    dict->Add(13.0, 13);
    dict->Add(74.0, 74);
    dict->Add(22.0, 22);
    dict->Add(0.0, 0);

    cliext::collection_adapter<System::Collections::Generic::IDictionary<float, int>> dictAdapter(dict);
    cliext::map<float, int> aMap;
    for each (KeyValuePair<float, int> ^kvp in dictAdapter)
    {
        cliext::pair<float, int> aPair = cliext::make_pair(kvp->Key, kvp->Value);
        aMap.insert(aPair);
    }

    Console::WriteLine("The contents of the cliext::map are:");
    cliext::map<float, int>::const_iterator it;
    for (it = aMap.begin(); it != aMap.end(); it++)
    {
        Console::WriteLine("Key: {0:F} Value: {1}", it->first, it->second);
    }
}
```

```Output
The contents of the cliext::map are:
Key: 0.00 Value: 0
Key: 13.00 Value: 13
Key: 22.00 Value: 22
Key: 42.00 Value: 42
Key: 74.00 Value: 74
```

## <a name="see-also"></a>참고 항목

[STL/CLR 라이브러리 참조](../dotnet/stl-clr-library-reference.md)<br/>
[adapter(STL/CLR)](../dotnet/adapter-stl-clr.md)<br/>
[방법: STL/CLR 컨테이너에서 .NET 컬렉션으로 변환](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)

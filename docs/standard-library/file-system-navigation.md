---
title: 파일 시스템 탐색
description: C++ 표준 라이브러리 파일 시스템 API를 사용하여 파일 시스템을 탐색하는 방법
ms.date: 04/13/2020
ms.assetid: f7cc5f5e-a541-4e00-87c7-a3769ef6096d
ms.openlocfilehash: 412d865582a14da7b8c31d9f07a43106b0c49491
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368436"
---
# <a name="file-system-navigation"></a>파일 시스템 탐색

\<filesystem> 헤더는 C++ 파일 시스템 기술 사양 ISO/IEC TS 18822:2015(최종 초안: [ISO/IEC JTC 1/SC 22/WG 21 N4100](https://wg21.link/n4100))을 구현하며 파일 시스템을 탐색하기 위한 플랫폼 독립적인 코드를 작성할 수 있게 해주는 형식과 함수를 포함합니다. 플랫폼 간이기 때문에 Windows 시스템과 관련이 없는 API가 포함되어 있습니다. 예를 들어 `is_fifo(const path&)` 항상 Windows에서 **false를** 반환합니다.

## <a name="overview"></a>개요

\<filesystem> API는 다음과 같은 작업에 사용합니다.

- 지정된 경로 아래의 파일과 디렉터리 반복

- 만든 시간, 크기, 확장명 및 루트 디렉터리를 포함하여 파일에 대한 정보 가져오기

- 경로 작성, 분해 및 비교

- 디렉터리 생성, 복사 및 삭제

- 파일 복사 및 삭제

표준 라이브러리를 사용한 파일 IO에 대한 자세한 내용은 [iostream 프로그래밍](../standard-library/iostream-programming.md)을 참조하세요.

## <a name="paths"></a>경로

### <a name="constructing-and-composing-paths"></a>경로 생성 및 작성

XP 이후 Windows의 경로는 기본적으로 유니코드로 저장됩니다. [경로](../standard-library/path-class.md) 클래스는 필요한 모든 문자열 변환을 자동으로 수행합니다. 넓고 좁은 문자 배열과 `std::string` UTF8 또는 UTF16으로 서식이 지정된 `std::wstring` 형식의 인수를 모두 허용합니다. 또한 `path` 클래스는 경로 구분 기호를 자동으로 정규화합니다. 생성자 인수에 단일 슬래시를 디렉터리 구분 기호로 사용할 수 있습니다. 이 구분 기호를 사용하면 동일한 문자열을 사용하여 Windows 및 UNIX 환경 모두에서 경로를 저장할 수 있습니다.

```cpp
path pathToDisplay(L"/FileSystemTest/SubDir3");     // OK!
path pathToDisplay2(L"\\FileSystemTest\\SubDir3");  // Still OK as always
path pathToDisplay3(LR"(\FileSystemTest\SubDir3)"); // Raw string literals are OK, too.
```

두 경로를 연결하기 위해 `/` 및 `/=` 의 `+` 및 `+=` 연산자와 유사한 오버로드된 `std::string` 및 `std::wstring`연산자를 사용할 수 있습니다. 그렇지 `path` 않으면 개체가 구분 기호를 편리하게 공급합니다.

```cpp
path myRoot("C:/FileSystemTest");  // no trailing separator, no problem!
myRoot /= path("SubDirRoot");      // C:/FileSystemTest/SubDirRoot
```

### <a name="examining-paths"></a>경로 검사

경로 클래스에는 경로 자체의 여러 부분에 대한 정보를 반환하는 여러 메서드가 있습니다. 이 정보는 참조할 수 있는 파일 시스템 엔터티에 대한 정보와 구별됩니다. 루트, 상대 경로, 파일 이름 및 파일 확장명 등을 가져올 수 있습니다. path 개체를 반복하여 계층 구조의 모든 폴더를 검사할 수 있습니다. 다음 예제에서는 경로 개체를 반복하는 방법을 보여 주며 있습니다. 그리고, 그 부분에 대한 정보를 검색하는 방법.

```cpp
// filesystem_path_example.cpp
// compile by using: /EHsc /W4 /permissive- /std:c++17 (or /std:c++latest)
#include <string>
#include <iostream>
#include <sstream>
#include <filesystem>

using namespace std;
using namespace std::filesystem;

wstring DisplayPathInfo()
{
    // This path may or may not refer to an existing file. We are
    // examining this path string, not file system objects.
    path pathToDisplay(L"C:/FileSystemTest/SubDir3/SubDirLevel2/File2.txt ");

    wostringstream wos;
    int i = 0;
    wos << L"Displaying path info for: " << pathToDisplay << endl;
    for (path::iterator itr = pathToDisplay.begin(); itr != pathToDisplay.end(); ++itr)
    {
        wos << L"path part: " << i++ << L" = " << *itr << endl;
    }

    wos << L"root_name() = " << pathToDisplay.root_name() << endl
        << L"root_path() = " << pathToDisplay.root_path() << endl
        << L"relative_path() = " << pathToDisplay.relative_path() << endl
        << L"parent_path() = " << pathToDisplay.parent_path() << endl
        << L"filename() = " << pathToDisplay.filename() << endl
        << L"stem() = " << pathToDisplay.stem() << endl
        << L"extension() = " << pathToDisplay.extension() << endl;

    return wos.str();
}

int main()
{
    wcout << DisplayPathInfo() << endl;
    // wcout << ComparePaths() << endl; // see following example
    wcout << endl << L"Press Enter to exit" << endl;
    wstring input;
    getline(wcin, input);
}
```

코드에서 다음 출력이 생성됩니다.

```Output
Displaying path info for: C:\FileSystemTest\SubDir3\SubDirLevel2\File2.txt
path part: 0 = C:
path part: 1 = \
path part: 2 = FileSystemTest
path part: 3 = SubDir3
path part: 4 = SubDirLevel2
path part: 5 = File2.txt
root_name() = C:
root_path() = C:\
relative_path() = FileSystemTest\SubDir3\SubDirLevel2\File2.txt
parent_path() = C:\FileSystemTest\SubDir3\SubDirLevel2
filename() = File2.txt
stem() = File2
extension() = .txt
```

### <a name="comparing-paths"></a>경로 비교

`path` 클래스는 `std::string` 및 `std::wstring`과 동일한 비교 연산자를 오버로드합니다. 두 경로를 비교할 때 구분 기호가 정규화된 후 문자열 비교를 합니다. 후행 슬래시(또는 백슬래시)가 없으면 추가되지 않으며 비교에 영향을 줍니다. 다음 예제에서는 경로 값이 비교되는 방식을 보여 줍니다.

```cpp
wstring ComparePaths()
{
    path p0(L"C:/Documents");                 // no trailing separator
    path p1(L"C:/Documents/");                // p0 < p1
    path p2(L"C:/Documents/2013/");           // p1 < p2
    path p3(L"C:/Documents/2013/Reports/");   // p2 < p3
    path p4(L"C:/Documents/2014/");           // p3 < p4
    path p5(L"D:/Documents/2013/Reports/");   // p4 < p5

    wostringstream wos;
    wos << boolalpha <<
        p0.wstring() << L" < " << p1.wstring() << L": " << (p0 < p1) << endl <<
        p1.wstring() << L" < " << p2.wstring() << L": " << (p1 < p2) << endl <<
        p2.wstring() << L" < " << p3.wstring() << L": " << (p2 < p3) << endl <<
        p3.wstring() << L" < " << p4.wstring() << L": " << (p3 < p4) << endl <<
        p4.wstring() << L" < " << p5.wstring() << L": " << (p4 < p5) << endl;
    return wos.str();
}
```

```Output
C:\Documents < C:\Documents\: true
C:\Documents\ < C:\Documents\2013\: true
C:\Documents\2013\ < C:\Documents\2013\Reports\: true
C:\Documents\2013\Reports\ < C:\Documents\2014\: true
C:\Documents\2014\ < D:\Documents\2013\Reports\: true
```

이 코드를 실행하려면 위의 전체 예제에서 `main` 앞에 붙여넣고 main에서 호출하는 줄의 주석 처리를 제거합니다.

### <a name="converting-between-path-and-string-types"></a>경로와 문자열 형식 간 변환

`path` 개체를 `std::wstring` 또는 `std::string`으로 암시적으로 변환할 수 있습니다. 즉, 이 예제와 같이 [wofstream::open](../standard-library/basic-ofstream-class.md#open)과 같은 함수에 경로를 전달할 수 있습니다.

```cpp
// filesystem_path_conversion.cpp
// compile by using: /EHsc /W4 /permissive- /std:c++17 (or /std:c++latest)
#include <string>
#include <iostream>
#include <fstream>
#include <filesystem>

using namespace std;
using namespace std::filesystem;

int main()
{
    const wchar_t* p{ L"C:/Users/Public/Documents" };
    path filePath(p);

    filePath /= L"NewFile.txt";

    // Open, write to, and close the file.
    wofstream writeFile(filePath, ios::out);  // implicit conversion
    writeFile << L"Lorem ipsum\nDolor sit amet";
    writeFile.close();

    // Open, read, and close the file.
    wifstream readFile;
    wstring line;
    readFile.open(filePath);  // implicit conversions
    wcout << L"File " << filePath << L" contains:" << endl;
    while (readFile.good())
    {
        getline(readFile, line);
        wcout << line << endl;
    }
    readFile.close();

    wcout << endl << L"Press Enter to exit" << endl;
    wstring input;
    getline(wcin, input);
}
```

```Output
File C:\Users\Public\Documents\NewFile.txt contains:
Lorem ipsum
Dolor sit amet

Press Enter to exit
```

## <a name="iterating-directories-and-files"></a>디렉터리 및 파일 반복

\<filesystem> 헤더는 단일 디렉터리를 반복하는 [directory_iterator](../standard-library/directory-iterator-class.md) 형식과 디렉터리 및 하위 디렉터리를 재귀적으로 반복하는 [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) 클래스를 제공합니다. `path` 개체를 전달하여 반복기를 생성하면 반복기가 경로의 첫 번째 directory_entry를 가리킵니다. 기본 생성자를 호출하여 끝 반복기를 만듭니다.

디렉터리를 반복할 때 여러 종류의 항목을 발견할 수 있습니다. 이러한 항목에는 디렉터리, 파일, 기호 링크, 소켓 파일 등이 포함됩니다. `directory_iterator`는 해당 항목을 [directory_entry](../standard-library/directory-entry-class.md) 개체로 반환합니다.

---
title: '&lt;fstream&gt; (Typedefs)'
ms.date: 11/04/2016
f1_keywords:
- fstream/std::filebuf
- fstream/std::fstream
- fstream/std::ifstream
- fstream/std::ofstream
- fstream/std::wfilebuf
- fstream/std::wfstream
- fstream/std::wifstream
- fstream/std::wofstream
ms.assetid: 8dddef2d-7f17-42a6-ba08-6f6f20597d23
ms.openlocfilehash: 57e481c131a6e4a1111b1ed88217b891d6fc96a8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317192"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt; (Typedefs)

||||
|-|-|-|
|[filebuf](#filebuf)|[Fstream](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a><a name="filebuf"></a>filebuf

Un `basic_filebuf` tipo especializado en parámetros de plantilla **char.**

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de plantilla de clase [basic_filebuf](../standard-library/basic-filebuf-class.md), especializada para elementos de tipo **char** con rasgos de carácter predeterminados.

## <a name="fstream"></a><a name="fstream"></a>Fstream

Un `basic_fstream` tipo especializado en parámetros de plantilla **char.**

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de plantilla de clase [basic_fstream](../standard-library/basic-fstream-class.md), especializada para elementos de tipo **char** con rasgos de carácter predeterminados.

## <a name="ifstream"></a><a name="ifstream"></a>ifstream

Define una secuencia que se utilizará para leer datos de caracteres de byte único en serie desde un archivo. `ifstream`es un typedef que especializa `basic_ifstream` la plantilla de clase para **char**.

También `wifstream`hay , una typedef `basic_ifstream` que se especializa para leer **wchar_t** caracteres de doble ancho. Para obtener más información, vea [wifstream](../standard-library/fstream-typedefs.md#wifstream).

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de plantilla de clase [basic_ifstream](../standard-library/basic-ifstream-class.md), especializada para elementos de tipo char con rasgos de carácter predeterminados. Un ejemplo es

```cpp
using namespace std;

ifstream infile("existingtextfile.txt");

if (!infile.bad())
{
    // Dump the contents of the file to cout.
    cout << infile.rdbuf();infile.close();
}
```

## <a name="ofstream"></a><a name="ofstream"></a>ofstream

Un `basic_ofstream` tipo especializado en parámetros de plantilla **char.**

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de plantilla de clase [basic_ofstream](../standard-library/basic-ofstream-class.md), especializada para elementos de tipo **char** con rasgos de carácter predeterminados.

## <a name="wfstream"></a><a name="wfstream"></a>wfstream

Un `basic_fstream` tipo especializado en **wchar_t** parámetros de plantilla.

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de plantilla de clase [basic_fstream](../standard-library/basic-fstream-class.md), especializada para elementos de tipo **wchar_t** con rasgos de carácter predeterminados.

## <a name="wifstream"></a><a name="wifstream"></a>wifstream

Un `basic_ifstream` tipo especializado en **wchar_t** parámetros de plantilla.

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de plantilla de clase [basic_ifstream](../standard-library/basic-ifstream-class.md), especializada para elementos de tipo **wchar_t** con rasgos de carácter predeterminados.

## <a name="wofstream"></a><a name="wofstream"></a>wofstream

Un `basic_ofstream` tipo especializado en **wchar_t** parámetros de plantilla.

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de plantilla de clase [basic_ofstream](../standard-library/basic-ofstream-class.md), especializada para elementos de tipo **wchar_t** con rasgos de carácter predeterminados.

## <a name="wfilebuf"></a><a name="wfilebuf"></a>wfilebuf

Un `basic_filebuf` tipo especializado en **wchar_t** parámetros de plantilla.

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de plantilla de clase [basic_filebuf](../standard-library/basic-filebuf-class.md), especializada para elementos de tipo **wchar_t** con rasgos de carácter predeterminados.

## <a name="see-also"></a>Consulte también

[\<>fstream](../standard-library/fstream.md)

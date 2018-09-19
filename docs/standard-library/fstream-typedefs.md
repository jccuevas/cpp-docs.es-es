---
title: '&lt;fstream&gt; (Typedefs) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: dcae38b92d4740758bad00bc6e07555654dfd973
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018059"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt; (Typedefs)

||||
|-|-|-|
|[filebuf](#filebuf)|[fstream](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a>  filebuf

Un tipo `basic_filebuf` especializado en **char** parámetros de plantilla.

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_filebuf](../standard-library/basic-filebuf-class.md), especializada en elementos del tipo **char** con rasgos de caracteres predeterminados.

## <a name="fstream"></a>  fstream

Un tipo `basic_fstream` especializado en **char** parámetros de plantilla.

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_fstream](../standard-library/basic-fstream-class.md), especializada en elementos del tipo **char** con rasgos de caracteres predeterminados.

## <a name="ifstream"></a>  ifstream

Define una secuencia que se utilizará para leer datos de caracteres de byte único en serie desde un archivo. `ifstream` es un typedef que especializa la clase de plantilla `basic_ifstream` para **char**.

También hay `wifstream`, un typedef que especializa `basic_ifstream` leer **wchar_t** caracteres de doble ancho. Para obtener más información, vea [wifstream](../standard-library/fstream-typedefs.md#wifstream).

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_ifstream](../standard-library/basic-ifstream-class.md), especializada en elementos de tipo char con rasgos de caracteres predeterminados. Un ejemplo es

```cpp
using namespace std;

ifstream infile("existingtextfile.txt");

if (!infile.bad())
{
    // Dump the contents of the file to cout.
    cout << infile.rdbuf();infile.close();
}
```

## <a name="ofstream"></a>  ofstream

Un tipo `basic_ofstream` especializado en **char** parámetros de plantilla.

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_ofstream](../standard-library/basic-ofstream-class.md), especializada en elementos del tipo **char** con rasgos de caracteres predeterminados.

## <a name="wfstream"></a>  wfstream

Un tipo `basic_fstream` especializado en **wchar_t** parámetros de plantilla.

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_fstream](../standard-library/basic-fstream-class.md), especializada en elementos del tipo **wchar_t** con rasgos de caracteres predeterminados.

## <a name="wifstream"></a>  wifstream

Un tipo `basic_ifstream` especializado en **wchar_t** parámetros de plantilla.

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_ifstream](../standard-library/basic-ifstream-class.md), especializada en elementos del tipo **wchar_t** con rasgos de caracteres predeterminados.

## <a name="wofstream"></a>  wofstream

Un tipo `basic_ofstream` especializado en **wchar_t** parámetros de plantilla.

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_ofstream](../standard-library/basic-ofstream-class.md), especializada en elementos del tipo **wchar_t** con rasgos de caracteres predeterminados.

## <a name="wfilebuf"></a>  wfilebuf

Un tipo `basic_filebuf` especializado en **wchar_t** parámetros de plantilla.

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_filebuf](../standard-library/basic-filebuf-class.md), especializada en elementos del tipo **wchar_t** con rasgos de caracteres predeterminados.

## <a name="see-also"></a>Vea también

[\<fstream>](../standard-library/fstream.md)<br/>

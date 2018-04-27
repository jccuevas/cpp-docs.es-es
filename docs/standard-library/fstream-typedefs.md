---
title: '&lt;fstream&gt; (Typedefs) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 11
manager: ghogen
ms.openlocfilehash: 3fb38bcee6d23968e51e86fbde0b824cb7316ed4
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt; (Typedefs)

||||
|-|-|-|
|[filebuf](#filebuf)|[fstream](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a>  filebuf

Un tipo `basic_filebuf` especializado en parámetros de plantilla `char`.

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>Comentarios

Tipo sinónimo de la clase de plantilla [basic_filebuf](../standard-library/basic-filebuf-class.md), especializada en elementos del tipo `char` con rasgos de caracteres predeterminados.

## <a name="fstream"></a>  fstream

Un tipo `basic_fstream` especializado en parámetros de plantilla `char`.

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>Comentarios

Tipo sinónimo de la clase de plantilla [basic_fstream](../standard-library/basic-fstream-class.md), especializada en elementos del tipo `char` con rasgos de caracteres predeterminados.

## <a name="ifstream"></a>  ifstream

Define una secuencia que se utilizará para leer datos de caracteres de byte único en serie desde un archivo. `ifstream`es un typedef que especializa la clase de plantilla `basic_ifstream` para `char`.

También está `wifstream`, un typedef que especializa `basic_ifstream` para leer caracteres de doble ancho `wchar_t`. Para obtener más información, vea [wifstream](../standard-library/fstream-typedefs.md#wifstream).

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_ifstream](../standard-library/basic-ifstream-class.md), especializada en elementos de tipo char con rasgos de caracteres predeterminados. Un ejemplo es

`using namespace std;`

`ifstream infile("existingtextfile.txt");`

`if (!infile.bad())`

`{`

`// Dump the contents of the file to cout.`

`cout << infile.rdbuf();`

`infile.close();`

`}`

## <a name="ofstream"></a>  ofstream

Un tipo `basic_ofstream` especializado en parámetros de plantilla `char`.

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>Comentarios

Tipo sinónimo de la clase de plantilla [basic_ofstream](../standard-library/basic-ofstream-class.md), especializada en elementos del tipo `char` con rasgos de caracteres predeterminados.

## <a name="wfstream"></a>  wfstream

Un tipo `basic_fstream` especializado en parámetros de plantilla `wchar_t`.

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>Comentarios

Tipo sinónimo de la clase de plantilla [basic_fstream](../standard-library/basic-fstream-class.md), especializada en elementos del tipo `wchar_t` con rasgos de caracteres predeterminados.

## <a name="wifstream"></a>  wifstream

Un tipo `basic_ifstream` especializado en parámetros de plantilla `wchar_t`.

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>Comentarios

Tipo sinónimo de la clase de plantilla [basic_ifstream](../standard-library/basic-ifstream-class.md), especializada en elementos del tipo `wchar_t` con rasgos de caracteres predeterminados.

## <a name="wofstream"></a>  wofstream

Un tipo `basic_ofstream` especializado en parámetros de plantilla `wchar_t`.

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>Comentarios

Tipo sinónimo de la clase de plantilla [basic_ofstream](../standard-library/basic-ofstream-class.md), especializada en elementos del tipo `wchar_t` con rasgos de caracteres predeterminados.

## <a name="wfilebuf"></a>  wfilebuf

Un tipo `basic_filebuf` especializado en parámetros de plantilla `wchar_t`.

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>Comentarios

Tipo sinónimo de la clase de plantilla [basic_filebuf](../standard-library/basic-filebuf-class.md), especializada en elementos del tipo `wchar_t` con rasgos de caracteres predeterminados.

## <a name="see-also"></a>Vea también

[\<fstream>](../standard-library/fstream.md)<br/>

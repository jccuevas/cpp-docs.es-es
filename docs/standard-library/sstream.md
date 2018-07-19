---
title: '&lt;sstream&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <sstream>
dev_langs:
- C++
helpviewer_keywords:
- sstream header
ms.assetid: 56f55bc5-549d-4e7f-aaad-99e0ffa49c9e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8801c41b23ab2c33e4c4e2df9cde8155c1eefafb
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957773"
---
# <a name="ltsstreamgt"></a>&lt;sstream&gt;

Define varias clases de plantilla que admiten operaciones de iostreams en secuencias almacenadas en un objeto de matriz asignado. Dichas secuencias fácilmente se convierten a y desde objetos de clase de plantilla [basic_string](../standard-library/basic-string-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
namespace std {
template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_stringbuf;
typedef basic_stringbuf<char>
stringbuf;
typedef basic_stringbuf<wchar_t> wstringbuf;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_istringstream;
typedef basic_istringstream<char>
istringstream;
typedef basic_istringstream<wchar_t> wistringstream;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_ostringstream;
typedef basic_ostringstream<char>
ostringstream;
typedef basic_ostringstream<wchar_t> wostringstream;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_stringstream;
typedef basic_stringstream<char>
stringstream;
typedef basic_stringstream<wchar_t> wstringstream;
// TEMPLATE FUNCTIONS
template <class CharType, class Traits, class Allocator>
void swap(
    basic_stringbuf<CharType, Traits, Allocator>& left,
    basic_stringbuf<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap(
    basic_istringstream<CharType, Traits, Allocator>& left,
    basic_istringstream<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap(
    basic_ostringstream<CharType, Traits, Allocator>& left,
    basic_ostringstream<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap (
    basic_stringstream<CharType, Traits, Allocator>& left,
    basic_stringstream<CharType, Traits, Allocator>& right);

}  // namespace std
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*left*|Referencia a un objeto `sstream`.|
|*right*|Referencia a un objeto `sstream`.|

## <a name="remarks"></a>Comentarios

Los objetos de tipo `char *` pueden usar la funcionalidad de [\<strstream>](../standard-library/strstream.md) para streaming. Sin embargo, \<strstream > está en desuso y el uso de \<sstream > se anima.

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[istringstream](../standard-library/sstream-typedefs.md#istringstream)|Crea un tipo `basic_istringstream` especializado en un **char** parámetro de plantilla.|
|[ostringstream](../standard-library/sstream-typedefs.md#ostringstream)|Crea un tipo `basic_ostringstream` especializado en un **char** parámetro de plantilla.|
|[stringbuf](../standard-library/sstream-typedefs.md#stringbuf)|Crea un tipo `basic_stringbuf` especializado en un **char** parámetro de plantilla.|
|[stringstream](../standard-library/sstream-typedefs.md#stringstream)|Crea un tipo `basic_stringstream` especializado en un **char** parámetro de plantilla.|
|[wistringstream](../standard-library/sstream-typedefs.md#wistringstream)|Crea un tipo `basic_istringstream` especializado en un **wchar_t** parámetro de plantilla.|
|[wostringstream](../standard-library/sstream-typedefs.md#wostringstream)|Crea un tipo `basic_ostringstream` especializado en un **wchar_t** parámetro de plantilla.|
|[wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf)|Crea un tipo `basic_stringbuf` especializado en un **wchar_t** parámetro de plantilla.|
|[wstringstream](../standard-library/sstream-typedefs.md#wstringstream)|Crea un tipo `basic_stringstream` especializado en un **wchar_t** parámetro de plantilla.|

### <a name="manipulators"></a>Manipuladores

|||
|-|-|
|[swap](../standard-library/sstream-functions.md#sstream_swap)|Intercambia los valores entre dos objetos `sstream`.|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[basic_stringbuf](../standard-library/basic-stringbuf-class.md)|Describe un búfer de secuencia que controla la transmisión bidireccional entre elementos de tipo `Elem` —cuyos rasgos de caracteres están determinados por la clase `Tr`— y una secuencia de elementos almacenados en un objeto Array.|
|[basic_istringstream](../standard-library/basic-istringstream-class.md)|Describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de secuencia de clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md)<**Elem**, **Tr**, `Alloc`>, con elementos de tipo `Elem`, cuyos rasgos de caracteres están determinados por la clase `Tr`, y cuyos elementos están asignados mediante un asignador de clase `Alloc`.|
|[basic_ostringstream](../standard-library/basic-ostringstream-class.md)|Describe un objeto que controla la inserción de elementos y objetos codificados en un búfer de secuencia de clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md)<**Elem**, **Tr**, `Alloc`>, con elementos de tipo `Elem`, cuyos rasgos de caracteres están determinados por la clase `Tr`, y cuyos elementos están asignados mediante un asignador de clase `Alloc`.|
|[basic_stringstream](../standard-library/basic-stringstream-class.md)|Describe un objeto que controla la inserción y extracción de elementos y objetos codificados usando un búfer de secuencia de clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md)<**Elem**, **Tr**, `Alloc`>, con elementos de tipo `Elem`, cuyos rasgos de caracteres están determinados por la clase `Tr`, y cuyos elementos están asignados mediante un asignador de clase `Alloc`.|

## <a name="requirements"></a>Requisitos

- **Encabezado:** \<sstream>

- **Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Programación con iostream](../standard-library/iostream-programming.md)<br/>
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)<br/>

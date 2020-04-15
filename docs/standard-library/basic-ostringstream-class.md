---
title: basic_ostringstream (Clase)
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_ostringstream
- sstream/std::basic_ostringstream::allocator_type
- sstream/std::basic_ostringstream::rdbuf
- sstream/std::basic_ostringstream::str
helpviewer_keywords:
- std::basic_ostringstream [C++]
- std::basic_ostringstream [C++], allocator_type
- std::basic_ostringstream [C++], rdbuf
- std::basic_ostringstream [C++], str
ms.assetid: aea699f7-350f-432a-acca-adbae7b483fb
ms.openlocfilehash: 9e10474d3e4fb2a37e8ab52f77495758c37e8a5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376775"
---
# <a name="basic_ostringstream-class"></a>basic_ostringstream (Clase)

Describe un objeto que controla la inserción de elementos y `Alloc` objetos codificados en un búfer de secuencia de clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_ostringstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>Parámetros

*Alloc*\
Clase de asignador.

*Elem*\
Tipo de elemento básico de la cadena.

*Tr*\
Rasgos de caracteres especializados en el elemento básico de la cadena.

## <a name="remarks"></a>Observaciones

La clase describe un objeto que controla la inserción de `Elem`elementos y objetos codificados en un búfer de secuencia, con elementos de tipo , cuyos rasgos de carácter están determinados por la clase `Tr`y cuyos elementos se asignan mediante un asignador de clase `Alloc`. El objeto almacena un objeto de clase basic_stringbuf< **Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[basic_ostringstream](#basic_ostringstream)|Construye un objeto de tipo `basic_ostringstream`.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[allocator_type](#allocator_type)|El tipo es un sinónimo del parámetro de plantilla *Alloc*.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[rdbuf](#rdbuf)|Devuelve la dirección del búfer `pointer` de secuencia `Alloc` almacenado de tipo a [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`,>.|
|[Str](#str)|Establece u obtiene el texto en un búfer de cadena sin cambiar la posición de escritura.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<sstream>

**Espacio de nombres:** std

## <a name="basic_ostringstreamallocator_type"></a><a name="allocator_type"></a>basic_ostringstream::allocator_type

El tipo es un sinónimo del parámetro de plantilla *Alloc*.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_ostringstreambasic_ostringstream"></a><a name="basic_ostringstream"></a>basic_ostringstream::basic_ostringstream

Construye un objeto de tipo basic_ostringstream.

```cpp
explicit basic_ostringstream(ios_base::openmode _Mode = ios_base::out);

explicit basic_ostringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Parámetros

*_Mode*\
Una de las enumeraciones de [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*Str*\
Objeto de tipo `basic_string`.

### <a name="remarks"></a>Observaciones

El primer constructor inicializa la clase base llamando `sb` a [basic_ostream](../standard-library/basic-ostream-class.md)( **sb**), donde `Alloc` está el objeto almacenado de la clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,> . También inicializa **sb** al llamar a basic_stringbuf< **Elem**, **Tr**, `Alloc`>(`_Mode` &#124; `ios_base::out`).

El segundo constructor inicializa la clase base al llamar a basic_ostream(**sb**). También se `sb` inicializa llamando a basic_stringbuf< `Alloc` **Elem**, `_Mode` **Tr**,>(_ *Str*, &#124; `ios_base::out`).

## <a name="basic_ostringstreamrdbuf"></a><a name="rdbuf"></a>basic_ostringstream::rdbuf

Devuelve la dirección del búfer `pointer` de secuencia almacenado de `Alloc` tipo a [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Valor devuelto

La dirección del búfer de `pointer` secuencia almacenado, de tipo `Alloc` para basic_stringbuf< **Elem**, **Tr**,>.

### <a name="remarks"></a>Observaciones

La función miembro devuelve la dirección `pointer` del búfer de secuencia `Alloc` almacenado de tipo para basic_stringbuf< **Elem**, **Tr**,> .

### <a name="example"></a>Ejemplo

Vea [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) para obtener un ejemplo que usa `rdbuf`.

## <a name="basic_ostringstreamstr"></a><a name="str"></a>basic_ostringstream::str

Establece u obtiene el texto en un búfer de cadena sin cambiar la posición de escritura.

```cpp
basic_string<Elem, Tr, Alloc> str() const;

void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parámetros

*_Newstr*\
La nueva cadena.

### <a name="return-value"></a>Valor devuelto

Devuelve un objeto [basic_string](../standard-library/basic-string-class.md)< de clase basic_string `Alloc` **Elem**, **Tr**,>, cuya secuencia controlada es una copia de la secuencia controlada por ** \*este**.

### <a name="remarks"></a>Observaciones

La primera función miembro devuelve [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str). La segunda función miembro llama `rdbuf`  -> a **str**( `_Newstr`).

### <a name="example"></a>Ejemplo

Consulte [basic_stringbuf::str](../standard-library/basic-stringbuf-class.md#str) para obtener `str`un ejemplo que utiliza .

## <a name="see-also"></a>Consulte también

[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programación iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)

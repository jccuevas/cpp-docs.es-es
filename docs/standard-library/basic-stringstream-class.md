---
title: basic_stringstream (Clase)
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_stringstream
- sstream/std::basic_stringstream::allocator_type
- sstream/std::basic_stringstream::rdbuf
- sstream/std::basic_stringstream::str
helpviewer_keywords:
- std::basic_stringstream [C++]
- std::basic_stringstream [C++], allocator_type
- std::basic_stringstream [C++], rdbuf
- std::basic_stringstream [C++], str
ms.assetid: 49629814-ca37-45c5-931b-4ff894e6ebd2
ms.openlocfilehash: f08689b1080837f042abfb3c4c52bb0ad558a448
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364870"
---
# <a name="basic_stringstream-class"></a>basic_stringstream (Clase)

Describe un objeto que controla la inserción y extracción de elementos `Alloc` y objetos codificados mediante un búfer de secuencia de clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_stringstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Parámetros

*Alloc*\
Clase de asignador.

*Elem*\
Tipo de elemento básico de la cadena.

*Tr*\
Rasgos de caracteres especializados en el elemento básico de la cadena.

## <a name="remarks"></a>Observaciones

La plantilla de clase describe un objeto que controla la inserción y extracción de elementos `Elem`y objetos codificados mediante `Tr`un búfer de secuencia de clase `Alloc` [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>, con elementos de tipo , cuyos rasgos de carácter están determinados por la clase y cuyos elementos se asignan mediante un asignador de clase . El objeto almacena un objeto de clase basic_stringbuf< **Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[basic_stringstream](#basic_stringstream)|Construye un objeto de tipo `basic_stringstream`.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[allocator_type](#allocator_type)|El tipo es un sinónimo del parámetro de plantilla `Alloc`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[rdbuf](#rdbuf)|Devuelve la dirección del búfer `pointer` de secuencia `Alloc` almacenado de tipo a [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`,>.|
|[Str](#str)|Establece u obtiene el texto en un búfer de cadena sin cambiar la posición de escritura.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<sstream>

**Espacio de nombres:** std

## <a name="basic_stringstreamallocator_type"></a><a name="allocator_type"></a>basic_stringstream::allocator_type

El tipo es un sinónimo del parámetro de plantilla `Alloc`.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringstreambasic_stringstream"></a><a name="basic_stringstream"></a>basic_stringstream::basic_stringstream

Construye un objeto de tipo `basic_stringstream`.

```cpp
explicit basic_stringstream(ios_base::openmode _Mode = ios_base::in | ios_base::out);

explicit basic_stringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parámetros

*_Mode*\
Una de las enumeraciones de [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*Str*\
Objeto de tipo `basic_string`.

### <a name="remarks"></a>Observaciones

El primer constructor inicializa la clase base llamando `sb` a [basic_iostream](../standard-library/basic-iostream-class.md)( **sb**), donde `Alloc` está el objeto almacenado de la clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,> . También se `sb` inicializa llamando a basic_stringbuf< `Alloc` **Elem**, **Tr**,>( `_Mode`).

El segundo constructor inicializa la clase base al llamar a basic_iostream( **sb**). También se `sb` inicializa llamando a basic_stringbuf< `Alloc` **Elem**, `_Mode` **Tr**,>(_ *Str*, ).

## <a name="basic_stringstreamrdbuf"></a><a name="rdbuf"></a>basic_stringstream::rdbuf

Devuelve la dirección del búfer de flujo almacenado de tipo **pointer** a [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Valor devuelto

La dirección del búfer de `pointer` secuencia almacenado de tipo `Alloc` para basic_stringbuf< **Elem**, **Tr**,>.

### <a name="example"></a>Ejemplo

Vea [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) para obtener un ejemplo que usa `rdbuf`.

## <a name="basic_stringstreamstr"></a><a name="str"></a>basic_stringstream::str

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

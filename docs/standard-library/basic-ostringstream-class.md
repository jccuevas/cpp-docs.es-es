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
ms.openlocfilehash: 45a7eb1384c70b488e057fb9df8ad4c496272316
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62414144"
---
# <a name="basicostringstream-class"></a>basic_ostringstream (Clase)

Describe un objeto que controla la inserción de objetos codificados y elementos en un búfer de flujo de clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_ostringstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>Parámetros

*Alloc*<br/>
Clase de asignador.

*Elem*<br/>
Tipo de elemento básico de la cadena.

*Tr*<br/>
Rasgos de caracteres especializados en el elemento básico de la cadena.

## <a name="remarks"></a>Comentarios

La clase describe un objeto que controla la inserción de elementos y objetos codificados en un búfer de secuencia, con elementos de tipo `Elem`, cuyos rasgos de caracteres están determinados por la clase `Tr`, y cuyos elementos están asignados mediante un asignador de clase `Alloc`. El objeto almacena un objeto de clase basic_stringbuf< **Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[basic_ostringstream](#basic_ostringstream)|Construye un objeto de tipo `basic_ostringstream`.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[allocator_type](#allocator_type)|El tipo es un sinónimo del parámetro de plantilla *Alloc*.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[rdbuf](#rdbuf)|Devuelve la dirección del búfer de flujo almacenado de tipo `pointer` a [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>.|
|[str](#str)|Establece u obtiene el texto en un búfer de cadena sin cambiar la posición de escritura.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<sstream>

**Espacio de nombres:** std

## <a name="allocator_type"></a>  basic_ostringstream::allocator_type

El tipo es un sinónimo del parámetro de plantilla *Alloc*.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_ostringstream"></a>  basic_ostringstream::basic_ostringstream

Construye un objeto de tipo basic_ostringstream.

```cpp
explicit basic_ostringstream(ios_base::openmode _Mode = ios_base::out);

explicit basic_ostringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Parámetros

*_Mode*<br/>
Una de las enumeraciones de [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*str*<br/>
Objeto de tipo `basic_string`.

### <a name="remarks"></a>Comentarios

El primer constructor inicializa la clase base mediante una llamada a [basic_ostream](../standard-library/basic-ostream-class.md)( **sb**), donde `sb` es el objeto almacenado de clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **Elem**, **Tr**, `Alloc`>. También inicializa **sb** al llamar a basic_stringbuf< **Elem**, **Tr**, `Alloc`>(`_Mode` &#124; `ios_base::out`).

El segundo constructor inicializa la clase base al llamar a basic_ostream(**sb**). También inicializa `sb` al llamar a basic_stringbuf < **Elem**, **Tr**, `Alloc`> (_ *Str*, `_Mode` &#124; `ios_base::out`).

## <a name="rdbuf"></a>  basic_ostringstream::rdbuf

Devuelve la dirección del búfer de flujo almacenado de tipo `pointer` a [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Valor devuelto

La dirección del búfer de secuencia almacenado, de tipo `pointer` a basic_stringbuf < **Elem**, **Tr**, `Alloc`>.

### <a name="remarks"></a>Comentarios

La función miembro devuelve la dirección del búfer de flujo almacenado de tipo `pointer` a basic_stringbuf < **Elem**, **Tr**, `Alloc`>.

### <a name="example"></a>Ejemplo

Vea [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) para obtener un ejemplo de uso de `rdbuf`.

## <a name="str"></a>  basic_ostringstream::str

Establece u obtiene el texto en un búfer de cadena sin cambiar la posición de escritura.

```cpp
basic_string<Elem, Tr, Alloc> str() const;

void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parámetros

*_Newstr*<br/>
La nueva cadena.

### <a name="return-value"></a>Valor devuelto

Devuelve un objeto de clase [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`>, cuya secuencia controlada es una copia de la secuencia controlada por **\*this**.

### <a name="remarks"></a>Comentarios

La primera función miembro devuelve [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str). La segunda función miembro llama a `rdbuf` -> **str**(`_Newstr`).

### <a name="example"></a>Ejemplo

Consulte [basic_stringbuf:: str](../standard-library/basic-stringbuf-class.md#str) para obtener un ejemplo que usa `str`.

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Programación con iostream](../standard-library/iostream-programming.md)<br/>
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)<br/>

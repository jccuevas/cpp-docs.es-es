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
ms.openlocfilehash: ebf9b87b60cf790a2ca032eb805095f277324178
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688409"
---
# <a name="basic_stringstream-class"></a>basic_stringstream (Clase)

Describe un objeto que controla la inserción y la extracción de elementos y objetos codificados usando un búfer de flujo de clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_stringstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Parámetros

@No__t_1 de *asignación*
Clase de asignador.

@No__t_1 *Elem*
Tipo de elemento básico de la cadena.

*Tr* \
Rasgos de caracteres especializados en el elemento básico de la cadena.

## <a name="remarks"></a>Comentarios

La plantilla de clase describe un objeto que controla la inserción y extracción de elementos y objetos codificados mediante un búfer de secuencia de la clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **Elem**, **TR**`Alloc` >, con elementos de tipo `Elem`, cuyo los rasgos de caracteres están determinados por la clase `Tr` y cuyos elementos están asignados por un asignador de clase `Alloc`. El objeto almacena un objeto de clase basic_stringbuf< **Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[basic_stringstream](#basic_stringstream)|Construye un objeto de tipo `basic_stringstream`.|

### <a name="typedefs"></a>Definiciones de tipo

|Nombre de tipo|Descripción|
|-|-|
|[allocator_type](#allocator_type)|El tipo es un sinónimo del parámetro de plantilla `Alloc`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[rdbuf](#rdbuf)|Devuelve la dirección del búfer de flujo almacenado de tipo `pointer` a [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>.|
|[str](#str)|Establece u obtiene el texto en un búfer de cadena sin cambiar la posición de escritura.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<sstream>

**Espacio de nombres:** std

## <a name="allocator_type"></a>  basic_stringstream::allocator_type

El tipo es un sinónimo del parámetro de plantilla `Alloc`.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringstream"></a>  basic_stringstream::basic_stringstream

Construye un objeto de tipo `basic_stringstream`.

```cpp
explicit basic_stringstream(ios_base::openmode _Mode = ios_base::in | ios_base::out);

explicit basic_stringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parámetros

@No__t_1 *_Mode*
Una de las enumeraciones de [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

\ *Str*
Objeto de tipo `basic_string`.

### <a name="remarks"></a>Comentarios

El primer constructor inicializa la clase base mediante una llamada a [basic_iostream](../standard-library/basic-iostream-class.md)( **SB**), donde `sb` es el objeto almacenado de la clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **Elem**, **TR**`Alloc` >. También inicializa `sb` llamando a basic_stringbuf < **Elem**, **TR**`Alloc` > (`_Mode`).

El segundo constructor inicializa la clase base al llamar a basic_iostream( **sb**). También inicializa `sb` llamando a basic_stringbuf < **Elem**, **TR**`Alloc` > (_ *Str*, `_Mode`).

## <a name="rdbuf"></a>  basic_stringstream::rdbuf

Devuelve la dirección del búfer de flujo almacenado de tipo **pointer** a [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Valor devuelto

La dirección del búfer de secuencia almacenado de tipo `pointer` a basic_stringbuf < **Elem**, **TR**`Alloc` >.

### <a name="example"></a>Ejemplo

Vea [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) para obtener un ejemplo que usa `rdbuf`.

## <a name="str"></a>  basic_stringstream::str

Establece u obtiene el texto en un búfer de cadena sin cambiar la posición de escritura.

```cpp
basic_string<Elem, Tr, Alloc> str() const;

void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parámetros

@No__t_1 *_Newstr*
La nueva cadena.

### <a name="return-value"></a>Valor devuelto

Devuelve un objeto de clase [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`>, cuya secuencia controlada es una copia de la secuencia controlada por **\*this**.

### <a name="remarks"></a>Comentarios

La primera función miembro devuelve [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str). La segunda función miembro llama a `rdbuf` -> **str**(`_Newstr`).

### <a name="example"></a>Ejemplo

Vea [basic_stringbuf:: STR](../standard-library/basic-stringbuf-class.md#str) para obtener un ejemplo en el que se usa `str`.

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programación con iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)

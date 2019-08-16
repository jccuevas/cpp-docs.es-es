---
title: basic_istringstream (Clase)
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_istringstream
- sstream/std::basic_istringstream::allocator_type
- sstream/std::basic_istringstream::rdbuf
- sstream/std::basic_istringstream::str
- sstream/std::basic_istringstream::swap
helpviewer_keywords:
- std::basic_istringstream [C++]
- std::basic_istringstream [C++], allocator_type
- std::basic_istringstream [C++], rdbuf
- std::basic_istringstream [C++], str
- std::basic_istringstream [C++], swap
ms.assetid: 1d5bb4b5-793d-4833-98e5-14676c451915
ms.openlocfilehash: 685195b13960c325076f1a38461394ada374d4b1
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452533"
---
# <a name="basicistringstream-class"></a>basic_istringstream (Clase)

Describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de flujo de clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_istringstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Parámetros

*Alloc*\
Clase de asignador.

*Elem*\
Tipo de elemento básico de la cadena.

*Anticipo*\
Rasgos de caracteres especializados en el elemento básico de la cadena.

## <a name="remarks"></a>Comentarios

La clase de plantilla describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de secuencia de clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, `Alloc` **TR**, >, con elementos de tipo *Elem*. cuyos rasgos de caracteres están determinados por la clase *TR*y cuyos elementos están asignados por un asignador de clase *Alloc*. El objeto almacena un objeto de clase basic_stringbuf< **Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Constructores

|Constructor|DESCRIPCIÓN|
|-|-|
|[basic_istringstream](#basic_istringstream)|Construye un objeto de tipo `basic_istringstream`.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|DESCRIPCIÓN|
|-|-|
|[allocator_type](#allocator_type)|El tipo es un sinónimo del parámetro de plantilla `Alloc`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|DESCRIPCIÓN|
|-|-|
|[rdbuf](#rdbuf)|Devuelve la dirección del búfer de flujo almacenado de tipo `pointer` a [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>.|
|[str](#str)|Establece u obtiene el texto en un búfer de cadena sin cambiar la posición de escritura.|
|[swap](#swap)|Intercambia los valores de este objeto `basic_istringstream` con los del objeto proporcionado.|

### <a name="operators"></a>Operadores

|Operador|DESCRIPCIÓN|
|-|-|
|[operator=](#op_eq)|Asigna los valores a este objeto `basic_istringstream` desde el parámetro de objeto.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<sstream>

**Espacio de nombres:** std

## <a name="allocator_type"></a>  basic_istringstream::allocator_type

El tipo es un sinónimo del parámetro de plantilla `Alloc`.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_istringstream"></a>  basic_istringstream::basic_istringstream

Construye un objeto de tipo `basic_istringstream`.

```cpp
explicit basic_istringstream(
    ios_base::openmode _Mode = ios_base::in);

explicit basic_istringstream(
    const basic_string<Elem, Tr, Alloc>& str,
    ios_base::openmode _Mode = ios_base::in);

basic_istringstream(
    basic_istringstream&& right);
```

### <a name="parameters"></a>Parámetros

*_Mode*\
Una de las enumeraciones de [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*CAD*\
Objeto de tipo `basic_string`.

*correcta*\
Referencia a un valor R de un objeto `basic_istringstream`.

### <a name="remarks"></a>Comentarios

El primer constructor inicializa la clase base mediante una llamada [](../standard-library/basic-istream-class.md)a basic_istream`sb`(), `sb` donde es el objeto almacenado de [](../standard-library/basic-stringbuf-class.md)< la clase `Tr`basic_stringbuf `Alloc``Elem`,, > . También inicializa `sb` al llamar a `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>(`_Mode` &#124; `ios_base::in`).

El segundo constructor inicializa la clase base al llamar a `basic_istream(sb)`. También inicializa `sb` al llamar a `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>(`str`, `_Mode` &#124; `ios_base::in`).

El tercer constructor inicializa el objeto con el contenido de la *derecha*, tratado como una referencia rvalue.

## <a name="op_eq"></a>  basic_istringstream::operator=

Asigna los valores a este objeto `basic_istringstream` desde el parámetro de objeto.

```cpp
basic_istringstream& operator=(basic_istringstream&& right);
```

### <a name="parameters"></a>Parámetros

*correcta*\
Referencia a un valor R a un objeto `basic_istringstream`.

### <a name="remarks"></a>Comentarios

El operador miembro reemplaza el contenido del objeto por el contenido de la *derecha*, tratado como una asignación de movimiento de referencia de valor r.

## <a name="rdbuf"></a>  basic_istringstream::rdbuf

Devuelve la dirección del búfer de secuencia almacenado de tipo `pointer` a [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **TR** `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Valor devuelto

La dirección del búfer de secuencia almacenado de tipo `pointer` a basic_stringbuf < **Elem**, **TR** `Alloc`>.

### <a name="example"></a>Ejemplo

Vea [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) para obtener un ejemplo de uso de `rdbuf`.

## <a name="str"></a>  basic_istringstream::str

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

Devuelve un objeto de clase [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`>, cuya secuencia controlada es una copia de la secuencia controlada por **\*this**.

### <a name="remarks"></a>Comentarios

La primera función miembro devuelve [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str). La segunda función miembro llama a `rdbuf` -> **str**(`_Newstr`).

### <a name="example"></a>Ejemplo

Vea [basic_stringbuf:: STR](../standard-library/basic-stringbuf-class.md#str) para obtener un ejemplo que `str`usa.

## <a name="swap"></a>  basic_istringstream::swap

Intercambia los valores de dos objetos `basic_istringstream`.

```cpp
void swap(basic_istringstream& right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*right*|Referencia `lvalue` a un objeto `basic_istringstream`.|

### <a name="remarks"></a>Comentarios

La función miembro intercambia los valores de este objeto y los valores de *right*.

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programación con iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)

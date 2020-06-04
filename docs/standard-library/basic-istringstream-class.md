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
ms.openlocfilehash: 6a8ead5f1014e7f750e01988241ab020431312da
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376803"
---
# <a name="basic_istringstream-class"></a>basic_istringstream (Clase)

Describe un objeto que controla la extracción de elementos y objetos codificados desde un búfer de secuencia de clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

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

*Tr*\
Rasgos de caracteres especializados en el elemento básico de la cadena.

## <a name="remarks"></a>Observaciones

La plantilla de clase describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de secuencia de clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>, con elementos de tipo *Elem*, cuyos rasgos de carácter están determinados por la clase *Tr*y cuyos elementos se asignan mediante un asignador de clase *Alloc*. El objeto almacena un objeto de clase basic_stringbuf< **Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[basic_istringstream](#basic_istringstream)|Construye un objeto de tipo `basic_istringstream`.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[allocator_type](#allocator_type)|El tipo es un sinónimo del parámetro de plantilla `Alloc`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[rdbuf](#rdbuf)|Devuelve la dirección del búfer `pointer` de secuencia `Alloc` almacenado de tipo a [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`,>.|
|[Str](#str)|Establece u obtiene el texto en un búfer de cadena sin cambiar la posición de escritura.|
|[swap](#swap)|Intercambia los valores de este objeto `basic_istringstream` con los del objeto proporcionado.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[operador](#op_eq)|Asigna los valores a este objeto `basic_istringstream` desde el parámetro de objeto.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<sstream>

**Espacio de nombres:** std

## <a name="basic_istringstreamallocator_type"></a><a name="allocator_type"></a>basic_istringstream::allocator_type

El tipo es un sinónimo del parámetro de plantilla `Alloc`.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_istringstreambasic_istringstream"></a><a name="basic_istringstream"></a>basic_istringstream::basic_istringstream

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

*Str*\
Objeto de tipo `basic_string`.

*Correcto*\
Referencia a un valor R de un objeto `basic_istringstream`.

### <a name="remarks"></a>Observaciones

El primer constructor inicializa la clase`sb`base `sb` llamando a [basic_istream](../standard-library/basic-istream-class.md)( ), `Alloc` donde está el objeto almacenado de la clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`,>. También inicializa `sb` al llamar a `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>(`_Mode` &#124; `ios_base::in`).

El segundo constructor inicializa la clase base al llamar a `basic_istream(sb)`. También inicializa `sb` al llamar a `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>(`str`, `_Mode` &#124; `ios_base::in`).

El tercer constructor inicializa el objeto con el contenido de *right*, tratado como una referencia rvalue.

## <a name="basic_istringstreamoperator"></a><a name="op_eq"></a>basic_istringstream::operador ?

Asigna los valores a este objeto `basic_istringstream` desde el parámetro de objeto.

```cpp
basic_istringstream& operator=(basic_istringstream&& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Referencia a un valor R a un objeto `basic_istringstream`.

### <a name="remarks"></a>Observaciones

El operador miembro reemplaza el contenido del objeto con el contenido de *right*, tratado como una asignación de movimiento de referencia rvalue.

## <a name="basic_istringstreamrdbuf"></a><a name="rdbuf"></a>basic_istringstream::rdbuf

Devuelve la dirección del búfer `pointer` de secuencia almacenado de `Alloc` tipo a [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Valor devuelto

La dirección del búfer de `pointer` secuencia almacenado de tipo `Alloc` para basic_stringbuf< **Elem**, **Tr**,>.

### <a name="example"></a>Ejemplo

Vea [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) para obtener un ejemplo que usa `rdbuf`.

## <a name="basic_istringstreamstr"></a><a name="str"></a>basic_istringstream::str

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

## <a name="basic_istringstreamswap"></a><a name="swap"></a>basic_istringstream::swap

Intercambia los valores de dos objetos `basic_istringstream`.

```cpp
void swap(basic_istringstream& right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Correcto*|Referencia `lvalue` a un objeto `basic_istringstream`.|

### <a name="remarks"></a>Observaciones

La función miembro intercambia los valores de este objeto y los valores de *right*.

## <a name="see-also"></a>Consulte también

[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programación iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)

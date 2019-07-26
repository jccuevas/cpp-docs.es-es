---
title: strstream (Clase)
ms.date: 11/04/2016
f1_keywords:
- strstream/std::strstream::freeze
- strstream/std::strstream::pcount
- strstream/std::strstream::rdbuf
- strstream/std::strstream::str
helpviewer_keywords:
- std::strstream [C++], freeze
- std::strstream [C++], pcount
- std::strstream [C++], rdbuf
- std::strstream [C++], str
ms.assetid: 63f3be31-9e36-42b1-9715-a474a5997e2a
ms.openlocfilehash: 53baa350121796d5198211e1fdb08f4341df6b80
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459100"
---
# <a name="strstream-class"></a>strstream (Clase)

Describe un objeto que controla la inserción y la extracción de objetos codificados y elementos usando un búfer de secuencia de la clase [strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
class strstream : public iostream
```

## <a name="remarks"></a>Comentarios

El objeto almacena un objeto de clase `strstreambuf`.

> [!NOTE]
> Esta clase está en desuso. Considere el uso de [stringstream](../standard-library/sstream-typedefs.md#stringstream) o [wstringstream](../standard-library/sstream-typedefs.md#wstringstream) en su lugar.

### <a name="constructors"></a>Constructores

|Constructor|DESCRIPCIÓN|
|-|-|
|[strstream](#strstream)|Construye un objeto de tipo `strstream`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|DESCRIPCIÓN|
|-|-|
|[freeze](#freeze)|Hace que un búfer de secuencia no esté disponible a través de las operaciones de búfer de secuencia.|
|[pcount](#pcount)|Devuelve un recuento del número de elementos que se escriben en la secuencia controlada.|
|[rdbuf](#rdbuf)|Devuelve un puntero al objeto `strstreambuf` asociado de la secuencia.|
|[str](#str)|Llama a [freeze](../standard-library/strstreambuf-class.md#freeze) y, después, devuelve un puntero al principio de la secuencia controlada.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<strstream>

**Espacio de nombres:** std

## <a name="freeze"></a>  strstream::freeze

Hace que un búfer de secuencia no esté disponible a través de las operaciones de búfer de secuencia.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parámetros

*_Freezeit*\
Un valor **booleano** que indica si desea que se inmovilizar la secuencia.

### <a name="remarks"></a>Comentarios

La función miembro llama a [rdbuf](#rdbuf) -> [freeze](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit*).

### <a name="example"></a>Ejemplo

Vea [strstreambuf:: Freeze](../standard-library/strstreambuf-class.md#freeze) para obtener un ejemplo que `freeze`usa.

## <a name="pcount"></a>  strstream::pcount

Devuelve un recuento del número de elementos que se escriben en la secuencia controlada.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos que se escriben en la secuencia controlada.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Ejemplo

Vea [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) para obtener un ejemplo del uso de pcount.

## <a name="rdbuf"></a>  strstream::rdbuf

Devuelve un puntero al objeto strstreambuf asociado de la secuencia.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Valor devuelto

Un puntero al objeto strstreambuf asociado del flujo.

### <a name="remarks"></a>Comentarios

La función miembro devuelve la dirección del búfer de secuencia almacenado de tipo `pointer` a [strstreambuf](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Ejemplo

Vea [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) para obtener un ejemplo que usa `rdbuf`.

## <a name="str"></a>  strstream::str

Llama a [freeze](../standard-library/strstreambuf-class.md#freeze) y, después, devuelve un puntero al principio de la secuencia controlada.

```cpp
char *str();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al principio de la secuencia controlada.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Ejemplo

Vea [strstreambuf:: STR](../standard-library/strstreambuf-class.md#str) para obtener un ejemplo que `str`usa.

## <a name="strstream"></a>  strstream::strstream

Construye un objeto de tipo `strstream`.

```cpp
strstream();

strstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parámetros

*contabiliza*\
Tamaño del búfer.

*_Mode*\
El modo de entrada y salida del búfer. Vea [ios_base::openmode](../standard-library/ios-base-class.md#openmode) para obtener más información.

*anota*\
El búfer.

### <a name="remarks"></a>Comentarios

Ambos constructores inicializan la clase base mediante una llamada a [streambuf](../standard-library/streambuf-typedefs.md#streambuf)( **SB**), donde `sb` es el objeto almacenado de la clase [strstreambuf](../standard-library/strstreambuf-class.md). El primer constructor también se inicializa `sb` llamando a [strstreambuf](../standard-library/strstreambuf-class.md#strstreambuf). El segundo constructor inicializa la clase base de una de estas dos maneras:

- Si `_Mode` `strstreambuf` `ptr` `count` `count` `ptr`  ios_base:: app = = 0, PTR debe designar el primer elemento de una matriz de elementos y el constructor llama a (,,).  &  .

- De lo contrario, *ptr* debe designar el primer elemento de una matriz de elementos Count que contiene una cadena de C cuyo primer elemento está designado por *ptr*y el `strstreambuf`constructor `ptr`llama a `ptr` (, `count`,  +  `strlen`( `ptr`) ).

## <a name="see-also"></a>Vea también

[iostream](../standard-library/istream-typedefs.md#iostream)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programación con iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)

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
ms.openlocfilehash: 047b7e9d7fdece75137980b013d43abf1d5e3ec3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376617"
---
# <a name="strstream-class"></a>strstream (Clase)

Describe un objeto que controla la inserción y la extracción de objetos codificados y elementos usando un búfer de secuencia de la clase [strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
class strstream : public iostream
```

## <a name="remarks"></a>Observaciones

El objeto almacena un objeto de clase `strstreambuf`.

> [!NOTE]
> Esta clase está en desuso. Considere el uso de [stringstream](../standard-library/sstream-typedefs.md#stringstream) o [wstringstream](../standard-library/sstream-typedefs.md#wstringstream) en su lugar.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[strstream](#strstream)|Construye un objeto de tipo `strstream`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[Congelar](#freeze)|Hace que un búfer de secuencia no esté disponible a través de las operaciones de búfer de secuencia.|
|[pcount](#pcount)|Devuelve un recuento del número de elementos que se escriben en la secuencia controlada.|
|[rdbuf](#rdbuf)|Devuelve un puntero al objeto `strstreambuf` asociado de la secuencia.|
|[Str](#str)|Llama a [freeze](../standard-library/strstreambuf-class.md#freeze) y, después, devuelve un puntero al principio de la secuencia controlada.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<strstream>

**Espacio de nombres:** std

## <a name="strstreamfreeze"></a><a name="freeze"></a>strstream::freeze

Hace que un búfer de secuencia no esté disponible a través de las operaciones de búfer de secuencia.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parámetros

*_Freezeit*\
Un **bool** que indica si desea que la secuencia se congele.

### <a name="remarks"></a>Observaciones

La función miembro llama [a rdbuf](#rdbuf) -> [freeze](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit*).

### <a name="example"></a>Ejemplo

Consulte [strstreambuf::freeze](../standard-library/strstreambuf-class.md#freeze) para obtener `freeze`un ejemplo que utiliza .

## <a name="strstreampcount"></a><a name="pcount"></a>strstream::pcount

Devuelve un recuento del número de elementos que se escriben en la secuencia controlada.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos que se escriben en la secuencia controlada.

### <a name="remarks"></a>Observaciones

La función miembro devuelve [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Ejemplo

Vea [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) para obtener un ejemplo del uso de pcount.

## <a name="strstreamrdbuf"></a><a name="rdbuf"></a>strstream::rdbuf

Devuelve un puntero al objeto strstreambuf asociado del flujo.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Valor devuelto

Un puntero al objeto strstreambuf asociado del flujo.

### <a name="remarks"></a>Observaciones

La función miembro devuelve la dirección `pointer` del búfer de secuencia almacenado de tipo a [strstreambuf](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Ejemplo

Vea [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) para obtener un ejemplo que usa `rdbuf`.

## <a name="strstreamstr"></a><a name="str"></a>strstream::str

Llama a [freeze](../standard-library/strstreambuf-class.md#freeze) y, después, devuelve un puntero al principio de la secuencia controlada.

```cpp
char *str();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al principio de la secuencia controlada.

### <a name="remarks"></a>Observaciones

La función miembro devuelve [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Ejemplo

Consulte [strstreambuf::str](../standard-library/strstreambuf-class.md#str) para obtener `str`un ejemplo que utilice .

## <a name="strstreamstrstream"></a><a name="strstream"></a>strstream::strstream

Construye un objeto de tipo `strstream`.

```cpp
strstream();

strstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parámetros

*Contar*\
Tamaño del búfer.

*_Mode*\
El modo de entrada y salida del búfer. Vea [ios_base::openmode](../standard-library/ios-base-class.md#openmode) para obtener más información.

*Ptr*\
El búfer.

### <a name="remarks"></a>Observaciones

Ambos constructores inicializan la clase base llamando `sb` a [streambuf](../standard-library/streambuf-typedefs.md#streambuf)( **sb**), donde está el objeto almacenado de la clase [strstreambuf](../standard-library/strstreambuf-class.md). El primer constructor `sb` también se inicializa llamando a [strstreambuf](../standard-library/strstreambuf-class.md#strstreambuf). El segundo constructor inicializa la clase base de una de estas dos maneras:

- Si `_Mode`  &  **ios_base::app**, a continuación, *ptr* debe designar `count` el primer elemento `strstreambuf`de `ptr` `count`una `ptr`matriz de elementos y el constructor llama ( , , ).

- De lo contrario, *ptr* debe designar el primer elemento de una matriz de elementos count que contiene `ptr`una cadena C cuyo primer elemento está designado por *ptr*y el constructor llama `strstreambuf`a ( `ptr`, `count`, `ptr`  +  `strlen`( ) ).

## <a name="see-also"></a>Consulte también

[Iostream](../standard-library/istream-typedefs.md#iostream)\
[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programación iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)

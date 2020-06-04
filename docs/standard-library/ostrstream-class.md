---
title: ostrstream (Clase)
ms.date: 11/04/2016
f1_keywords:
- strstream/std::ostrstream::freeze
- strstream/std::ostrstream::pcount
- strstream/std::ostrstream::rdbuf
- strstream/std::ostrstream::str
helpviewer_keywords:
- std::ostrstream [C++], freeze
- std::ostrstream [C++], pcount
- std::ostrstream [C++], rdbuf
- std::ostrstream [C++], str
ms.assetid: e2e34679-b266-4728-a8e1-8eda5d400e46
ms.openlocfilehash: b52ba70607a5214a6aa28f04cdded0b19a56b2f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373543"
---
# <a name="ostrstream-class"></a>ostrstream (Clase)

Describe un objeto que controla la inserción de objetos codificados y elementos en un búfer de secuencia de clase [strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
class ostrstream : public ostream
```

## <a name="remarks"></a>Observaciones

El objeto almacena un objeto de clase `strstreambuf`.

> [!NOTE]
> Esta clase está en desuso. Considere el uso de [ostringstream](../standard-library/sstream-typedefs.md#ostringstream) o [wostringstream](../standard-library/sstream-typedefs.md#wostringstream) en su lugar.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[ostrstream](#ostrstream)|Construye un objeto de tipo `ostrstream`.|

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

## <a name="ostrstreamfreeze"></a><a name="freeze"></a>ostrstream::freeze

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

Consulte [strstream::freeze](../standard-library/strstreambuf-class.md#freeze) para obtener `freeze`un ejemplo que utiliza .

## <a name="ostrstreamostrstream"></a><a name="ostrstream"></a>ostrstream::ostrstream

Construye un objeto de tipo `ostrstream`.

```cpp
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Parámetros

*Ptr*\
El búfer.

*Contar*\
Tamaño del búfer en bytes.

*_Mode*\
El modo de entrada y salida del búfer. Vea [ios_base::openmode](../standard-library/ios-base-class.md#openmode) para obtener más información.

### <a name="remarks"></a>Observaciones

Ambos constructores inicializan la clase base llamando `sb` a [ostream](../standard-library/ostream-typedefs.md#ostream)(**sb**), donde está el objeto almacenado de la clase [strstreambuf](../standard-library/strstreambuf-class.md). El primer constructor `sb` también `strstreambuf`se inicializa llamando a . El segundo constructor inicializa la clase base de una de estas dos maneras:

- Si `_Mode`  &  **ios_base::app**á 0, `ptr` debe designar el primer `count` elemento de una `strstreambuf``ptr`matriz de elementos y el constructor llama a ( , `count`, `ptr`).

- De `ptr` lo contrario, debe designar el primer elemento de una matriz de `ptr`elementos count `strstreambuf``ptr`que `count` `ptr`  +  `strlen`contiene `ptr`una cadena C cuyo primer elemento está designado por , y el constructor llama a ( , , ( ) ).

## <a name="ostrstreampcount"></a><a name="pcount"></a>ostrstream::pcount

Devuelve un recuento del número de elementos que se escriben en la secuencia controlada.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos que se escriben en la secuencia controlada.

### <a name="remarks"></a>Observaciones

La función miembro devuelve [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Ejemplo

Vea [strstream::pcount](../standard-library/strstreambuf-class.md#pcount) para obtener un ejemplo que usa `pcount`.

## <a name="ostrstreamrdbuf"></a><a name="rdbuf"></a>ostrstream::rdbuf

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

## <a name="ostrstreamstr"></a><a name="str"></a>ostrstream::str

Llama a [freeze](../standard-library/strstreambuf-class.md#freeze) y, después, devuelve un puntero al principio de la secuencia controlada.

```cpp
char *str();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al principio de la secuencia controlada.

### <a name="remarks"></a>Observaciones

La función miembro devuelve [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Ejemplo

Consulte [strstream::str](../standard-library/strstreambuf-class.md#str) para obtener `str`un ejemplo que utiliza .

## <a name="see-also"></a>Consulte también

[ostream](../standard-library/ostream-typedefs.md#ostream)\
[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programación iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)

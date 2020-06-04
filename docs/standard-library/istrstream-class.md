---
title: istrstream (Clase)
ms.date: 11/04/2016
f1_keywords:
- strstream/std::istrstream::rdbuf
- strstream/std::istrstream::str
helpviewer_keywords:
- istrstream class
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
ms.openlocfilehash: d548a8c2c47a5a345be725afdedb47524344f720
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337521"
---
# <a name="istrstream-class"></a>istrstream (Clase)

Describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de flujo de clase [strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
class istrstream : public istream
```

## <a name="remarks"></a>Observaciones

El objeto almacena un objeto de clase `strstreambuf`.

> [!NOTE]
> Esta clase está en desuso. Considere el uso de [istringstream](../standard-library/sstream-typedefs.md#istringstream) o [wistringstream](../standard-library/sstream-typedefs.md#wistringstream) en su lugar.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[istrstream](#istrstream)|Construye un objeto de tipo `istrstream`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[rdbuf](#rdbuf)|Devuelve un puntero al objeto `strstreambuf` asociado de la secuencia.|
|[Str](#str)|Llama a [freeze](../standard-library/strstreambuf-class.md#freeze) y, después, devuelve un puntero al principio de la secuencia controlada.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<strstream>

**Espacio de nombres:** std

## <a name="istrstreamistrstream"></a><a name="istrstream"></a>istrstream::istrstream

Construye un objeto de tipo `istrstream`.

```cpp
explicit istrstream(
    const char* ptr);

explicit istrstream(
    char* ptr);

istrstream(
    const char* ptr,
    streamsize count);

istrstream(
    char* ptr,
    int count);
```

### <a name="parameters"></a>Parámetros

*Contar*\
La longitud del búfer (*ptr*).

*Ptr*\
Contenido con el que se inicializa el búfer.

### <a name="remarks"></a>Observaciones

Todos los constructores inicializan la clase base llamando `sb` a [istream](../standard-library/istream-typedefs.md#istream)(**sb**), donde está el objeto almacenado de la clase [strstreambuf](../standard-library/strstreambuf-class.md). Los `sb` dos primeros constructores `strstreambuf`también se inicializan `ptr`llamando a ( ( **const** `char` \*), 0 ). Los dos constructores restantes, en su lugar, llaman a `strstreambuf`( ( **const** `char` *) `ptr`, `count` ).

## <a name="istrstreamrdbuf"></a><a name="rdbuf"></a>istrstream::rdbuf

Devuelve un puntero al objeto strstreambuf asociado del flujo.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Valor devuelto

Un puntero al objeto strstreambuf asociado del flujo.

### <a name="remarks"></a>Observaciones

La función miembro devuelve la dirección del búfer de flujo almacenado de tipo pointer a [strstreambuf](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Ejemplo

Vea [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) para obtener un ejemplo que usa `rdbuf`.

## <a name="istrstreamstr"></a><a name="str"></a>istrstream::str

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

[Istream](../standard-library/istream-typedefs.md#istream)\
[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programación iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)

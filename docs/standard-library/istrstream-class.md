---
title: istrstream (Clase)
ms.date: 11/04/2016
f1_keywords:
- strstream/std::istrstream::rdbuf
- strstream/std::istrstream::str
helpviewer_keywords:
- istrstream class
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
ms.openlocfilehash: 59b69d3f862715840e1557a10d6087350488a3c9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448072"
---
# <a name="istrstream-class"></a>istrstream (Clase)

Describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de flujo de clase [strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
class istrstream : public istream
```

## <a name="remarks"></a>Comentarios

El objeto almacena un objeto de clase `strstreambuf`.

> [!NOTE]
> Esta clase está en desuso. Considere el uso de [istringstream](../standard-library/sstream-typedefs.md#istringstream) o [wistringstream](../standard-library/sstream-typedefs.md#wistringstream) en su lugar.

### <a name="constructors"></a>Constructores

|Constructor|DESCRIPCIÓN|
|-|-|
|[istrstream](#istrstream)|Construye un objeto de tipo `istrstream`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|DESCRIPCIÓN|
|-|-|
|[rdbuf](#rdbuf)|Devuelve un puntero al objeto `strstreambuf` asociado de la secuencia.|
|[str](#str)|Llama a [freeze](../standard-library/strstreambuf-class.md#freeze) y, después, devuelve un puntero al principio de la secuencia controlada.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<strstream>

**Espacio de nombres:** std

## <a name="istrstream"></a>  istrstream::istrstream

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

*contabiliza*\
Longitud del búfer (*ptr*).

*anota*\
Contenido con el que se inicializa el búfer.

### <a name="remarks"></a>Comentarios

Todos los constructores inicializan la clase base mediante una llamada a [IStream](../standard-library/istream-typedefs.md#istream)(**SB**), donde `sb` es el objeto almacenado de la clase [strstreambuf](../standard-library/strstreambuf-class.md). Los dos primeros constructores también se `sb` inicializan `strstreambuf`llamando a (( `ptr` **const** `char` \*), 0). Los dos constructores restantes llaman a `strstreambuf`( ( **const**`char` *) `ptr`, `count` ).

## <a name="rdbuf"></a>  istrstream::rdbuf

Devuelve un puntero al objeto strstreambuf asociado del flujo.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Valor devuelto

Un puntero al objeto strstreambuf asociado del flujo.

### <a name="remarks"></a>Comentarios

La función miembro devuelve la dirección del búfer de flujo almacenado de tipo pointer a [strstreambuf](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Ejemplo

Vea [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) para obtener un ejemplo del uso de `rdbuf`.

## <a name="str"></a>  istrstream::str

Llama a [freeze](../standard-library/strstreambuf-class.md#freeze) y, después, devuelve un puntero al principio de la secuencia controlada.

```cpp
char *str();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al principio de la secuencia controlada.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Ejemplo

Vea [strstream:: STR](../standard-library/strstreambuf-class.md#str) para obtener un ejemplo que `str`usa.

## <a name="see-also"></a>Vea también

[istream](../standard-library/istream-typedefs.md#istream)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programación con iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)

---
title: '&lt;strstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <strstream>
helpviewer_keywords:
- strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
ms.openlocfilehash: ecf8499a07f03c00588e7b7fd83b8d41a23e8e7a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459084"
---
# <a name="ltstrstreamgt"></a>&lt;strstream&gt;

Define varias clases que admiten operaciones de iostreams en secuencias almacenadas en una matriz asignada de un objeto **Char** . Estas secuencias se convierten fácilmente a y desde cadenas de C.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<strstream>

**Espacio de nombres:** std

## <a name="remarks"></a>Comentarios

Los objetos de tipo `strstream` funcionan con `char` *, que son cadenas de C. Use [\<sstream>](../standard-library/sstream.md) para trabajar con objetos de tipo [basic_string](../standard-library/basic-string-class.md).

> [!NOTE]
> Las clases de \<> strstream están desusadas. Considere la posibilidad de usar \<las clases de sstream > en su lugar.

## <a name="members"></a>Miembros

### <a name="classes"></a>Clases

|||
|-|-|
|[strstreambuf (Clase)](../standard-library/strstreambuf-class.md)|La clase describe un búfer de secuencia que controla la transmisión de elementos a y desde una secuencia de elementos almacenados en un objeto de matriz de **caracteres** .|
|[istrstream (Clase)](../standard-library/istrstream-class.md)|La clase describe un objeto que controla la extracción de objetos codificados y elementos de un búfer de secuencia de la clase [strstreambuf](../standard-library/strstreambuf-class.md).|
|[ostrstream (Clase)](../standard-library/ostrstream-class.md)|La clase describe un objeto que controla la inserción de objetos codificados y elementos en un búfer de secuencia de la clase [strstreambuf](../standard-library/strstreambuf-class.md).|
|[strstream (Clase)](../standard-library/strstream-class.md)|La clase describe un objeto que controla la inserción y la extracción de objetos codificados y elementos mediante un búfer de secuencia de la clase [strstreambuf](../standard-library/strstreambuf-class.md).|

### <a name="functions"></a>Funciones

```cpp
void freeze(bool freezefl = true);
char* str();
int pcount();
```

## <a name="see-also"></a>Vea también

[\<strstream>](../standard-library/strstream.md)\
[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programación con iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)

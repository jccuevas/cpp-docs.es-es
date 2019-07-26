---
title: '&lt;ostream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ostream>
- ostream/std::<ostream>
- std::<ostream>
helpviewer_keywords:
- ostream header
ms.assetid: 90c3b6fb-57cd-4ae7-99b8-8512f24a67d2
ms.openlocfilehash: 8de66718dab10b5c95e8c1ab7fd0bd17e9b4ee5e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448173"
---
# <a name="ltostreamgt"></a>&lt;ostream&gt;

Define la clase de plantilla [basic_ostream](../standard-library/basic-ostream-class.md), que remite inserciones para iostreams. El encabezado define también varios manipuladores relacionados. (Este encabezado suele incluirlo automáticamente otro encabezado de iostreams. Rara vez tendrá que incluirlo directamente).

## <a name="syntax"></a>Sintaxis

```cpp
#include <ostream>
```

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|DESCRIPCIÓN|
|-|-|
|[ostream](../standard-library/ostream-typedefs.md#ostream)|Crea un tipo a `basic_ostream` partir de que está especializado en `char_traits` **Char** y está especializado en **Char**.|
|[wostream](../standard-library/ostream-typedefs.md#wostream)|Crea un tipo a `basic_ostream` partir de que se especializa en `char_traits` **wchar_t** y se especializa en **wchar_t**.|

### <a name="manipulators"></a>Manipuladores

|||
|-|-|
|[endl](../standard-library/ostream-functions.md#endl)|Termina una línea y vacía el búfer.|
|[ends](../standard-library/ostream-functions.md#ends)|Termina una cadena|
|[flush](../standard-library/ostream-functions.md#flush)|Vacía el búfer.|
|[swap](../standard-library/ostream-functions.md#swap)|Intercambia los valores del parámetro de objeto `basic_ostream` de la izquierda con los del parámetro del objeto `basic_ostream` de la derecha.|

### <a name="operators"></a>Operadores

|Operador|DESCRIPCIÓN|
|-|-|
|[operator<<](../standard-library/ostream-operators.md#op_lt_lt)|Escribe varios tipos en la secuencia.|

### <a name="classes"></a>Clases

|Clase|DESCRIPCIÓN|
|-|-|
|[basic_ostream](../standard-library/basic-ostream-class.md)|La clase de plantilla describe un objeto que controla la inserción de objetos codificados y elementos en un búfer de secuencia.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programación con iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)

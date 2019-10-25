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
ms.openlocfilehash: 3838e215ffac42ec6902ab6a9837f638153cf184
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689165"
---
# <a name="ltostreamgt"></a>&lt;ostream&gt;

Define la plantilla de clase [basic_ostream](../standard-library/basic-ostream-class.md), que media las inserciones de iostreams. El encabezado define también varios manipuladores relacionados. (Este encabezado suele incluirlo automáticamente otro encabezado de iostreams. Rara vez tendrá que incluirlo directamente).

## <a name="syntax"></a>Sintaxis

```cpp
#include <ostream>
```

### <a name="typedefs"></a>Definiciones de tipo

|Nombre de tipo|Descripción|
|-|-|
|[ostream](../standard-library/ostream-typedefs.md#ostream)|Crea un tipo a partir de `basic_ostream` especializado en **Char** y `char_traits` Specialized en **Char**.|
|[wostream](../standard-library/ostream-typedefs.md#wostream)|Crea un tipo a partir de `basic_ostream` especializado en **wchar_t** y `char_traits` especializados en **wchar_t**.|

### <a name="manipulators"></a>Manipuladores

|||
|-|-|
|[endl](../standard-library/ostream-functions.md#endl)|Termina una línea y vacía el búfer.|
|[ends](../standard-library/ostream-functions.md#ends)|Termina una cadena|
|[flush](../standard-library/ostream-functions.md#flush)|Vacía el búfer.|
|[swap](../standard-library/ostream-functions.md#swap)|Intercambia los valores del parámetro de objeto `basic_ostream` de la izquierda con los del parámetro del objeto `basic_ostream` de la derecha.|

### <a name="operators"></a>Operadores

|"??"|Descripción|
|-|-|
|[operator<<](../standard-library/ostream-operators.md#op_lt_lt)|Escribe varios tipos en la secuencia.|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[basic_ostream](../standard-library/basic-ostream-class.md)|La plantilla de clase describe un objeto que controla la inserción de elementos y objetos codificados en un búfer de secuencia.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programación con iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)

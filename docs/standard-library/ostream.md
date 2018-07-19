---
title: '&lt;ostream&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <ostream>
- ostream/std::<ostream>
- std::<ostream>
dev_langs:
- C++
helpviewer_keywords:
- ostream header
ms.assetid: 90c3b6fb-57cd-4ae7-99b8-8512f24a67d2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf7b8bf3015879643728358258cfe4a67536b3ea
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863792"
---
# <a name="ltostreamgt"></a>&lt;ostream&gt;

Define la clase de plantilla [basic_ostream](../standard-library/basic-ostream-class.md), que remite inserciones para iostreams. El encabezado define también varios manipuladores relacionados. (Este encabezado suele incluirlo automáticamente otro encabezado de iostreams. Rara vez tendrá que incluirlo directamente).

## <a name="syntax"></a>Sintaxis

```cpp
#include <ostream>

```

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[ostream](../standard-library/ostream-typedefs.md#ostream)|Crea un tipo de `basic_ostream` que está especializado en `char` y `char_traits` especializado en `char`.|
|[wostream](../standard-library/ostream-typedefs.md#wostream)|Crea un tipo de `basic_ostream` que está especializado en `wchar_t` y `char_traits` especializado en `wchar_t`.|

### <a name="manipulators"></a>Manipuladores

|||
|-|-|
|[endl](../standard-library/ostream-functions.md#endl)|Termina una línea y vacía el búfer.|
|[ends](../standard-library/ostream-functions.md#ends)|Termina una cadena|
|[flush](../standard-library/ostream-functions.md#flush)|Vacía el búfer.|
|[swap](../standard-library/ostream-functions.md#swap)|Intercambia los valores del parámetro de objeto `basic_ostream` de la izquierda con los del parámetro del objeto `basic_ostream` de la derecha.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator<<](../standard-library/ostream-operators.md#op_lt_lt)|Escribe varios tipos en la secuencia.|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[basic_ostream](../standard-library/basic-ostream-class.md)|La clase de plantilla describe un objeto que controla la inserción de objetos codificados y elementos en un búfer de secuencia.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Programación con iostream](../standard-library/iostream-programming.md)<br/>
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)<br/>

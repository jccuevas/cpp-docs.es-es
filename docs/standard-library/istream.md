---
title: '&lt;istream&gt;'
ms.date: 11/04/2016
f1_keywords:
- istream/std::<istream>
- <istream>
- std::<istream>
helpviewer_keywords:
- istream header
ms.assetid: efcf24e4-05d1-4719-ab0b-9e7ebe845d89
ms.openlocfilehash: 0ad27bf849e8d4b9188868b9a29bf423b4cafafa
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458742"
---
# <a name="ltistreamgt"></a>&lt;istream&gt;

Define el basic_istream de clase de plantilla que remita extracciones para las iostreams, y el basic_iostream de clase de plantilla que remita las inserciones y extracciones. El encabezado define también un manipulador relacionado. Este archivo de encabezado se suele incluir automáticamente mediante otro encabezado de iostreams; rara vez tendrá que incluirlo directamente.

## <a name="syntax"></a>Sintaxis

```cpp
#include <istream>
```

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|DESCRIPCIÓN|
|-|-|
|[iostream](../standard-library/istream-typedefs.md#iostream)|Tipo `basic_iostream` especializado en **Char**.|
|[istream](../standard-library/istream-typedefs.md#istream)|Tipo `basic_istream` especializado en **Char**.|
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|Tipo `basic_iostream` especializado en **wchar**.|
|[wistream](../standard-library/istream-typedefs.md#wistream)|Tipo `basic_istream` especializado en **wchar**.|

### <a name="manipulators"></a>Manipuladores

|||
|-|-|
|[ws](../standard-library/istream-functions.md#ws)|Omite los espacios en blanco en el flujo.|
|[swap](../standard-library/istream-functions.md#istream_swap)|Intercambia dos objetos de flujo.|

### <a name="operators"></a>Operadores

|Operador|DESCRIPCIÓN|
|-|-|
|[operator>>](../standard-library/istream-operators.md#op_gt_gt)|Extrae caracteres y cadenas del flujo.|

### <a name="classes"></a>Clases

|Clase|DESCRIPCIÓN|
|-|-|
|[basic_iostream](../standard-library/basic-iostream-class.md)|Clase de secuencia que puede realizar tanto operaciones de entrada como de salida.|
|[basic_istream](../standard-library/basic-istream-class.md)|La clase de plantilla describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de flujo con elementos `Elem`de tipo, también conocidos como [char_type](../standard-library/basic-ios-class.md#char_type), cuyos rasgos de caracteres están determinados por `Tr`la clase, también se conoce como [traits_type](../standard-library/basic-ios-class.md#traits_type).|

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programación con iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)

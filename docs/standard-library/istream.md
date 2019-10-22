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
ms.openlocfilehash: 8e9675a673462c8eaab94d29a3ae36a4786737b7
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687849"
---
# <a name="ltistreamgt"></a>&lt;istream&gt;

Define la plantilla de clase basic_istream, que media las extracciones para iostreams y la plantilla de clase basic_iostream, que media las inserciones y extracciones. El encabezado define también un manipulador relacionado. Este archivo de encabezado se suele incluir automáticamente mediante otro encabezado de iostreams; rara vez tendrá que incluirlo directamente.

## <a name="syntax"></a>Sintaxis

```cpp
#include <istream>
```

### <a name="typedefs"></a>Definiciones de tipo

|Nombre de tipo|Descripción|
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

|"??"|Descripción|
|-|-|
|[operator>>](../standard-library/istream-operators.md#op_gt_gt)|Extrae caracteres y cadenas del flujo.|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[basic_iostream](../standard-library/basic-iostream-class.md)|Clase de secuencia que puede realizar tanto operaciones de entrada como de salida.|
|[basic_istream](../standard-library/basic-istream-class.md)|La plantilla de clase describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de flujo con elementos de tipo `Elem`, también conocido como [char_type](../standard-library/basic-ios-class.md#char_type), cuyos rasgos de caracteres están determinados por la clase `Tr`, también conocida como [ traits_type](../standard-library/basic-ios-class.md#traits_type).|

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programación con iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)
